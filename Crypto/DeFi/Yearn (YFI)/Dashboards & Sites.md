# Helpful Yearn sites and dashboards
#research #defi #analytics #tools 

found some really great websites for yearn, tracking pools, analytics, etc, want to eventually model our own dashboards to monitor similar stats for investments

## Old Versions
https://v1.yearn.finance/dashboard (has links to old stuff you can track)
https://v2.yearn.finance/vaults
Previous V3/Beta: https://beta.yearn.finance/

## Stats and TVL
### Yearn vision 
is an overview of all pools/tvl/daily changes/etc
https://yearn.vision/?orgId=1&refresh=1m&from=now-90d&to=now

This Exporter/Vision acts as the realtime data dashboard for all yearn vaults. Best thing for monitoring transactions and metrics, as well as keeping up with Harvests for certain pools
https://github.com/yearn/yearn-exporter

Take for example this yvUsdc pool that has 36 mil in assets, paying out 2.5% in apy. Interesting point here is that the pool has only $236k in free funds before it would have to pull funds from the strategies used for yvUsdc yield.
https://yearn.vision/d/apkUMx6nz/vault-overview?orgId=1&var-networks=ETH&var-exp=false&var-vaults=yvUSDC%200.4.3&var-address=0xa354F35829Ae975e850e23e9615b11Da1B3dC4DE&var-version=v2

### YFI stats
is a clean database for prev years of balance sheets and vaults that are launched on yearn. first pic displays their revue for multiple vaults that initially launched in july 2020, safe to say their starting balance of 3k after the initial yvUSD pool is more than impressive. 
![[Pasted image 20220608110850.png]]

second pic displays overall rev and other income, primarily the yfi mint from feb 2021 that yielded them 215m! pretty insane to consider that their token was the focus of so much hype and led to the further expansion of the yfi eco
![[Pasted image 20220608110856.png]]

third pic displays vaults v1 again but with a focus on the number of pools that were launched post-mint, spec as the token was launched the team became more experimental and added new pools, which then saw their tvl increase massively. 
![[Pasted image 20220608110910.png]]
in the same set of months, v2 vaults were launched and saw another boost in tvl, spec in the same stablecoin -> risk asset -> liq pool, process that they had similarly used for v1 vaults
https://www.yfistats.com/

## Dune dashboards
### Yearn Analysis of all vaults 
Dune analytics: this is a really eye opening dashboard for monitoring daily active users, vault volumes and deposit info, and top contributors to certain vaults. 4th pic displays this info with helpful diagrams of how diverse yearn became with vaults overtime
https://dune.com/jhackworth/ert

![[Pasted image 20220608110930.png]]

### Correlation metrics
![[Pasted image 20220608111019.png]]
This dashboard (5th/6th pics) displays all vault correlations and metrics for yvWeth and Usdc pools. same interest as before as well as visualizations to how diverse yearn vaults became just in 2022
https://dune.com/shini/Y

![[Pasted image 20220608110939.png]]

## Yearn Vaults: 
breakdown on crv boost multipliers (7th pic)
https://vaults.yearn.finance/curve-boost-multipliers
![[Pasted image 20220608111008.png]]

all defi tokens
https://vaults.yearn.finance/ethereum/defi-tokens

curve pools - stETH and 3crv main focuses
https://vaults.yearn.finance/ethereum/curve-pools 

### FTM Curve
Curve pools on ftm, most popular being 3pool
https://vaults.yearn.finance/fantom/curve-pools
![[Pasted image 20220608111443.png]]
Contract address
https://ftmscan.com/address/0xA9a904B5567b5AFfb6bB334bea2f90F700EB221a#code
#### Source code for Tricrypto Strategy
https://ftmscan.com/address/0xA9a904B5567b5AFfb6bB334bea2f90F700EB221a#code#F1#L1

// SPDX-License-Identifier: AGPL-3.0
pragma solidity 0.6.12;
pragma experimental ABIEncoderV2;

// These are the core Yearn libraries
import "IERC20.sol";
import "SafeMath.sol";
import "Address.sol";
import "SafeERC20.sol";
import "Math.sol";

import { IGauge, IGaugeFactory, ICurveFi } from "curve.sol";
import { IUniswapV2Router02 } from "uniswap.sol";
import { BaseStrategy, StrategyParams } from "BaseStrategy.sol";

