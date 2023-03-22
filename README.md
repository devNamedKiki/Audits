# Kiki's security audits, reviews, and contributions

Some of my personal security audits, reviews and contributions will be shared here.

## Guardian Audits

- [Raisin Labs - Peer to Peer Fundraiser](GuardianAudits/Raisin_Audit.pdf)
- [Poodl - Dividend Paying Token](GuardianAudits/PoodlAuditTeam2.md)

## Contest Findings

| Vulnerability                                                                                   | Severity | Vulnerability Type | Protocol | Protocol Type   | Platform |
| ----------------------------------------------------------------------------------------------- | -------- | ------------------ | -------- | --------------- | -------- |
| [Unbound loop in getLockedFunds() can cause DOS preventing refunds.](Contests/009-h.md) |  High        |        DOS            |    OpenQ      |         Bounty Platform        |    Sherlock      |
| [Max out nft deposit with low value ones making bounty undesirable.](Contests/008-m.md)         | Medium   | Transfer           | OpenQ    | Bounty Platform | Sherlock |
| [malicious or paused tokens can cause claiming to fail.](Contests/007-h.md)                     | High     | Transfer           | OpenQ    | Bounty Platform | Sherlock |
| [Token Address Limit can be reached by sending dust amounts of junk tokens.](Contests/006-m.md) | Medium   | Transfer           | OpenQ    | Bounty Platform | Sherlock |
| [Unsafe Transfer of arbitrary erc20 tokens.](Contests/001-h.md)                                 | High     | Transfer           | Cooler   | P2P Lending     | Sherlock |
| [If user repays more than what is owed the function will revert](Contests/002-m.md)             | Medium   | Front-Running      | Cooler   | P2P Lending     | Sherlock |
| [Attacker can drain fractional tokens from pair](Contests/004-m.md)                             | Medium   | Arithmatic         | Caviar   | NFT AMM         | Code4ena |
| [Dutch auction getPrice() formula can lead to price reaching 0](Contests/003-h.md)              | High     | Arithmatic         | Escher   | NFT Marketplace | Code4ena |
| [Funds will be locked in FixedSale.sol if all editions are not sold.](Contests/005-m.md)        | Medium   | Locked Funds       | Escher   | NFT Marketplace | Code4ena |
