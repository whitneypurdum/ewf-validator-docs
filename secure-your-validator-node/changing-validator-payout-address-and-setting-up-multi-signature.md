---
description: >-
  To mitigate any kind of risks, it is also important to secure the validator
  node address using techniques such as changing the payout address and
  implementing a multi-signature contract.
---

# Changing validator payout address and setting up multi-signature

**Payout address:**&#x20;

A payout address, also known as a reward address, is the Ethereum address where a validator node receives its rewards for validating transactions and participating in consensus in the network.

The benefit of changing the payout address for a validator node is to allow the operator to receive rewards at a different address. This can be useful for several reasons, such as:

* Better fund management: Node operators can choose to receive rewards at a different address for better management of their funds.
* Security: Node operators can reduce the risk of losing funds in case the original address is compromised.
* Privacy: Node operators can choose to receive rewards at a different address to maintain privacy and separate their reward earnings from their other transactions.

> _Changing the payout address does not affect the node's ability to validate transactions and participate in consensus, but it will change the destination of the rewards received for participating in the network._

**Change Validator Payout address**

* See the instruction here - [<img src="https://1628739436-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FYWg48ihcKhfciND26AxD%2Ficon%2Fcg9m4Zr6SwZzX9Tnub4C%2FEWT_token.png?alt=media&#x26;token=aafb68e3-eaa6-4443-95a7-ba587979ba03" alt="" data-size="line">How To Transfer EWT from a Validator Node](https://energy-web-foundation.gitbook.io/ewc-validator-documentation/guides/maintaining-a-validator-node/how-to-transfer-ewt-from-a-validator-node)

> _**EWF recommend that all validators set a separate payout address so that block rewards are issued to another secure wallet (preferably a multi-signature one) instead of the node address itself.**_
>
> _**If validator members would like to receive block rewards in an address separate from the validator node, please see**_ [_**instructions for calling the setPayoutAddress function in the Reward Contract for further**_](https://energyweb.atlassian.net/wiki/spaces/EWF/pages/701923337) _**details.**_
>
> _**Please note that it is not possible to reallocate transaction fees to a separate account, so all validator nodes will accrue and maintain a small balance of EWT from transaction fees. Based on historical data, total transaction fee balances are expected to be <1 EWT per month.**_

**Multi-signature contract**

A multi-signature contract or multisig contract, is a type of smart contract in the Ethereum network that requires multiple signatures or approvals before certain actions like transferring funds can be taken.

There are several ways to create a multisig contract. One of the example is using Gnosis Safe.

* Create Multi Signature contract address using Gnosis Safe
  * [Gnosis Safe Tutorial | Multisig Wallet for DeFi](https://www.youtube.com/watch?v=GHyxe32Z814)
  * [Creating a Safe on a Web browser.](https://help.gnosis-safe.io/en/articles/3876461-creating-a-safe-on-a-web-browser)

The benefit of using a multi-signature contract for a payout address is that it adds an additional layer of security and control to the management of the rewards. With a multi-sig contract, multiple individuals or entities must be involved in the decision to transfer the rewards, which helps reduce the risk of theft or unauthorized access.

Validator members can have cold storage wallet like hardware wallet, paper wallet for the changed payout address.
