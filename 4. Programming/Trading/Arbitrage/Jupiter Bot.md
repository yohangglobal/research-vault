# Arbing on Jupiter
#dev #solana 

Source: https://github.com/ARBProtocol/solana-jupiter-bot

This bot is an open-source CLI tool that allows you to automate your crypto trading strategies on the Solana blockchain. The bot is currently written in JS and uses the [Jupiter SDK](https://docs.jup.ag/jupiter-core/jupiter-sdk/v1) to find routes and execute trades.

## nav

### [features](#features) · [CLI UI](#cli-ui) · ⚡️[install](#install) · [quickstart](#quickstart) · [tips](#some-tips-👀) · [hotkeys](#hotkeys) · [contributing](#contributing) · [license](#license) · [risk](#risk-disclaimer)

---

## features

- [x] mainnet / devnet network support
- [x] all **Jupiter Aggregator** coins
- [x] easy to use **Config Wizard**
- [x] CLI UI
- **Trading strategies**
  - [x] Arbitrage strategy
  - [x] PingPong strategy
  - [ ] limit swap\*
- **Slippage management**
  - [x] `ProfitOrKill`
  - [x] percentage % slippage
- **Profit management**
  - [x] min profit % _(target)_
- **Charts**
  - [x] latency chart
  - [x] simulated profit chart
- **History & Statistics**
  - [x] history of trades (CLI table)
  - [x] statistics of all trades
  - [ ] export to CSV\*
- **Advanced**

  - [x] custom UI colors
  - [x] min. interval beetween iterations _(to avoid 429)_
  - [ ] switch betweem multiple RPCs\*
  - [ ] Telegram notifications \ monitoring\*
  - [ ] Telegram management\*

- [x] hotkeys
- [x] lots of fun
- [ ] bug free 🥲

\* not yet implemented / may never be implemented

# CLI UI

> ⚠️ EPILEPSY WARNING - CLI UI is constantly refreshed and may be disruptive for sensitive people

🔥 CLI UI helps you monitor your trading strategy with little impact on performance.

CLI UI currently displays a simulated profit chart and latency chart. The latency chart shows you the time taken to compute routes with Jupiter SDK.

All trades are stored in trades history and will be shown in the table. Table is limited to 5 entries, but history stores all trades.

💡 UI elements can be hidden or shown using [hotkeys](#hotkeys).

![](https://github.com/arbprotocol/solana-jupiter-bot/blob/main/.gifs/wizard.gif)

![](https://github.com/arbprotocol/solana-jupiter-bot/blob/main/.gifs/bot.gif)

![](https://github.com/arbprotocol/solana-jupiter-bot/blob/main/.gifs/history.gif)

· [back to top](#nav) ·

# install

> Please don't use `npm`, use `yarn` instead.

```bash
$ git clone https://github.com/arbprotocol/solana-jupiter-bot && cd solana-jupiter-bot
$ yarn
```

Set your wallet private key in the `.env` file

```js
SOLANA_WALLET_PRIVATE_KEY =
	hgq847chjjjJUPITERiiiISaaaAWESOMEaaANDiiiIwwWANNAbbbBErrrRICHh;
```

Set the default RPC
**_ARB Protocol RPC is used by default_**

```js
SOLANA_WALLET_PRIVATE_KEY=hgq847chjjjJUPITERiiiISaaaAWESOMEaaANDiiiIwwWANNAbbbBErrrRICHh
DEFAULT_RPC=https://my-super-lazy-rpc.gov
```

· [back to top](#nav) ·

# quickstart

1. Clone this repo
2. Install dependencies
3. Set your wallet private key in the `.env` file
4. Run `yarn start` to start the Config Wizard
5. Follow the steps in the Config Wizard

```
  Usage:
    $ yarn start
      This will open Config Wizard and start the bot

    $ yarn trade
      Start Bot and Trade with latest config

    $ yarn wizard
      Start Config Wizard only
```

### some tips 👀

🔨 The bot is a Tool, not a holy grail that will make you rich just by running it. If you don't know what you are doing, you will lose money.

👉 RPC / Network speed & good trading strategy is the key to success.

🙉 Not everything is so obvious. eg. a larger trade size can lead to smaller profits than a lower trade size.

🛑 If you frequently get 429 errors, you should increase the `minInterval` in the config (`Advanced` step).

🥵 You want to `arbitrage` USDC or USDT? YES! Guess what? E V E R Y O N E wants to arbitrage USDC or USDT. If you don't have access to a super fancy RPC, there is a good chance you will end up with lots of 'Slippage errors'.

🥶 `SLIPPAGE ERRORS` are not bot errors. They are part of the Solana blockchain. If you want to avoid them you have to go with the super fancy RPC or pick the less popular pairs/coins - just try to find out which ones hold profit opportunities.

🏓 `PingPong` strategy is really poweful on sideways markets. Search through charts the coins that are constantly moving up and down.

🗡 `ProfitOrKill` slippage strategy is your smart seat belt. It will set the minimum output of the transaction to the last balance so you minimize the risk of losing money when the market moves against you. You always should get at least the amount from the previous trade \*_ofc you still pay the tx fees_

📡 If you can't run the bot, it's likely something wrong with the network, RPC, or config file.

😬 Don't like the intro? You can disable it in the .env file with `SKIP_INTRO=true`

· [back to top](#nav) ·

# hotkeys

While the bot is running, you can use some hotkeys that will change the behaviour of the bot or UI

`[H]` - show/hide Help

`[CTRL] + [C]` - obviously it will kill the bot

`[I]` - incognito RPC _Hide RPC address - helpful when streaming / screenshotting_

`[E]` - force execution with current setup & profit _*(may result in loss - you bypass all rules)*_

`[R]` - force execution, stop the bot _*(may result in loss - you bypass all rules)*_

`[L]` - show/hide latency chart (of Jupiter `computeRoutes()`)

`[P]` - show/hide profit chart

`[T]` - show/hide trade history table \*_table isn't working yet_

`[S]` - simulation mode switch (enable/disable trading)

· [back to top](#nav) ·

# trading strategies

    TODO

## arbitrage strategy

    TODO

## PingPong strategy

    TODO

· [back to top](#nav) ·

# slippage management

    TODO

## ProfitOrKill

It will set the minimum output of the transaction to the last balance so you minimize the risk of losing money when the market moves against you. You always should get at least the amount from the previous trade \*_ofc you still pay the tx fees_

## percentage slippage

Simple percentage slippage. The percentage slippage is calculated by the Jupiter SDK.

    TODO

· [back to top](#nav) ·

# profit management

    TODO

· [back to top](#nav) ·

# contributing

Arb Jupiter Bot is an open source project and contributions are welcome.

· [back to top](#nav) ·

# license

**MIT** yay! 🎉

· [back to top](#nav) ·

# risk disclaimer

This software is provided as is, without any warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors be liable for any claim, damages, or other liability.

· [back to top](#nav) ·

# supported tokens

| 🪙          | 🪙       | 🪙      | 🪙         | 🪙         | 🪙         | 🪙         | 🪙       |
| ----------- | -------- | ------- | ---------- | ---------- | ---------- | ---------- | -------- |
| YAKU        | agEUR    | MBS     | CWAR       | VINU       | DIO        | HIPPO      | BLT      |
| CKG         | JSOL     | INU     | WIPE       | MINECRAFT  | NEKI       | SWOLE      | BOKU     |
| OOGI        | TRTLS    | MMaps   | SOLFI      | SLX        | BMBO       | FUM        | SLB      |
| SOLA        | SOL      | USDC    | IVN        | BTC        | soETH      | soYFI      | soLINK   |
| soSUSHI     | soALEPH  | soSXP   | soCREAM    | soAKRO     | soHXRO     | SRM        | soFTT    |
| soTOMO      | soGRT    | FIDA    | KIN        | MAPS       | OXY        | BRZ        | USDT     |
| RAY         | wCAPS_v1 | wFTT_v1 | AUDIO      | wHEX_v1    | wDAI_v1    | yPRT       | wFRAX_v1 |
| wLUNA_v1    | wBUSD_v1 | oDOP    | COPE       | ROPE       | MEDIA      | STEP       | xSTEP    |
| XSB         | COBAN    | QUEST   | SLIM       | SAMO       | PANDA      | ATLAS      | POLIS    |
| TCW         | SDOGE    | YARD    | SNY        | FROG       | MOLA       | SOLAPE     | WOOF     |
| MER         | APYS     | SOLPAD  | TULIP      | TYNA       | MGT        | CHEEMS     | CATO     |
| NINJA       | BOP      | DXL     | GRAPE      | CKC        | APEX       | SOLD       | ORCA     |
| SHILL       | FTR      | renBTC  | renDOGE    | renLUNA    | SAIL       | RIN        | SCY      |
| VCC         | OXS      | FAB     | POTATO     | STR        | GU         | SOLC       | LUNY     |
| DINO        | LIQ      | CRP     | SLRS       | JET        | WOO        | LIKE       | wUST_v1  |
| METAS       | Orbs     | C98     | SBR        | LRA        | wHBTC_v1   | wHUSD_v1   | wHAPI    |
| LARIX       | SSU      | sSOL    | mSOL       | PSOL       | PORT       | MNGO       | UPS      |
| gSAIL       | PAI      | PRT     | pBTC       | pSOL       | ULA        | SUNNY      | CYS      |
| stSOL       | wstETH   | KURO    | SYP        | CRY        | DINOEGG    | SMRT       | DATE     |
| CSTR        | apUSDT   | apUSDC  | SOLR       | SPWN       | SNS        | scnSOL     | SOLX     |
| ABR         | abBUSD   | aeWETH  | aeUSDT     | aeUSDC     | aeDAI      | acUSD      | cSOL     |
| cUSDC       | cUSDT    | LDO     | rSOL       | WET        | aeFTT      | MDF        | WAG      |
| SBNK        | MNDE     | DGLN    | xUSD       | xBTC       | xSOL       | xFTT       | xETH     |
| xLUNA       | UXD      | USDCet  | USDCpo     | USDTet     | USDTpo     | DAI        | HIMA     |
| FRKT        | aaUSDT   | aaUSDC  | aaDAI      | aaWBTC     | AVAX       | FRIES      | PNT      |
| FRNT        | AURY     | DOGO    | SOLPAY     | MSI        | SAO        | CAVE       | GOFX     |
| FTT         | UST      | ETH     | SRMet      | LUNA       | AVAX       | HUSD       | BUSDet   |
| FRAX        | HBTC     | USDK    | SUSHI      | UNI        | BNB        | LINK       | PAXG     |
| HXRO        | SXP      | OASIS   | SAMU       | acUSDC     | ahBTC      | ahUSDT     | BABY     |
| SLND        | SAMOL    | SHIBA   | UXP        | MARI🌱ANA  | USDCbs     | aSOL       | USDTbs   |
| ASGARD      | SER      | PU😸    | BITCH      | TICKET     | PART       | NOM        | KITTY    |
| MEND        | IN       | SHIB    | AXSet      | DYDX       | MATICpo    | BUSDbs     | KKO      |
| WAGMI       | SCT      | MODUL   | MANA       | SAND       | SOLBEAR    | CRAT       | SVIZ     |
| GENE        | SONAR    | FOXY    | BITXBIT    | GMSOL      | SOLAB      | PHY        | CCC      |
| ELU         | HIRAM    | GM      | ICE        | JUNGLE     | REAL       | APT        | THECA    |
| SINGULARITY | 1SOL     | WEENS   | CAPY       | MIMO       | POLE       | SEEDED     | CASH     |
| SPORE       | DFL      | STARS   | sUSDC-8    | sBTC-9     | sUSDT-9    | srenBTC-10 | sCASH-9  |
| srenBTC-9   | swFTT-9  | sFTT-9  | sUSDC-9    | swhETH-9   | srenLUNA-9 | sBTC-8     | sETH-8   |
| NANA        | BURD     | SCRAP   | TTT        | abUSDT     | abUSDC     | abBTCB     | abETH    |
| DAWG        | RLB      | pUSDC   | pUSDT      | sUSDT-8    | XTAG       | TRYB       | YORK     |
| TWT         | SNTR     | CRYY    | BOFB       | aeMIM      | aeFEI      | afBTC      | afETH    |
| afUSDC      | afDAI    | $FROG   | $KSH       | PIXL       | EYE        | FREN       | CHICKS   |
| SHARDS      | MARIO    | PUFF    | BANA       | RACEFI     | GST        | GMT        | SUCH     |
| UNQ         | FORA     | RUN     | PSK        | PCN        | BLOCK      | DAOJONES   | CHB      |
| TRYB        | $ASH     | FANI    | daoSOL     | SBABYDOGE  | FANT       | PAW        | BOT      |
| CRWNY       | BASIS    | VOID    | swtUST-9   | ppUSDC     | Zion       | KLUB       | SHDW     |
| CC          | FJBT     | $FORCE  | wDingocoin | SANTA      | MEAN       | DAPE       | WMP      |
| NOVA        | MKD      | FLWR    | SEI        | PTN        | DRAW       | BAIL       | CHP      |
| atUST       | acEUR    | SMBD    | BRWNDO     | MCAKE      | SOULO      | GOOSE      | TRPY     |
| DLN         | PRISM    | NOCH    | RAD        | $YETI      | WAV        | GGSG       | ALEPH    |
| COMP        | ATS      | PEOPLE  | HYPE       | MBC        | EGO        | bSOL       | LOOT     |
| BAPE        | BNTY     | CWM     | SDO        | SB         | AART       | GUANO      | SLC      |
| BMA         | SYXT     | TINY    | CRH        | creatorpro | pHONEY     | $WOOD      | MILK     |
| DGE         | GXE      | atLUNA  | TFBK       | CMFI       | CORE       | ILU        | NOS      |
| ARTZ        | MOONBURN | CCG     | SVT        | AMMO       | GARI       | VIVAION    | cMETA    |
| eSOL        | ACM      | BXS     | sCASH-8    | sagEUR-9   | sUST-8     | ARTE       | PSY      |
| SXS         | BUD      | CELO    | FTM        | SGEM       | FCON       | POZZ       | GYC      |
| $HONEY      | BORG     | sRLY    | 1SP        | BASIC      | LSTAR      | GODZ       | WHEY     |
| GMORNN      | UM       | SIXY    | BREA       | HBB        | DOOB       | SMCK       | ENC      |
| USDH        | BIT      | DAU     | ROLL       | DARC       | NAGA       | MAGA       | NFD      |
| POT         | PENNY    | MAI     | CHIPS      | ALIEN      | MONY       | TAKI       | DUST     |
| DEV         | SHUT     | MRX     | EDO        | $WNZ       | 9LIVES     | SD         | SOLI     |
| ORIA        | FUJI     | GMFC    | $POT       | SLDR       | GNOM       | GUARD      | EPOCH    |
| JFI         | cmSOL    | prtSOL  | $SPWX      | sUSD       | SPACEGOLD  | SOLP       | NESTA    |
| $PACES      | PEEL     | HONSHU  | FRTN       | HTO        | DOPIES     | CLAN       | DAB      |
| NRC         | JJJJC    | $ROBO   | ROL        | Miku       | T1NY       | BONE       | MALL     |
| RIBBET      | RICE     | HONE    | KROBA      | BONES      | FBZ        | CHIMP      | PLAYA    |
| RING        | KRILL    | NLTK    | WAS        | MMA        | MTP        | SPM        | MRTS     |
| HENDX       | XGLI     | FAC     | DELFI      | BLEEP      | DREAM      | SKULL      | CRAFT    |
| QUACK       | BOOTY    | PURR    | KAI        | GV         | DRGNZ      | LUST       | CYRUS    |
| SKUL        | IV       | KING    | $CRECK     | BNCE       | ssoFTT-8   | sLUNA-9    | PRGC     |
| wrBTC       | CRM      | SNAP    | JUNKz      | YAW        | TOCO       | THC        | WAVE     |
| JELLY       | DGNA     | GEAR    | FamSOL     | BLOOD      | SAC        | PERP       | FFF      |
| AUR         | GENO     | LIFL    | DGOD       | solUST     | THUGZ      | PLWAV      | AGVZ     |
| PREY        | NEAR     | GLXY    | $ALL       | BM         | WAVES      | HKDD       | BMT      |
| AIR         | CHI      | ZBC     | ACA        | TRIT       | TKMK       | WATT       | DKM      |
| SAFE        | MHC      | PRIME   | NOVAX      | HNYG       | SLCL       | RATIO      | ELIXIR   |
| MHCNWS      | WOOP     | ENRX    | FUNZ       | RAMENF     | NEST       | REAP       | SMRAI    |
| API         | BOFx     | WIZE    | USDr       | DISK       | HAWK       | MONGO      | ZAP      |
| IDOLZ       | $EGG     | ACF     | FEED       | $NEON      | FORGE      | PRANA      | VSNRY    |
| OOINK       | MOSHI    | ANA     | TTST       | CARTEL     | GLXY       | ERRA       | NIRV     |
| NNI         | UNKN     | ARNM    | JOINTS     | WOW        | MNRL       | sTZC       | $FLY     |
| PLD         | RPC      | PU238   | LFNTY      | xLFNTY     | ZIG        | NEO        | CSM      |
| LILY        | SIX      | WPUFF   | VAULT      | FLWRS      | DARK       | ENX        | CREAMY   |
| GEAR        | $LUV     | OTAKU   | DPAY       | $GARY      | HALO       | EMBER      | KTRC     |
| COCU        | TENKAI   | BTL     | DEDS       | USN        | PENNY      | fUSD       | USH      |
| HDG         | KS       | 44TH    | TROOP      | MONKES     | SURF       | sRLY       | calUSD   |
| TREN        | GOLDY    | PHNX    | HCOIN      | BBI        | AERA       | VIKN       | KSW      |
| VIBEZ       | FERO     | TGT     | WNDO       | BOO        | DRIPP      | rPWNG      | rPUNK    |
| rLGND       | rZOOM    | FINE    | MILK       | DKCOIN     | $STONE     | WEYU       | TRB      |
| TRUE        | XTR      | SSURF   | GB         | NECTAR2    | DMV        | ARB        | ICHIGO   |
| svtOKAY     | RIBH     | svtFFF  | svtSMB     | svtPSK     | svtDGOD    | svtVSNRY   | svtFLARE |
| svtGGSG     | svtCWM   | svtDAPE | svtBV      | KREECHURE  | svtTHUGZ   | svtGENE    | svtAURY  |
| $TLA        | DUSK     | CRM     | KI         | WEC        | AUT        | WHALES     | ZALINA   |
| IP3         | xALGO    | OKAYB   | MC         | BOXCH      | TAP        | KST        | KNK      |
| ATH         | JFI      | MARROW  | LSI        | PCPC       | NARK       | FRR        | ABC      |
| AHT         | PRIMATES | AFSeX   | INFX       | ENG        | SNAIL      | DAPE       | TAPES    |
