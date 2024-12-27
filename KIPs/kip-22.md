---
kip: 22
title: Loyalty Points Token Standard on Bitkub Chain
description: A standard interface for loyalty points tokens on Bitkub Chain
author: Bitkub Chain (@bitkubchain), et al.
status: Draft
type: Standards Track
category: KAP
---

## Abstract

The following standard outlines a smart contract interface and logic for loyalty points tokens on Bitkub Chain that behaves similar to traditional loyalty points, enabling interoperability and composability within the decentralized ecosystem. By adhering to this standard, loyalty programs can leverage the benefits of blockchain technology, such as transparency, immutability, and programmability, while maintaining the familiar functionality of traditional loyalty points. It is proposed by deriving the KAP-20 standard of Bitkub Chain with an additional functions related to periods and token expiration.

## Motivation

A standard interface allows loyalty points tokens on Bitkub Chain to be used in the Bitkub Chain ecosystem. Traditional loyalty programs often suffer from limitations such as centralized control, limited interoperability, and opaque reward mechanisms. This proposal aims to address these issues by introducing a standardized token for loyalty points on the Bitkub Chain. This proposal aims to unlock the full potential of loyalty programs by combining the benefits of blockchain technology with the familiar functionality of traditional loyalty points. This will create a more efficient, transparent, and user-centric loyalty ecosystem. This standard interface also extends [ERC-20](https://eips.ethereum.org/EIPS/eip-20) and KAP-20.

## Specification

NOTE: The following specifications use syntax from Solidity `0.8.0` (or above)

### Token Interface

#### IAdminProjectRouter

##### isSuperAdmin

Check whether `_addr` is the Super Admin role in `_project`.

``` js
function isSuperAdmin(address _addr, string calldata _project) external view returns (bool)
```

##### isAdmin

Check whether `_addr` is the Admin role in `_project`.

``` js
function isAdmin(address _addr, string calldata _project) external view returns (bool)
```

#### IKYCBitkubChain

##### kycsLevel

Returns the KYC Level of `_addr`

``` js
function kycsLevel(address _addr) external view returns (uint256)
```

#### IKAP20

#### Methods

##### totalSupply

Returns the total token supply.

``` js
function totalSupply() external view returns (uint256)
```

##### decimals

Returns the number of decimals the token uses - e.g. `8`, means to divide the token amount by `100000000` to get its user representation.

NOTE: This method is optional in ERC-20. In KAP-20, this is a required method.

``` js
function decimals() external view returns (uint8)
```

##### symbol

Returns the symbol of the token. E.g. "HIX".

NOTE: This method is optional in ERC-20. In KAP-20, this is a required method.

``` js
function symbol() external view returns (string memory)
```

##### name

Returns the name of the token - e.g.`"MyToken"`.

NOTE: This method is optional in ERC-20. In KAP-20, this is a required method.

``` js
function name() external view returns (string memory)
```

##### allowance

Returns the amount which `spender` is still allowed to withdraw from `owner`.

``` js
function allowance(address owner, address spender) external view returns (uint256)
```

##### approve

Allows `spender` to withdraw from your account multiple times, up to the `amount` amount. If this function is called again it overwrites the current allowance with `amount`.

NOTE: To prevent attack vectors, clients SHOULD make sure to create user interfaces in such a way that they set the allowance first to 0 before setting it to another value for the same spender. THOUGH The contract itself shouldn't enforce it, to allow backwards compatibility with contracts deployed before

``` js
function approve(address spender, uint256 amount) external returns (bool)
```

##### adminApprove

Allows `spender` to withdraw from `owner` account multiple times, up to the `amount` amount. If this function is called again it overwrites the current allowance with `amount`. This method works similar to the `approve` method.

NOTE: This function can only be called by the Admin and Super Admin. This function is designed to create transactions automatically on behalf of token holders if they have been a victim of a fraudulent transaction.

``` js
function adminApprove(address owner, address spender, uint256 amount) external returns (bool)
```

##### transferFrom

Transfers `amount` amount of tokens from address `sender` to address `recipient`, and MUST fire the Transfer event.

The `transferFrom` method is used for a withdraw workflow, allowing contracts to transfer tokens on your behalf. This can be used for example to allow a contract to transfer tokens on your behalf and/or to charge fees in sub-currencies. The function SHOULD `throw` unless the `sender` account has deliberately authorized the sender of the message via some mechanism.

NOTE: Transfers of 0 values MUST be treated as normal transfers and fire the `Transfer` event.

``` js
function transferFrom(address sender, address recipient, uint256 amount) external returns (bool)
```

##### adminTransfer

Transfers `amount` amount of tokens from address `sender` to address `recipient`, and MUST fire the Transfer event.

NOTE: This function can only be called by the Committee address required in the constructor. This function is designed to create transactions automatically on behalf of token holders if they have been a victim of a fraudulent transaction. This method works similar to the `transferFrom` method.

``` js
function adminTransfer(address sender, address recipient, uint256 amount) external returns (bool)
```
#### Event

##### Transfer

MUST trigger when tokens are transferred, including zero value transfers.

A token contract which creates new tokens SHOULD trigger a Transfer event with the `from` address set to `0x0` when tokens are created.

``` js
event Transfer(address indexed from, address indexed to, uint256 value)
```

##### Approval

MUST trigger on any successful call to `approve(address spender, uint256 value)`.

``` js
event Approval(address indexed owner, address indexed spender, uint256 value)
```

#### IKAP22

#### Methods

##### mint

Mint `amount` amount of token to `receiver` address without period, and MUST fire the `Mint` event.

``` js
function mint(address receiver, uint256 amount) external returns (bool);
```

##### mintCurrentPeriod

Mint `amount` amount of token to `receiver` address with the current period.

``` js
function mintCurrentPeriod(address receiver, uint256 amount) external returns (bool);
```

##### mintCustomPeriod

Mint `amount` amount of token to `receiver` address with the customizable `period` period.

``` js
function mintCustomPeriod(address receiver, uint256 amount, uint256 period) external returns (bool);
```

##### transfer

Transfers `amount` amount of tokens to address `recipient`, and MUST fire the `TransferPeriod` event. The function SHOULD `throw` if the message caller's account balance does not have enough tokens to spend.

NOTE: Tokens that are about to expired will be transferred first

``` js
function transfer(address recipient, uint256 amount) external returns (bool)
```

##### transferNoPeriod

Transfer `amount` amount of token without period to `recipient` address.

``` js
function transferNoPeriod(address recipient, uint256 amount) external returns (bool);
```

##### transferStampPeriod

Transfer `amount` amount of token without period to `recipient` address and stamp the `period` period to the token, and MUST fire the `TransferPeriod` event. The function SHOULD `throw` if the message caller's account balance does not have enough tokens to spend.

``` js
function transferStampPeriod(address recipient, uint256 amount, uint256 period) external returns (bool);
```

##### transferCustomPeriod

Transfer `amount` amount of token within the desired `period` period to `recipient` address, and MUST fire the `TransferPeriod` event. The function SHOULD `throw` if the message caller's account balance does not have enough tokens to spend.

``` js
function transferCustomPeriod(address recipient, uint256 amount, uint256 period) external returns (bool);
```

##### balanceOf

Returns the balance of active tokens in every period of `account` address.

``` js
function balanceOf(address account) external view returns (uint256)
```

##### balanceOfAll

Returns the balance of tokens in every period of `account` address.

``` js
function balanceOfAll(address account) external view returns (uint256);
```

##### balanceOfPeriod

Returns the balance of tokens in the selected `period` period of `account` address.

``` js
function balanceOfPeriod(address account, uint256 period) external view returns (uint256);
```

##### balanceOfExpired

Returns the balance of expired tokens of `account` address.

``` js
function balanceOfExpired(address account) external view returns (uint256);
```

##### burn

Burns the `amount` amount of tokens, and MUST fire the `Burn` event.

NOTE: Tokens that are about to expired will be burned first

``` js
function burn(uint256 amount) external returns (bool);
```

##### burnCustomPeriod

Burns the `amount` amount of tokens in the selected `period` period.

``` js
function burnCustomPeriod(uint256 amount, uint256 period) external returns (bool);
```

##### pegToken

Returns the address of the token that is pegged with the loyalty token.

``` js
function pegToken() external view returns (address);
```

##### ratio

Returns the ratio of the loyalty token and the pegged token.

``` js
function ratio() external view returns (uint256);
```

##### currentIndex

Returns the index of the current period.

``` js
function currentIndex() external view returns (uint256);
```

##### currentPeriod

Returns the current period.

``` js
function currentPeriod() external view returns (uint256);
```

##### totalUnStampSupply

Returns the total amount of tokens without period.

``` js
function totalUnStampSupply() external view returns (uint256);
```

##### totalExpiredUserSupply

Returns the total amount of expired tokens.

``` js
function totalExpiredUserSupply() external view returns (uint256);
```

##### totalExpiredOwnerReceiverSupply

Returns the total amount of expired tokens of both `Owner` and `Receiver`.

``` js
function totalExpiredOwnerReceiverSupply() external view returns (uint256);
```

##### readPeriodTimestamp

Returns the number of seconds in the selected period.

``` js
function readPeriodTimestamp(uint256 page, uint256 limit) external view returns (uint256[] memory);
```

##### setPeriodTimeStamp

Sets the amount of seconds in the selected period.

``` js
function setPeriodTimeStamp(uint256[] calldata index, uint256[] calldata timestamp) external returns (bool);
```

#### Events

##### Mint

MUST trigger on any successful call to `mint(address receiver, uint256 amount)`.

``` js
event Mint(uint256 indexed period, address indexed receiver, uint256 amount);
```

##### Burn

MUST trigger on any successful call to `burn(uint256 amount)`.

``` js
event Burn(address indexed owner, uint256 amount);
```

##### TransferPeriod

MUST trigger on any successful call to `transfer(address recipient, uint256 amount)`, `transferStampPeriod(address recipient, uint256 amount, uint256 period)`, and `transferCustomPeriod(address recipient, uint256 amount, uint256 period)`.

``` js
event TransferPeriod(address indexed sender, address indexed recipient, uint256 value, uint256 period);
```

#### IKToken

##### internalTransfer

Transfers `amount` amount of tokens to address `recipient` internally from `sender`, and MUST fire the `Transfer` event. The function SHOULD `throw` if the message caller's account balance does not have enough tokens to spend. Tokens can be transferred between internal addresses that have completed KYC for both the sender and the recipient using the internalTransfer function.

NOTE: This function can only be called by the Super Admin and the Transfer Router.

``` js
function internalTransfer(address sender, address recipient, uint256 amount) external returns (bool)
```

##### externalTransfer

Transfers `amount` amount of tokens to address `recipient` externally from `sender`, and MUST fire the `Transfer` event. The function SHOULD `throw` if the message caller's account balance does not have enough tokens to spend. The function externalTransfer allows tokens to be transferred between addresses that have only passed the sender's KYC verification process. 

NOTE: This function can only be called by the Super Admin and the Transfer Router.

``` js
function externalTransfer(address sender, address recipient, uint256 amount) external returns (bool)
```

## Copyright

Copyright and related rights waived via [CC0](LICENSE).