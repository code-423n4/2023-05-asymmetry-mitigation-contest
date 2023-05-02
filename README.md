# Sponsorname - Mitigation contest details
- Total Prize Pool: $10,000 USDC 
- [Warden guidelines for C4 mitigation reviews](https://code4rena.notion.site/Guidelines-for-Versus-mitigation-reviews-ed10fc5cfbf640bd8dcec66f38b343c4)
- Submit findings [using the C4 form](https://code4rena.com/contests/2023-05-asymmetry-mitigation-contest/submit)
- Starts TBD XXX XXX XX 20:00 UTC
- Ends TBD XXX XXX XX 20:00 UTC

## Important note 

Each warden must submit a mitigation review for *every High and Medium finding* from the parent contest. **Incomplete mitigation reviews will not be eligible for awards.**

[ ⭐️ SPONSORS ADD INFO HERE ]

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
- [M-11: Residual ETH unreachable and unuitilized in SafEth.sol] (https://github.com/code-423n4/2023-03-asymmetry-findings/issues/152)
- [M-12: No slippage protection on stake() in SafEth.sol] (https://github.com/code-423n4/2023-03-asymmetry-findings/issues/150)


## Overview of changes

Please provide context about the mitigations that were applied if applicable and identify any areas of specific concern.

## Mitigations to be reviewed

Wherever possible, mitigations should be provided in separate pull requests, one per issue. If that is not possible (e.g. because several audit findings stem from the same core problem), then please link the PR to all relevant issues in your findings repo. 

| URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| https://github.com/code4rena/sample-contracts/pull/XXX | H-01 | This mitigation does XYZ | 

## Out of Scope

Please list any High and Medium issues that were judged as valid but you have chosen not to fix.
