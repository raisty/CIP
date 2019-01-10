---
cip: 2
title: CRC-2 Token Standard
author: Rastislav Vasicka <rastislav@corecoin.cc>, Dexaran <dexaran@ethereumclassic.org>
type: Standards Track
category: CRC
status: Draft
created: 2019-01-10
---

## Simple Summary

A secured interface for tokens.

## Abstract

The following describes standard functions a token contract and contract working with specified token can implement to prevent accidentally sends of tokens to contracts and make token transactions behave like core transactions.

## Motivation

CRC1 token standard is leading to money losses for end users. The main problem is lack of possibility to handle incoming CRC1 transactions, that were performed via `transfer` function of CRC1 token.
If you send 100 XCE to a contract that is not intended to work with Core platform, then it will reject a transaction and nothing bad will happen. If you will send 100 CRC1 tokens to a contract that is not intended to work with CRC1 tokens, then it will not reject tokens because it cant recognize an incoming transaction. As the result, your tokens will get stuck at the contracts balance.

Another disadvantages of CRC1 that CRC2 will solve:
1. Lack of `transfer` handling possibility.
2. Loss of tokens.
3. Token-transactions should match Core ideology of uniformity. When a user wants to transfer tokens, he should always call `transfer`. It doesn't matter if the user is depositing to a contract or sending to an externally owned account.

Those will allow contracts to handle incoming token transactions and prevent accidentally sent tokens from being accepted by contracts (and stuck at contract's balance).

For example decentralized exchange will no more need to require users to call `approve` then call `deposit` (which is internally calling `transferFrom` to withdraw approved tokens). Token transaction will automatically be handled at the exchange contract.

## Specification

## Token
### Methods

**NOTES**:
An important point is that contract developers must implement `tokenFallback` if they want their contracts to work with the specified tokens.
If the receiver does not implement the `tokenFallback` function, consider the contract is not designed to work with tokens, then the transaction must fail and no tokens will be transferred. An analogy with a Core transaction that is failing when trying to send Core to a contract that did not implement `function() payable`.

#### totalSupply
```js
function totalSupply() constant returns (uint256 totalSupply)
```

Get the total token supply

#### name
```js
function name() constant returns (string _name)
```

Get the name of token

#### symbol
```js
function symbol() constant returns (bytes32 _symbol)
```

Get the symbol of token

#### decimals
```js
function decimals() constant returns (uint8 _decimals)
```

Get decimals of token

#### balanceOf
```js
function balanceOf(address _owner) constant returns (uint256 balance)
```

Get the account balance of another account with address `_owner`

#### transfer(address, uint)
```js
function transfer(address _to, uint _value) returns (bool)
```

Needed due to backwards compatibility reasons because of CRC1 transfer function doesn't have `bytes` parameter. This function must transfer tokens and invoke the function `tokenFallback(address, uint256, bytes)` in `_to`, if `_to` is a contract. If the `tokenFallback` function is not implemented in ` _to` (receiver contract), then the transaction must fail and the transfer of tokens should not occur.

#### transfer(address, uint, bytes)
```js
function transfer(address _to, uint _value, bytes _data) returns (bool)
```

function that is always called when someone wants to transfer tokens.
This function must transfer tokens and invoke the function `tokenFallback (address, uint256, bytes)` in `_to`, if `_to` is a contract. If the `tokenFallback` function is not implemented in ` _to` (receiver contract), then the transaction must fail and the transfer of tokens should not occur.
If `_to` is an externally owned address, then the transaction must be sent without trying to execute ` tokenFallback` in `_to`.
`_data` can be attached to this token transaction and it will stay in blockchain forever (requires more gas). `_data` can be empty.

NOTE: The recommended way to check whether the `_to` is a contract or an address is to assemble the code of ` _to`. If there is no code in `_to`, then this is an externally owned address, otherwise it's a contract.

### Events

#### Transfer
```js
event Transfer(address indexed _from, address indexed _to, uint256 indexed _value, bytes _data)
```

Triggered when tokens are transferred.

## Contract to work with tokens
```js
function tokenFallback(address _from, uint _value, bytes _data)
```

A function for handling token transfers, which is called from the token contract, when a token holder sends tokens. `_from` is the address of the sender of the token,` _value` is the amount of incoming tokens, and `_data` is attached data similar to `msg.data` of Core transactions. It works by analogy with the fallback function of Core transactions and returns nothing.

NOTE: `msg.sender` will be a token-contract inside the `tokenFallback` function. It may be important to filter which tokens are sent (by token-contract address). The token sender (the person who initiated the token transaction) will be `_from` inside the` tokenFallback` function.

IMPORTANT: This function must be named `tokenFallback` and take parameters` address`, `uint256`,` bytes` to match the function signature.

## Implementation

CRC2 tokens are backwards compatible with CRC1 tokens.

#### Example implementations is available at
- [CRC2 implementation](https://github.com/raisty/Core-CRC2/tree/master/CRC2)

## History

Historical links related to this standard:

- [Reddit discussion](https://coretalk.info/t/crc-2-token-standard/39)
- [Original Issue #2](https://github.com/core-coin/CIP/issues/2)

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
