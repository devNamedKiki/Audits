
# [Kiki's](https://devnamedkiki.github.io/) security audits, reviews, and contributions

Some of my personal security audits, reviews and contributions will be shared here.
## Private Audits

- [Flashare - Decentralized Fund Raiser](PrivateAudits/Flashare_Audit_Final_Report.md)
## Guardian Audits

- [Raisin Labs - Peer to Peer Fundraiser](GuardianAudits/Raisin_Audit.pdf)
- [Poodl - Dividend Paying Token](GuardianAudits/PoodlAuditTeam2.md)

## Contest Findings 
(~9 findings pending)

| Vulnerability                                                                                   | Severity | Vulnerability Type | Protocol | Protocol Type   | Platform |
| ----------------------------------------------------------------------------------------------- | -------- | ------------------ | -------- | --------------- | -------- |
| [Buyer of club owner can be frontrun by owner of club.](Contests/018.md)                     |  High  |  Frontrunning      |   Footium  |   NFT       | Sherlock |
| [Unsafe transfer of arbitrary erc20 token](Contests/017.md)                     |  Medium  |  Transfer      |   Footium  |   NFT       | Sherlock |
| [Unsafe minting of footiumClubs](Contests/016.md)                     |  Medium  |  Minting      |   Footium  |   NFT       | Sherlock |
| [Royalty recipients will not get fair share of royalties.](Contests/015.md)                     |  Medium  |  Arithmatic      |   Caviar  |   Private Pool       | Code4ena |
| [ Some ERC20 tokens revert on 0 transfer.](Contests/014.md)                                     |  Medium  |  Weird ERC20      |   Caviar  |   Private Pool       | Code4ena |
| [Some base tokens will cause revert due to underflow.](Contests/013.md)                         |  Medium  |  Weird ERC20      |   Caviar  |   Private Pool       | Code4ena |
| [Frontrunning with allowence can cause users to loose funds.](Contests/011-m.md)                |  Medium  |  Frontrunning      |   Surge  |   Lending       | sherlock |
| [Once reward token is removed users wont have access to their yield.](Contests/010-m.md)        | Medium   | Yield      | Olympus  | SSLV            | Sherlock |
| [Unbound loop in getLockedFunds() can cause DOS preventing refunds.](Contests/009-h.md)         | High     | DOS                | OpenQ    | Bounty Platform | Sherlock |
| [Max out nft deposit with low value ones making bounty undesirable.](Contests/008-m.md)         | Medium   | Transfer           | OpenQ    | Bounty Platform | Sherlock |
| [malicious or paused tokens can cause claiming to fail.](Contests/007-h.md)                     | High     | Transfer           | OpenQ    | Bounty Platform | Sherlock |
| [Token Address Limit can be reached by sending dust amounts of junk tokens.](Contests/006-m.md) | Medium   | Transfer           | OpenQ    | Bounty Platform | Sherlock |
| [Unsafe Transfer of arbitrary erc20 tokens.](Contests/001-h.md)                                 | High     | Transfer           | Cooler   | Lending     | Sherlock |
| [If user repays more than what is owed the function will revert](Contests/002-m.md)             | Medium   | Front-Running      | Cooler   | Lending     | Sherlock |
| [Yield can be stolen due to delay in syncRewards()](Contests/012.md)                            | Medium   | Arithmatic         | GogoPool   | Liquid Staking         | Code4ena |
| [Attacker can drain fractional tokens from pair](Contests/004-m.md)                             | Medium   | Arithmatic         | Caviar   | NFT AMM         | Code4ena |
| [Dutch auction getPrice() formula can lead to price reaching 0](Contests/003-h.md)              | High     | Arithmatic         | Escher   | NFT Marketplace | Code4ena |
| [Funds will be locked in FixedSale.sol if all editions are not sold.](Contests/005-m.md)        | Medium   | Locked Funds       | Escher   | NFT Marketplace | Code4ena |

## Publications 

- [8 Common Smart Contract Vulnerabilities Found Throughout Audit Contest](https://medium.com/@unsnarl_secure/8-common-smart-contract-vulnerabilities-found-throughout-audit-contest-b421b80b08b5)
