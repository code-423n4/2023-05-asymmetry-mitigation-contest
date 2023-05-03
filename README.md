# Sponsorname - Mitigation contest details
- Total Prize Pool: $15,000 USDC 
- [Warden guidelines for C4 mitigation reviews](https://code4rena.notion.site/Guidelines-for-Versus-mitigation-reviews-ed10fc5cfbf640bd8dcec66f38b343c4)
- Submit findings [using the C4 form](https://code4rena.com/contests/2023-05-asymmetry-mitigation-contest/submit)
- Starts  04 May 2023 20:00 UTC
- Ends 09 May 2023 20:00 UTC

## Important note 

Each warden must submit a mitigation review for *every High and Medium finding* from the parent contest. **Incomplete mitigation reviews will not be eligible for awards.**

## Findings being mitigated

Mitigations of all High and Medium issues will be considered in-scope and listed here.

- [H-01: An attacker can manipulate the preDepositvePrice to steal from other users.](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/1098)
- [H-02: A temporary issue shows in the staking functionality which leads to the users receiving less minted tokens.](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/1004)
- [H-03: Users can fail to unstake and lose their deserved ETH because malfunctioning or untrusted derivative cannot be removed.](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/703)
- [H-04: Price of sfrxEth derivative is calculated incorrectly.](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/641)
- [H-05: Reth poolPrice calculation may overflow.](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/593)
- [H-06: WstEth derivative assumes a ~1=1 peg of stETH to ETH.](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/588)
- [H-07: Reth.sol: Withdrawals are unreliable and depend on excess RocketDepositPool balance which can brick the whole protocol.](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/210)
- [H-08: Staking, unstaking and rebalanceToWeight can be sandwiched (Mainly rETH deposit).](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/142)

- [M-01: Division before multiplication truncate minOut and incurs heavy precision loss and result in insufficient slippage protection](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/1078)
- [M-02: sFrxEth may revert on redeeming non-zero amount](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/1049)
- [M-03: potential stake() DoS if sole safETH holder (ie: first depositor) unstakes totalSupply - 1](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/1016)
- [M-04: Lack of deadline for uniswap AMM](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/932)
- [M-05: Missing derivative limit and deposit availability checks will revert the whole stake() function](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/812) 
- [M-06: DoS due to external call failure](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/770)
- [M-07: In de-peg scenario, forcing full exit from every derivative & immediately re-entering can cause big losses for depositors](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/765)
- [M-08: Possible DoS on unstake()](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/685)
- [M-09: Non-ideal rETH/WETH pool used pays unnecessary fees](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/673)
- [M-10: Stuck ether when use function stake with empty derivatives(derivativeCount = 0)](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/363)
- [M-11: Residual ETH unreachable and unuitilized in SafEth.sol](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/152)
- [M-12: No slippage protection on stake() in SafEth.sol](https://github.com/code-423n4/2023-03-asymmetry-findings/issues/150)


## Overview of changes

Most of the mitigations I feel are self explanatory, and the Out of Scope ones are low priority that I think it is very straight forward.

The one exception is H-04, I would like extra attention towards that one because we are assuming 1:1 but are reverting if the CRV pool is depegged.  I think there could be a better solution, but it seems that we had many 
issues that had separate solutions, one being adding a chainlink oracle, which doesn't exist.


## Mitigations to be reviewed

| URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| https://github.com/asymmetryfinance/smart-contracts/pull/282/files | H-01 | Use internal accounting to get the balance | 
| https://github.com/asymmetryfinance/smart-contracts/pull/209/files | H-02 | Don't get rETH from pool on deposits | 
| https://github.com/asymmetryfinance/smart-contracts/pull/264/files | H-03 | Enable/Disable Derivatives | 
| https://github.com/asymmetryfinance/smart-contracts/pull/262/files | H-04 | To protect against oracle attacks we assume FRX is 1:1 with ETH and revert if the oracle says otherwise since there is no chainlink for FRX | 
| https://github.com/asymmetryfinance/smart-contracts/pull/209/files | H-05 | Using Chainlink to get price instead of poolPrice | 
| https://github.com/asymmetryfinance/smart-contracts/pull/242/files | H-06 | Using Chainlink to get price instead of assuming 1:1 | 
| https://github.com/asymmetryfinance/smart-contracts/pull/258/files | H-07 | Check if withdraw from deposit contract possible | 
| https://github.com/asymmetryfinance/smart-contracts/pull/209/files | H-08 | Using Chainlink to get price instead of poolPrice | 
| https://github.com/asymmetryfinance/smart-contracts/pull/276/files | M-01 | Don't divide before multiply | 
| https://github.com/asymmetryfinance/smart-contracts/pull/264/files | M-02 | Fixing it by enable/disable derivatives | 
| https://github.com/asymmetryfinance/smart-contracts/pull/228/files | M-04 | Using swapTo/swapFrom directly from rocketpool | 
| https://github.com/asymmetryfinance/smart-contracts/pull/264/files | M-05 | Fixing it by enable/disable derivatives | 
| https://github.com/asymmetryfinance/smart-contracts/pull/209/files | M-08 | Use Chainlink to get rETH | 
| https://github.com/asymmetryfinance/smart-contracts/pull/208/files | M-10 | Check derivativeCount on stake | 
| https://github.com/asymmetryfinance/smart-contracts/pull/226 | M-11 | Use entire balance for rebalance | 
| https://github.com/asymmetryfinance/smart-contracts/pull/252/files | M-12 | Pass in minAmount | 

## Out of Scope

| Reason | Issue |
| ----------- | ------------- |
| We will be manually holding safETH to prevent this, if not redeploy | M-03 |
| This is as expected | M-06  | 
| Will need a black swan event to happen and will upgrade rebalanceToWeights later to handle this | M-07  | 
