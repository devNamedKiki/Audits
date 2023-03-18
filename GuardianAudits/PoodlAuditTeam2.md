![](https://i.imgur.com/zGzXYfT.jpg)


__Audit Firm__: Solidity Lab

__Client Firm__: Poodl

__Prepared By__: infamousdegen, Kiki_Dev, 0x4non, Willboy

__Delivery Date:__ March 7th, 2023

<br />

__Client Firm__ engaged Solidity Lab to review the security of its Smart Contract system. From 25/02/2023 to 07/03/2023, a team of 4 auditors reviewed the source code in scope. All findings have been recorded in the following report.

Notice that the examined smart contracts are not resistant to external/internal exploit. For a detailed understanding of risk severity, source code vulnerability, and potential attack vectors, refer to the complete audit report below.



# Project Overview

| Project Name | RaisinLabs                                                                                               |
|--------------|----------------------------------------------------------------------------------------------------------|
| Language     | Solidity                                                                                                 |
| Codebase     | https://github.com/poodlTech/tokenAudit/tree/main/contracts                           |
| Commit       | [eebe267b3fdd75a82e09cc270b3c046b2c9f2c84](https://github.com/poodlTech/tokenAudit/commit/eebe267b3fdd75a82e09cc270b3c046b2c9f2c84) |


| Delivery Date     | 07/03/2023       |
|-------------------|--------------------------------|
| Audit Methodology | Static Analysis, Manual Review |


| Vulnerability Level | Total | Pending | Declined | Acknowledged | Partially Resolved | Resolved |
|---------------------|-------|---------|----------|--------------|--------------------|----------|
| [Critical](#Critical)| 0     |   0     | 0        | 0            | 0                  | 0        |
| [High](#High)        | 0     | 1       | 0        | 0            | 0                  | 0        |
| [Medium](#Medium)    | 0     | 4       | 0        | 0            | 0                  | 0        |
| [Low](#Low)          | 0     | 4      | 0        | 0            | 0                  | 0        |

# Audit Scope & Methodology

## Scope

| ID File | SHA-256      | Checksum                              |
|---------|------------|---------------------------------------|
| A      | contracts/DividendPayingToken.sol |03754dd9bb6810afaeea9f89c43b6587a123bc485aa7383cebe1d89480fe7b12  |
| B      | contracts/Token.sol | 415199e53bce4ef12717900ca4750e5fbf53b3451f0e17702dae3f1a47ba6f76 |
| C      | contracts/Presale.sol | 15e348fa45d6d18fa032638b18e31ea0332532daadcab8aa610a42d6679fa01f |
| D     | contracts/Airdropper.sol | a3c1bfbf048d07dd257994ebf94b1984fd7160f5c0cbd579388da1cf13fc6389 |

## Methodology

The auditing process pays special attention to the following considerations:
- Testing the smart contracts against both common and uncommon attack vectors.
- Assessing the codebase to ensure compliance with current best practices and industry standards.
- Ensuring contract logic meets the specifications and intentions of the client.
- Cross-referencing contract structure and implementation against similar smart contracts produced by industry leaders.
- Thorough line-by-line manual review of the entire codebase by community auditors.

## Vulnerability Classifications

| Vulnerability Level | Classification                                                                               |
|---------------------|----------------------------------------------------------------------------------------------|
| [Critical](#Critical)            | Easily exploitable by anyone, causing loss/manipulation of assets or data.                   |
| [High](#High)                | Arduously exploitable by a subset of addresses, causing loss/manipulation of assets or data. |
| [Medium](#Medium)              | Inherent risk of future exploits that may or may not impact the smart contract execution.    |
| [Low](#Low)                 | Minor deviation from best practices.                                                         |



# Findings & Resolutions

| ID      | Title                                                                                     | Category            | Severity | Status  |
|-------|-------------------------------------------------------------------------------------------|---------------------|----------|---------|
| [H-01](#H01)  | withdrawnDividends is not updated properly while using custom tokens                                    | Logic error                | HIGH     | Pending |
| [M-01](#M01)  | Balance of dividends equal 0 for all user when the Dividend Tracker is updated - Token.sol | Logic error   | MEDIUM   | Pending |
| [M-02](#M02)  | A user can't claim his dividends before he is excluded - Token.sol | Logic error   | MEDIUM   | Pending |
| [M-03](#M03)  | Error of amount sending to the user inside buyPresale() | Logic error   | MEDIUM   | Pending |
| [M-04](#M04)  | The function buyPresale() needs to be payable                                                      | Logic error         | MEDIUM   | Pending |
| [L-01](#L01)  | Missing update when the Dividen Tracker is updated - Token.sol                                                                             | Logic error | LOW      | Pending |
| [L-02](#L02)  | Missing update when the UniswapV2Router is updated - Token.sol                                                                             | Logic error | LOW      | Pending |
| [L-03](#L03)  | No variables are instantiated - Airdropper.sol/Presale.sol                                                                             | Logic error | LOW      | Pending |
| [L-04](#L04)  | Approve is useless | Logic error   | LOW   | Pending |
| [I-01](#I01)  |A lot of state-changing methods do not emit events  |  | Informational      | Pending |
| [I-02](#I02)  | The contract Reentrancy is not used - Airdropper.sol/Presale.sol  |  | Informational      | Pending |
| [I-03](#I03)  | The library SafeMath is not needed - Airdropper.sol  |  | Informational      | Pending |







## <a id="Critical"></a>Critical




## <a id="High"></a> High

### <a id="H01"></a> H-01 withdrawnDividends is not updated properly while using custom tokens

https://github.com/poodlTech/tokenAudit/blob/main/contracts/DividendPayingToken.sol#L131


#### Description:
If a user has a custom reward token then the  withdrawnDividends[user] is never updated.
The user is able to drain all the dividends.



#### Recommendation:
Move the L136 to L134

```solidity
  function _withdrawDividendOfUser(address payable user) internal returns (uint256) {
    uint256 _withdrawableDividend = withdrawableDividendOf(user);
    if (_withdrawableDividend > 0) {
        withdrawnDividends[user] = withdrawnDividends[user].add(_withdrawableDividend);
         // if no custom reward token send BNB.
        if(!userHasCustomRewardToken[user]){
          (bool success,) = user.call{value: _withdrawableDividend, gas: stipend}("");
          if(!success) {
            withdrawnDividends[user] = withdrawnDividends[user].sub(_withdrawableDividend);
            return 0;
          }
          emit DividendWithdrawn(user, _withdrawableDividend);
          return _withdrawableDividend;
        } else {  
          // if the reward is not BNB
          emit DividendWithdrawn(user, _withdrawableDividend);
          return swapETHForTokens(user, _withdrawableDividend);
        }
    }
    return 0;
  }
```




#### Resolution:






## <a id="Medium"></a> Medium

### <a id="M01"></a> M-01 Balance of dividends equal 0 for all user when the Dividend Tracker is updated - Token.sol


https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol#L113

#### Description:
When the Dividend Tracker is updated. The balance of dividends for all the user is equal to 0.

#### Recommendation:
Create a function in order to setBalance(payable(users[i]),balanceOf(users[i])) for all the user who has n amount of Token.
```solidity=
function setAllBalance(address[] calldata holders) external onlyOwner {
        for(uint256 i = 0; i < holders.length; i++) {
            dividendTracker.setBalance(payable(holders[i]), balanceOf(holders[i]));
        }
   }
```

#### Resolution:

____




### <a id="M02"></a> M-02 A user can't claim his dividends before he is excluded - Token.sol

https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol#L175


#### Description:
Imagine a case where  a user has some dividends. If the owner of Token.sol exclude the user. The user is not able to claim his dividends before having a balance of 0.

#### Recommendation:
Send the dividends to the user before setting his balance to 0.
At L176
```diff 
+ if(dividendTracker.withdrawableDividendOf(account)>0) {
+   processAccount(account);
+}
```

#### Resolution:

-----------------


### <a id="M03"></a> M-03 Error of amount sending to the user inside buyPresale()

https://github.com/poodlTech/tokenAudit/blob/main/contracts/Presale.sol#L56


#### Description:
At line L56, we are sending the amount `value` instead of the variable `amount` that is calculated at L54.


#### Recommendation:
At L56, replace `value` by `amount`.

#### Resolution:

-----------------

### <a id="M04"></a> M-04 The function buyPresale() needs to be payable

https://github.com/poodlTech/tokenAudit/blob/main/contracts/Presale.sol#L51


#### Description:
The function buyPresale() is not payable. However, inside the function we are using `msg.value`.



#### Recommendation:
Put the function buyPresale() as payable.




#### Resolution:

-----------------


## <a id="Low"></a> Low


### <a id="L01"></a> L-01 Missing update when the Dividend Tracker is updated - Token.sol


https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol#L122
https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol#L94

#### Description:
Compared to the constructor, the Uniswap pair is not excluded from dividends when updating the Dividend Tracker. However, you can call excludeFromDividends() in a new transaction.

#### Recommendation:
At L122
```diff 
+ address _uniswapV2Pair = IUniswapV2Factory(uniswapV2Router.factory()).createPair(address(this),uniswapV2Router.WETH());
+ newDividendTracker.excludeFromDividends(_uniswapV2Pair);
```
#### Resolution:

____


### <a id="L02"></a> L-02 Missing update when the UniswapV2Router is updated - Token.sol


https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol#L127
https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol#L93
https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol#L94

#### Description:
Compared to the constructor, the UniswapV2Router is not excluded from dividends when updating the UniswapV2Router. If a new pair is created, the pair is not excluding from dividends.  However, you can call excludeFromDividends() in a new transaction.

#### Recommendation:
At L130
```diff 
+ dividendTracker.excludeFromDividends(uniswapV2Router);
```
At L135
```diff 
+ dividendTracker.excludeFromDividends(newPair);
```
With this recommendation, the old router/pair are still exclude from dividends. 

#### Resolution:

____


### <a id="L03"></a> L-03 No variables are instantiated - Airdropper.sol/Presale.sol


https://github.com/poodlTech/tokenAudit/blob/main/contracts/Airdropper.sol
https://github.com/poodlTech/tokenAudit/blob/main/contracts/Presale.sol

#### Description:
There are no variables instantiated inside these contract. Which means, all the variables are equal to 0.




#### Recommendation:
Instantiate the variables inside the constructor.


#### Resolution:

____

### <a id="L04"></a> L-04 Approve is useless -  DividendPayingToken.sol

https://github.com/poodlTech/tokenAudit/blob/main/contracts/DividendPayingToken.sol#L168


#### Description:
Inside swapETHForTokens(), there is an approval for the DividendsPayingToken token who is useless. We are sending ETH in swapExactETHForTokensSupportingFeeOnTransferTokens() so we don't need to approve something. Moreover the DividendsPayingToken token is not transferable.

#### Recommendation:
At L168
```diff 
-  _approve(path[0], address(swapRouter), ethAmount);
```

#### Resolution:

-----------------

## <a id="Informational"></a> Informational


### <a id="I01"></a> I-01 A lot of state-changing methods do not emit events - Token.sol/DividendPayingToken.sol


https://github.com/poodlTech/tokenAudit/blob/main/contracts/Token.sol
https://github.com/poodlTech/tokenAudit/blob/main/contracts/DividendPayingToken.sol

#### Description:
A lot of state-changing methods do not emit events.

### <a id="I02"></a> I-02 The contract Reentrancy is not used - Airdropper.sol/Presale.sol


https://github.com/poodlTech/tokenAudit/blob/main/contracts/Airdropper.sol
https://github.com/poodlTech/tokenAudit/blob/main/contracts/Presale.sol

#### Description:
The contract Reeantrancy is not used. Which for the current implementation, the contract is useless.

### <a id="I03"></a> I-03 The library SafeMath is not needed - Airdropper.sol


https://github.com/poodlTech/tokenAudit/blob/main/contracts/Airdropper.sol

#### Description:
The SafeMath library is not used.





## Disclaimer
> 
> This report is not, nor should be considered, an “endorsement” or “disapproval” of any particular project or team. This report is not, nor should be considered, an indication of the economics or value of any “product” or “asset” created by any team or project that contracts Solidity Lab to perform a security assessment. This report does not provide any warranty or guarantee regarding the absolute bug-free nature of the technology analyzed, nor do they provide any indication of the technologies proprietors, business, business model or legal compliance.
> 
> This report should not be used in any way to make decisions around investment or involvement with any particular project. This report in no way provides investment advice, nor should be leveraged as investment advice of any sort. This report represents an extensive assessing process intending to help our customers increase the quality of their code while reducing the high level of risk presented by cryptographic tokens and blockchain technology.
> 
> Blockchain technology and cryptographic assets present a high level of ongoing risk. Solidity Lab’s position is that each company and individual are responsible for their own due diligence and continuous security. Solidity Lab’s goal is to help reduce the attack vectors and the high level of variance associated with utilizing new and consistently changing technologies, and in no way claims any guarantee of security or functionality of the technology we agree to analyze.
> 
> The assessment services provided by Solidity Lab is subject to dependencies and under continuing
> development. You agree that your access and/or use, including but not limited to any services, reports, and materials, will be at your sole risk on an as-is, where-is, and as-available basis. Cryptographic tokens are emergent technologies and carry with them high levels of technical risk and uncertainty. The assessment reports could include false positives, false negatives, and other unpredictable results. The services may access, and depend upon, multiple layers of third-parties.
> 
> Notice that smart contracts deployed on the blockchain are not resistant from internal/external exploit. Notice that active smart contract owner privileges constitute an elevated impact to any smart contract’s safety and security. Therefore, Solidity Lab does not guarantee the explicit security of the audited smart contract, regardless of the verdict.

<br/>

____

## About

Solidity Lab is a community of practicing auditors guided by Guardian Audits.

To learn more, visit https://lab.guardianaudits.com

To view the Solidity Lab audit portfolio, visit https://github.com/GuardianAudits/LabAudits