abstract contract StrategyCurveBase is BaseStrategy {
    using SafeERC20 for IERC20;
    using Address for address;
    using SafeMath for uint256;

    /* ========== STATE VARIABLES ========== */
    // these should stay the same across different wants.

    // Curve stuff
    IGauge public constant gauge =
        IGauge(0x319E268f0A4C85D404734ee7958857F5891506d7); // Curve gauge contract, most are tokenized, held by strategy

    IGaugeFactory public constant gaugeFactory =
        IGaugeFactory(0xabC000d88f23Bb45525E447528DBF656A9D55bf5);

    // keepCRV stuff
    uint256 public keepCRV; // the percentage of CRV we re-lock for boost (in basis points)
    uint256 internal constant FEE_DENOMINATOR = 10000; // this means all of our fee values are in basis points

    IERC20 public constant crv =
        IERC20(0x1E4F97b9f9F913c46F1632781732927B9019C68b);
    IERC20 public constant wftm =
        IERC20(0x21be370D5312f44cB42ce377BC9b8a0cEF1A4C83);

    bool internal forceHarvestTriggerOnce; // only set this to true externally when we want to trigger our keepers to harvest for us

    string internal stratName; // set our strategy name here

    /* ========== CONSTRUCTOR ========== */

    constructor(address _vault) public BaseStrategy(_vault) {}

    /* ========== VIEWS ========== */

    function name() external view override returns (string memory) {
        return stratName;
    }

    function stakedBalance() public view returns (uint256) {
        return gauge.balanceOf(address(this));
    }

    function balanceOfWant() public view returns (uint256) {
        return want.balanceOf(address(this));
    }

    function estimatedTotalAssets() public view override returns (uint256) {
        return balanceOfWant().add(stakedBalance());
    }

    /* ========== MUTATIVE FUNCTIONS ========== */
    // these should stay the same across different wants.

    function adjustPosition(uint256 _debtOutstanding) internal override {
        if (emergencyExit) {
            return;
        }
        // Send all of our LP tokens to deposit to the gauge if we have any
        uint256 _toInvest = balanceOfWant();
        if (_toInvest > 0) {
            gauge.deposit(_toInvest);
        }
    }

    function liquidatePosition(uint256 _amountNeeded)
        internal
        override
        returns (uint256 _liquidatedAmount, uint256 _loss)
    {
        uint256 _wantBal = balanceOfWant();
        if (_amountNeeded > _wantBal) {
            // check if we have enough free funds to cover the withdrawal
            uint256 _stakedBal = stakedBalance();
            if (_stakedBal > 0) {
                gauge.withdraw(
                    Math.min(_stakedBal, _amountNeeded.sub(_wantBal))
                );
            }
            uint256 _withdrawnBal = balanceOfWant();
            _liquidatedAmount = Math.min(_amountNeeded, _withdrawnBal);
            _loss = _amountNeeded.sub(_liquidatedAmount);
        } else {
            // we have enough balance to cover the liquidation available
            return (_amountNeeded, 0);
        }
    }

    // fire sale, get rid of it all!
    function liquidateAllPositions() internal override returns (uint256) {
        uint256 _stakedBal = stakedBalance();
        if (_stakedBal > 0) {
            // don't bother withdrawing zero
            gauge.withdraw(_stakedBal);
        }
        return balanceOfWant();
    }

    function _claimRewards() internal {
        gaugeFactory.mint(address(gauge));
    }

    function claimRewards() external onlyVaultManagers {
        // Claims any pending CRV
        //
        // Mints claimable CRV from the factory gauge. Reward tokens are sent to `msg.sender`
        // The method claim_rewards() from the old gauge now only applies to third-party tokens.
        // There are no third-party tokens in this strategy.
        _claimRewards();
    }

    function prepareMigration(address _newStrategy) internal override {
        // Withdraw LP tokens from the gauge. The transfer to the new strategy is done
        // by migrate() in BaseStrategy.sol
        uint256 _stakedBal = stakedBalance();
        if (_stakedBal > 0) {
            gauge.withdraw(_stakedBal);
        }
    }

    function protectedTokens()
        internal
        view
        override
        returns (address[] memory)
    {}

    /* ========== SETTERS ========== */

    // These functions are useful for setting parameters of the strategy that may need to be adjusted.

    // Set the amount of CRV to be locked in Yearn's veCRV voter from each harvest. Default is 10%.
    function setKeepCRV(uint256 _keepCRV) external onlyAuthorized {
        require(_keepCRV <= 10_000);
        keepCRV = _keepCRV;
    }

    // This allows us to manually harvest with our keeper as needed
    function setForceHarvestTriggerOnce(bool _forceHarvestTriggerOnce)
        external
        onlyAuthorized
    {
        forceHarvestTriggerOnce = _forceHarvestTriggerOnce;
    }
}

