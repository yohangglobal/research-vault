# Using SafeSnap, first gov tool suite for DAOs
#tools #research #treasurymanagement 

Medium article:
https://blog.gnosis.pm/introducing-safesnap-the-first-in-a-decentralized-governance-tool-suite-for-the-gnosis-safe-ea67eb95c34f

## SafeSnap breakdown 
![[Pasted image 20220608114707.png]]

## Setting up the Module
Zodiac module
https://github.com/gnosis/zodiac-module-reality

## How the solution works
![[Pasted image 20220608114942.png]]

Just to be more clear, the SafeSnap module is an oracle-based solution that looks something like this:

-   A Gnosis Safe module, where anyone can create a new proposal: an array of multisend transaction payloads.
-   Each proposal is a Reality.eth question asking if (1) the linked Snapshot proposal passed, (2) did the proposal include the payload, and (3) does the payload do what the proposal describes.
-   If the proposal passes on Snapshot, then Reality.eth should resolve to the same outcome, and after a 24 hour cooldown period, the proposal’s transactions are executable by anyone.
-   Reality uses an ERC-20 token (a given DAO’s governance token) for the bond. The minimum bond can be set by way of a proposal to the DAO.
-   The UI is a Snapshot plugin, in which users can enter an array of tx-payloads to be executed sequentially by the Gnosis Safe if the proposal passes. Once the proposal has passed, the Reality.eth question has resolved, and the 24 hour cooldown period is over, there is the option on the Snapshot interface to trigger each of the multisend transactions in the proposal.
