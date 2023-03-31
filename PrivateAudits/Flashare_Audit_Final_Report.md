
![](https://i.imgur.com/vNTieXv.jpeg)
### Table of Contents

- [1. About Kiki](#1.-About-Kiki)
- [2. Disclaimer](#2.-Disclaimer)
- [3. Risk Classification](#3.-Risk-Classification)
  - [Impact](#3.1-Impact)
  - [Likelihood](#3.2-Likelihood)
  - [Action Required for Severity Issues](#3.3-Action-Required)
- [4. Executive Summary](#4.-Executive-Summary)
  - [Summary](#4.1-Summary)
  - [Issues Found](#4.2-Issues-Found)
  - [Qualitative Analysis](#4.3-Qualitative-Analysis)
  - [Decentralization Score](#4.4-Decentralization-Score)
- [5. Scope](#5.-Scope)
- [6. Roles](#6.-Roles)
  - [Roles](#6.1-Roles)
- [7. System Overview](#7.-System-Overview)
- [8. Findings](#8.-Findings)
  - [High](#8.2.-High)
  - [Medium](#8.3-Medium)
  - [Low](#8.4-Low)
  - [Gas Optimization](#8.5-Gas-Optimization)
  - [Informational](#8.6-Informational)
- [9. Additional Recommendations](#9.-Additional-Recommendations) 
- [10. Centralization Risks](#10.-Centralization-Risks)
- [11. Conclusion](#11.-Conclusion)

## 1. About Kiki

I am an independent smart contract security researcher. With a background in Computer Science and Business. I strive to provide thorough and quality service in every audit I partake in. To read more about me you may visit my [github](https://github.com/devNamedKiki/Audits), [twitter](https://twitter.com/Kiki_developer), and/or [linkedin](https://www.linkedin.com/in/kiki-brown-2191a525b/).

## 2. Disclaimer

> A smart contract security review can never verify the complete absence of vulnerabilities. This is a time, resource and expertise bound effort where I try to find as many vulnerabilities as possible. 
>
> This report is not, nor should be considered, an “endorsement” or “disapproval” of any particular project or team. This report is not, nor should be considered, an indication of the economics or value of any “product” or “asset” created by any team or project that contracts Kiki to perform a security assessment. This report does not provide any warranty or guarantee regarding the absolute bug-free nature of the technology analyzed, nor do they provide any indication of the technologies proprietors, business, business model or legal compliance.
> 
> This report should not be used in any way to make decisions around investment or involvement with any particular project. This report in no way provides investment advice, nor should be leveraged as investment advice of any sort. This report represents an extensive assessing process intending to help our customers increase the quality of their code while reducing the high level of risk presented by cryptographic tokens and blockchain technology.
> 
> Blockchain technology and cryptographic assets present a high level of ongoing risk. Kiki's position is that each company and individual are responsible for their own due diligence and continuous security. Kiki’s goal is to help reduce the attack vectors and the high level of variance associated with utilizing new and consistently changing technologies, and in no way claims any guarantee of security or functionality of the technology we agree to analyze.
> 
> The assessment services provided by Kiki is subject to dependencies and under continuing
> development. You agree that your access and/or use, including but not limited to any services, reports, and materials, will be at your sole risk on an as-is, where-is, and as-available basis. Cryptographic tokens are emergent technologies and carry with them high levels of technical risk and uncertainty. The assessment reports could include false positives, false negatives, and other unpredictable results. The services may access, and depend upon, multiple layers of third-parties.
> 
> Notice that smart contracts deployed on the blockchain are not resistant from internal/external exploit. Notice that active smart contract owner privileges constitute an elevated impact to any smart contract’s safety and security. Therefore, Kiki does not guarantee the explicit security of the audited smart contract, regardless of the verdict.


## 3. Risk Classification

|        | High     | Medium | Low    |
| ------ | -------- | ------ | ------ |
| High   | Critical | High   | Medium |
| Medium | High     | Medium | Low    |
| Low    | Medium   | Low    | Low    |

### 3.1 Impact

- High
  - Leads to a significant material loss of assets in the protocol or significantly harms a group of users.
- Medium
  - Only a small amount of funds can be lost or a core functionality of the protocol is affected.
- Low
  - Any kind of unexpected behavior with some of the protocol's functionalities.

### 3.2 Likelihood

- High
  - Almost certain to happen, easy to perform, or not easy but highly incentivized.
- Medium
  - Only conditionally possible or incentivized, but still relatively incentivized.
- Low
  - Little incentive and would need extra ordinary events to occur for this to happen.

### 3.3 Action Required

- Critical
  - Must fix as soon as possible (if already deployed)
- High
  - Must fix
- Medium
  - Should fix
- Low
  - Could fix

## 4. Executive Summary

Over the course of 3 days in total. Flashare engaged with Kiki to review the Flashare protocol. In this period of time a total of 17 issues were found.


### 4.1 Summary

| Project Name             | <span style="font-weight:normal">Flashare</span> |
| ------------------------ | ------------------------------------------------ |
| <b>Type</b>              | Decentralized Fundraiser                         |
| <b>Commit</b>            | e81090602dd701b4210059ca90dbab211a6efd5c                                          |
| <b>Audit Timeline</b>    | 3/23 - 3/25                                      |
| <b>Fix Period</b>        | 3/26 - 3/29                                      |
|     <b>Mitigation Review</b>                     |    3/29 - 3/30                                              |
| <b>Mitigation Commit</b>  |      a9cc728db37186125ad2fa2c563c8724713f416f                               |

### 4.2 Issues Found

| Severity         | Count | Fixed | Acknowlewdged |
| ---------------- | ----- | ----- | ------------- |
| Critical         |   0    |       |               |
| High             |  1     |   1    |               |
| Medium           |   2    |   2    |               |
| Low              |   2    |   2    |               |
| Gas Optimization |   4    |   2    | 2              |
| Informational    |    8   |       |    8           |
| Total            |    17   |    7   |       10        |

## 4.3 Qualitative Analysis



|  Metric |  Rating |  Comment |
| -------- | -------- | -------- |
| Code Complexity         |   Excellent       |     Functionality is kept simple and organized    |
|    Documentation      |    Moderate      |  Documentation could be improved        |
|  Best Practices        |     Moderate     |    Some best practices are implemeted      |


## 4.4 Decentralization Score


The rating represents how decentralized the protocol is. The rating system operates on a scale of 1 -10. 1 Being very centralized, 10 Being very decentralized. 

|  Rating |
| -------- |
| 2.5   |


## 5. Scope

| Files In Scope        | SLOC    |
| --------------------- | --- |
| <i>Contracts: 2</i>   |     |
| Vendor.sol            |   65  |
| GFSX.sol              |   125  |
| <b>Total Files: 2</b> |  190   |

## 6. Roles

### 6.1 Roles

- Owner (Vendor)
    - Can pause buying and selling functionality
    - Can withdraw matic
- Token Owner
    - Controls the minting and burning of GFSX token.
- User
    - Buys and sells GSFX tokens.

## 7. System Overview

- Vendor.sol
    -  Local exchange for users to buy and sell GSFX tokens. 
    -   GSFX tokens are sold at a fixed 1000th of Matic.


- GFSX.sol
    - ERC20 token which is used as the gas token in the vendor contract.
    - Owner creates the token and then has control minting and burning functionalities. 

## 8. Findings

---

---

### 8.2 High

---

## [H-01] User will often overpay for `gastoken`

## Summary

Anytime a user calls this function while `msg.value` and `amount` don't match the function will either revert or that user will overpay for their gas tokens. 

## Vulnerability Detail


Currently in `buyTokens()` a user will choose the amount of tokens they want to buy and also send in some Matic via `msg.value`. 

There is a require check in the function that ensures the user supplied enough Matic to buy said amount. 
`    require(msg.value>=amountMATIC,"raise the msgvalue");`

If this check passes then `amount` requested of `gastoken` gets sent that user. 
`(bool sent) = gastoken.transfer(msg.sender, amount);`

 There is no actual tie between the amount request and the value being sent to the vendor.
 


## Recommendation


 The best way to fix this would be to derive `amount` from the `msg.value`. This would avoid spending extra `msg.value`.

---

### 8.3 Medium

---

## [M-01] Attacker can frontrun `changetokenPrice()`

## Summary
An attacker can wait for the owner to change the exchange rate for gas tokens and take advantage of knowing the upcoming price.
## Vulnerability Detail
Currently the owner of the vendor contract has the ability to change the exchange rate for gas token. If an attacker saw that the owner was going to lower the exchange rate. Meaning it would take less gas tokens to exchange for a MATIC. The attacker could frontrun this transaction, buy a large amount of gas tokens while it was worth less. And then when the owner's transaction completes, the attacker can then sell the gas tokens for a guarenteed profit. 

## Recommendation

One solution would be to pause buying and selling in one transaction and then change the exchange rate in the next. This would prevent an attacker from frontrunning the exchange transaction. 


## [M-02] User can buy zero `gastoken` for non zero amount

## Summary

Currently in `buytokens()` there is no check that `amount` being transferred is greater than 0. Leaving the oppourtunity for a user to send `msg.value` to the function and not get any `gasTokens` in return. 

## Vulnerability Detail

 Becasue this is a payable function a user could send funds in without getting anything in return. Payable functions do not refund unused MATIC. In addition there is no real tie between `msg.value` and `amount` passed in. Allowing a user to lose funds due to user error. 

## Recommendation

Before the transfer is made there should be a check that `amount` is greater than 0. This way it will revert if no amout is being sent. By reverting it will prevent the user from losing whatever `msg.value` they sent.

---

### 8.4 Low

---

## [L-01] Ownership changes should utilize pull method 

In `changeManagerFlashareTokensAdd()` the owner can transfer ownership to a different address. It is recommened that this be done in two steps to prevent misassignments of ownership. Best practice would look something like this.

0) Create a variable called `electedOwner`
1) Create a function called `electOwner(address _electedOwner)` that sets `electedOwner` to `_electedOwner`.
2) Create a function called `claimOwnershisp()` in here there will be a check that ensures that `msg.sender == electedOwner`. If that check passes set `owner = msg.sender` and set `electedOwner = address(0);`



## [L-02] Unnecessary fallback function should be removed

In `GFSX.sol` there is a fallback function that does not do anything. Typically ERC20 contracts do not have a fallback as there is no real need for them. Per our discusssions it was noted that this was supposed to be payable. If payable was added all funds would be locked becasue there is no functionality to move or withdraw those funds. It is recommended that this be removed.

---

### 8.5 Gas Optimization

---

## [G-01] Variables that do not change should be marked as `immutable`.

`Owner` of the`vendor.sol` contract is initalized in the constructor and is not inteded on ever changing nor is there any functionality for that. Setting this variable to immutable would save about 25494 gas upon deployment. 

## [G-02] Unused variables should be removed.

`MainFlashare` in `vendor.sol` is not used throughout the contract but is initialized as private. Meaning there is no way to access the data stored there. Removing this variable would save about 3780 gas upon deployment. 

## [G-03] Use Custom Errors.
[Source](https://blog.soliditylang.org/2021/04/21/custom-errors/)
Instead of using error strings, to reduce deployment and runtime cost, you should use Custom Errors. This would save both deployment and runtime cost.

*Instances (15)*:
```solidity
File: GFSX.sol

203: require(ManagerFlashareTokensAdd==msg.sender,"error!");

230: require(ManagerFlashareTokensAdd==msg.sender,"error!");

```

```solidity
File: Vendor.sol

27:       require(msg.sender==owner,"error");

42:     require(msg.value > 0, "You need to send some MATIC to proceed");

45:     require(msg.value>=amountMATIC,"raise the msgvalue");

46:     require(vendorBalance >= amount, "Vendor has insufficient tokens"); 

49:     require(sent, "Failed to transfer token to user");

56:     require(tokenAmountToSell > 0, "Specify an amount of token greater than zero");

59:     require(userBalance >= tokenAmountToSell, "You have insufficient tokens"); 

62:     require(ownerMATICBalance >= amountOfMATICToTransfer, "Vendor has insufficient funds");

64:     require(sent, "Failed to transfer tokens from user to vendor");

67:     require(sent, "Failed to send MATIC to the user");

71:     require(msg.sender==owner,"error!");

73:     require(ownerBalance > 0, "No MATIC present in Vendor");

75:     require(sent, "Failed to withdraw");

```

## [G-04] Use != 0 instead of > 0 for unsigned integer comparison.

*Instances (3)*:
```solidity
File: Vendor.sol

42:     require(msg.value > 0, "You need to send some MATIC to proceed");

56:     require(tokenAmountToSell > 0, "Specify an amount of token greater than zero");

73:     require(ownerBalance > 0, "No MATIC present in Vendor");

```

---

### 8.6 Informational

---
## [I-01] Missing events for critical state changes

When certain state changes occur that are owner only type of changes there should be events emitted. 

Instances(5):

```solidity 
File: Vendor.sol

  function changeTokensPerMatic(uint256 newValue)
  function changeFlashareGasToken(address newGasTokenAdd) 
  function changeCanBuy(bool value) 
  function changeCanSell(bool value) 
  function withdrawGFSX()



```
```solidity 
File: GFSX.sol
  function changeManagerFlashareTokensAdd(address NewAddress)


```

## [I-02] Missing zero-address checks in constructor and setters

*Instances (3)*:`

```solidity
File: Vendor.sol

constructor(address gastokenadd,address MainFlashareAdd,address newOwner)
function changeTokensPerMatic(uint256 newValue)
function changeFlashareGasToken(address newGasTokenAdd)
      
```

## [I-03] `gastoken.transfer` will always return true

`transfer` will either return true or revert. No need to check if the return value will be true.  

## [I-04] Redundent check for sufficient balance
ERC20 transfers already check if sender has sufficient balance. The check inside of `buytokens()` isn't necessary.

## [I-05] Inconsistant naming conventions

For readability it is good to use consistant naming conventions. Below you will see both these variables are set to the same value but are named differently.

``` solidity
    uint256 ownerMATICBalance = address(this).balance;
    uint256 ownerBalance = address(this).balance;

```

## [I-06] Functions not used internally could be marked external


*Instances (8)*:
```solidity
File: GFSX.sol

35: function changeManagerFlashareTokensAdd(address NewAddress)public{

```

```solidity
File: Vendor.sol

21:   function changeTokensPerMatic(uint256 newValue)public { 

26:   function changeFlashareGasToken(address newGasTokenAdd)public { 

31:   function changeCanBuy(bool value) public {

35:     function changeCanSell(bool value) public {

40:   function buyTokens(uint amount) public payable returns (uint256 tokenAmount) { 

54:   function sellTokens(uint256 tokenAmountToSell) public {

70:   function withdrawGFSX() public { 

```

## [I-07] Event is missing indexed fields

Index event fields make the field more quickly accessible to off-chain tools that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily best to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

*Instances (1)*:
```solidity
File: Vendor.sol

11:   event BuyTokens(address buyer, uint256 amountOfMATIC, uint256 amountOfTokens); 

```
## [I-08] require() / revert() statements should have descriptive reason strings.

*Instances (5)*:
```solidity
File: Vendor.sol

22:       require(msg.sender==owner);

32:       require(msg.sender==owner); 

36:       require(msg.sender==owner);

41:     require(canBuy==true); 

55:     require(canSell==true); 

```

---

## 9. Additional Recommendations

- Implementing [natspec](https://docs.soliditylang.org/en/v0.8.17/natspec-format.html) throughout the codebase would improve overall code quality. 
    - By improving the code quality it will make it easier to test, audit, and eventually build upon down the road. 
- More Comprehensive Testing 
    - A test suite that ensures the protocol behaves as expected would be a good start. Beyond that implementing fuzz testing and other forms of stress testing  would be benificial to the health of the protocol.
- Reduce centralization risk 
    - Implementing timelocks, reducing owner privileges, and setting boundries all would be effective ways to reduce risk.

## 10. Centralization Risks
- Currently the owner of the vendor contract can:
    - Withdraw all MATIC from the contract at any point.
    - Pause selling and buying gas tokens. 
    - Change gastoken to another ERC20 token 
    - Change the exchange rate for gastokens to MATIC
- In GSFX the owner can:
    - Mint and burn arbitrary amount of tokens to/from any address
## 11. Conclusion

- Over the course of 3 days, 17 issues were found. 7 were fixed and 10 were acknowledged during the mitigation period.
- The ownership issue is partially fixed and should be fixed in a future commit. As are some other non-critical issues. 
- There were many changes made and it is reccomended that this protocol be tested thoroughly on a testnet to ensure proper behavior before going to mainnet.
- The overall code quality during the auditing period was moderate and the decentralization score was low. However fixing the issues found as well as implemeting the additional recommendations would improve the code quality and the decentralization score. 
