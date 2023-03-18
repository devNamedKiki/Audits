# Kiki's security audits, reviews, and contributions

Some of my personal security audits, reviews and contributions will be shared here.

## Guardian Audits

- [Raisin Labs - Peer to Peer Fundraiser](GuardianAudits/Raisin_Audit.pdf)
- [Poodl - Dividend Paying Token](GuardianAudits/PoodlAuditTeam2.md)

## Contest Findings

| Vulnerability                                                                            | Severity                                 | Vulnerability Type | Protocol | Protocol Type   | Platform |
| ---------------------------------------------------------------------------------------- | ---------------------------------------- | ------------------ | -------- | --------------- | -------- |
| [Unsafe Transfer of arbitrary erc20 tokens.](Contests/001-h.md)                          | <span style="color:Red">High</span>      | Transfer           | Cooler   | P2P Lending     | Sherlock |
| [If user repays more than what is owed the function will revert](Contests/002-m.md)      | <span style="color:Orange">Medium</span> | Front-Running      | Cooler   | P2P Lending     | Sherlock |
| [Attacker can drain fractional tokens from pair](Contests/004-m.md)                      | <span style="color:Orange">Medium</span> | Arithmatic         | Caviar   | NFT AMM         | Code4ena |
| [Dutch auction getPrice() formula can lead to price reaching 0](Contests/003-h.md)       | <span style="color:Red">High<span>       | Arithmatic         | Escher   | NFT Marketplace | Code4ena |
| [Funds will be locked in FixedSale.sol if all editions are not sold.](Contests/005-m.md) | <span style="color:Orange">Medium</span> | Locked Funds       | Escher   | NFT Marketplace | Code4ena |