contract StrategyCurveTricrypto is StrategyCurveBase {
    /* ========== STATE VARIABLES ========== */
    // these will likely change across different wants.

    // Curve stuff
    ICurveFi public constant curve =
        ICurveFi(0x3a1659Ddcf2339Be3aeA159cA010979FB49155FF); // This is our pool specific to this vault.

    // we use these to deposit to our curve pool
    address public targetToken; // this is the token we sell into, WETH, WBTC, or fUSDT
    IERC20 public constant wbtc =
        IERC20(0x321162Cd933E2Be498Cd2267a90534A804051b11);
    IERC20 public constant weth =
        IERC20(0x74b23882a30290451A17c44f4F05243b6b58C76d);
    IERC20 public constant fusdt =
        IERC20(0x049d68029688eAbF473097a2fC38ef61633A3C7A);
    IUniswapV2Router02 public router =
        IUniswapV2Router02(0xF491e7B69E4244ad4002BC14e878a34207E38c29); // this is the router we swap with, start with spookyswap

    address public constant voter = 0x72a34AbafAB09b15E7191822A679f28E067C4a16; // sms

    /* ========== CONSTRUCTOR ========== */

    constructor(address _vault, string memory _name)
        public
        StrategyCurveBase(_vault)
    {
        // You can set these parameters on deployment to whatever you want
        maxReportDelay = 2 days; // 2 days in seconds
        healthCheck = 0xf13Cd6887C62B5beC145e30c38c4938c5E627fe0; // health.ychad.eth

        // these are our standard approvals. want = Curve LP token
        address spooky = 0xF491e7B69E4244ad4002BC14e878a34207E38c29;
        address spirit = 0x16327E3FbDaCA3bcF7E38F5Af2599D2DDc33aE52;
        want.approve(address(gauge), type(uint256).max);
        crv.approve(spooky, type(uint256).max);
        crv.approve(spirit, type(uint256).max);

        // set our strategy's name
        stratName = _name;

        // these are our approvals and path specific to this contract
        wbtc.approve(address(curve), type(uint256).max);
        weth.approve(address(curve), type(uint256).max);
        fusdt.safeApprove(address(curve), type(uint256).max);

        // start off with fusdt
        targetToken = address(fusdt);
    }

    /* ========== MUTATIVE FUNCTIONS ========== */
    // these will likely change across different wants.

    function prepareReturn(uint256 _debtOutstanding)
        internal
        override
        returns (
            uint256 _profit,
            uint256 _loss,
            uint256 _debtPayment
        )
    {
        // Claim and get a fresh snapshot of the strategy's CRV balance
        _claimRewards();

        uint256 crvBalance = crv.balanceOf(address(this));

        // Sell CRV if we have any
        if (crvBalance > 0) {
            // keep some of our CRV to increase our boost
            uint256 sendToVoter = crvBalance.mul(keepCRV).div(FEE_DENOMINATOR);
            if (keepCRV > 0) {
                crv.safeTransfer(voter, sendToVoter);
            }

            // check our balance again after transferring some crv to our voter
            crvBalance = crv.balanceOf(address(this));

            // sell the rest of our CRV
            if (crvBalance > 0) {
                _sellToken(address(crv), crvBalance);
            }
        }

        uint256 wethBalance = weth.balanceOf(address(this));
        uint256 wbtcBalance = wbtc.balanceOf(address(this));
        uint256 fusdtBalance = fusdt.balanceOf(address(this));

        // deposit our balance to Curve if we have any
        if (wethBalance > 0 || wbtcBalance > 0 || fusdtBalance > 0) {
            curve.add_liquidity([fusdtBalance, wbtcBalance, wethBalance], 0);
        }

        // debtOustanding will only be > 0 in the event of revoking or if we need to rebalance from a withdrawal or lowering the debtRatio
        uint256 stakedBal = stakedBalance();
        if (_debtOutstanding > 0) {
            if (stakedBal > 0) {
                // don't bother withdrawing if we don't have staked funds
                gauge.withdraw(Math.min(stakedBal, _debtOutstanding));
            }
            uint256 _withdrawnBal = balanceOfWant();
            _debtPayment = Math.min(_debtOutstanding, _withdrawnBal);
        }

        // serious loss should never happen, but if it does (for instance, if Curve is hacked), let's record it accurately
        uint256 assets = estimatedTotalAssets();
        uint256 debt = vault.strategies(address(this)).totalDebt;

        // if assets are greater than debt, things are working great!
        if (assets > debt) {
            _profit = assets.sub(debt);
            uint256 _wantBal = balanceOfWant();
            if (_profit.add(_debtPayment) > _wantBal) {
                // this should only be hit following donations to strategy
                liquidateAllPositions();
            }
        }
        // if assets are less than debt, we are in trouble
        else {
            _loss = debt.sub(assets);
        }

        // we're done harvesting, so reset our trigger if we used it
        forceHarvestTriggerOnce = false;
    }

    // Sells our CRV for our target token
    function _sellToken(address token, uint256 _amount) internal {
        address[] memory tokenPath = new address[](3);
        tokenPath[0] = address(token);
        tokenPath[1] = address(wftm);
        tokenPath[2] = address(targetToken);
        IUniswapV2Router02(router).swapExactTokensForTokens(
            _amount,
            uint256(0),
            tokenPath,
            address(this),
            block.timestamp
        );
    }

    /* ========== KEEP3RS ========== */

    function harvestTrigger(uint256 callCostinEth)
        public
        view
        override
        returns (bool)
    {
        StrategyParams memory params = vault.strategies(address(this));

        // harvest no matter what once we reach our maxDelay
        if (block.timestamp.sub(params.lastReport) > maxReportDelay) {
            return true;
        }

        // trigger if we want to manually harvest
        if (forceHarvestTriggerOnce) {
            return true;
        }

        // otherwise, we don't harvest
        return false;
    }

    // convert our keeper's eth cost into want, we don't need this anymore since we don't use baseStrategy harvestTrigger
    function ethToWant(uint256 _ethAmount)
        public
        view
        override
        returns (uint256)
    {
        return _ethAmount;
    }

    /* ========== SETTERS ========== */

    // These functions are useful for setting parameters of the strategy that may need to be adjusted.
    // Set optimal token to sell harvested funds for depositing to Curve.
    // Default is fUSDT, but can be set to WETH or WBTC as needed by strategist or governance.
    function setOptimal(uint256 _optimal) external onlyAuthorized {
        if (_optimal == 0) {
            targetToken = address(weth);
        } else if (_optimal == 1) {
            targetToken = address(wbtc);
        } else if (_optimal == 2) {
            targetToken = address(fusdt);
        } else {
            revert("incorrect token");
        }
    }

    // spookyswap generally has better liquidity. if this changes, we can use spiritswap.
    function setUseSpooky(bool useSpooky) external onlyAuthorized {
        if (useSpooky) {
            router = IUniswapV2Router02(
                0xF491e7B69E4244ad4002BC14e878a34207E38c29
            ); // spookyswap's router
        } else {
            router = IUniswapV2Router02(
                0x16327E3FbDaCA3bcF7E38F5Af2599D2DDc33aE52
            ); // spiritswap router
        }
    }
}

## Tools

### Ape Safe
ape safe from the yearn team for creating complex transactions through a gnosis safe multisig. This accomplishes a bundled transaction that can be tested prior to getting sent for multisig confirmation. Best for daos and using defi thru gnosis safe

https://safe.ape.tax/quickstart.html
repo
https://github.com/banteg/ape-safe

this article explains how to use cowswap with gnosis safe for batched txszz
https://hackmd.io/@2jvugD4TTLaxyG3oLkPg-g/H14TQ1Omt

cowswap has also been getting used a lot recently with batched txs, specifically the bahamas drama where the hacker used cowswap for settlements
https://twitter.com/wavey0x/status/1594112340206956544?s=46&t=tu_NnzhzICnyss_9Z_6hVQ

Gauge boost calculator for Curve and Yearn vaults on curve
https://dao.curve.fi/minter/calc
![[Pasted image 20220608111315.png]]