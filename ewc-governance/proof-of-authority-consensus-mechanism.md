# Proof-of-Authority Consensus Mechanism

## Blockchain Consensus

In a centralized system, such as a bank or a broker, a designated authority or central operating system would be in charge of adding transactions or information to the system, making sure that each transaction is trustworthy, up to date with the whole system, and does not duplicate previous transactions.

In contrast, public blockchains are decentralized, peer-to-peer systems that have no central authority or oversight like this. Designated actors are responsible for processing transactions, creating new blocks and maintaining the integrity and history of previous blocks.

**The system for determining these actors and how they are selected is called a** [**consensus mechanism**](https://ethereum.org/en/developers/docs/consensus-mechanisms/)**.** These mechanisms determine the process of who can confirm transactions and create new blocks on the blockchain and the protocol for how they do so. Because there is no central oversight, consensus needs to be designed in a way that prevents or disincentivizes malicious or uninformed actors from corrupting the integrity of the chain.&#x20;

There are many consensus algorithms. You may have heard of some widely used ones like [Proof-of-Work](https://ethereum.org/en/developers/docs/consensus-mechanisms/#proof-of-work) or [Proof-of-Stake](https://ethereum.org/en/developers/docs/consensus-mechanisms/#proof-of-stake'). Each mechanism has its own way of determining who is eligible to process transactions and create new blocks, and how how actors are selected to do so.

**The Energy Web Chain uses the Proof-of-Authority (PoA) consensus mechanism.**&#x20;

&#x20;All consensus mechanisms have disadvantages and advantages and are chosen based on the purpose and use case of the blockchain it will be serving.[ You can read more about why Energy Web employs the Proof-of-Authority mechanisms below.](broken-reference)

## [Proof-of-Authority Consensus](https://www.poa.network/for-users/whitepaper/poadao-v1/proof-of-authority)

The Proof-of-Authority (PoA) consensus mechanism has a defined set of actors that validate transactions and propagate new blocks to the chain. Rather than competing or staking for a chance to add blocks, they take turns creating new blocks in a round-robin style. These actors are called validators.&#x20;

Energy Web validators participate by [running full nodes](broken-reference) of the blockchain using [OpenEthereum client software](https://openethereum.github.io/). Smart contracts called Validator-Set contracts have the functionality to add or remove validators. **Anyone can run a full node of the blockchain, but only addresses that are included in the Validator-Set contracts can validate transactions and seal blocks.** You can read about the Energy Web Chain's Validator Set Contracts [here](broken-reference).&#x20;

The Energy Web Chain uses a specific type of PoA called [Authority Roundtable (AuRa)](https://www.poa.network/for-users/whitepaper/poadao-v1/proof-of-authority).  The AuRa Proof-of-Authority consensus mechanism can be used by blockchains that run the OpenEthereum client. &#x20;

{% hint style="info" %}
For more in-depth information on Proof-of-Authority, read the [Authority Roundtable Proof-of-Authority white paper](https://www.poa.network/for-users/whitepaper/poadao-v1/proof-of-authority)
{% endhint %}

### Proof-of-Authority Process

At a high level, the PoA mechanism works as follows:

1. All validator nodes maintain a complete list of the validators, identified by public keys. This list changes as validators are added or removed. In addition to storing the current and historical state of the network, all validators maintain essential information about the network (such as synchronized timing information and current data processing limits).
2. For a defined time window, one validator is assigned as the primary validator via the PoA algorithm. During this time, they are responsible for collecting the broadcasted transactions and proposing the new block. Only one validator is designated as primary at a time–based on a calculation derived from the timestamp on synchronized clocks among the validator nodes in the network and the number of validators–in order to prevent validators from arbitrarily creating blocks at irregular intervals.
3. If a validator fails to create a block when it is selected (e.g., because of hardware problems on the side of the validator) or its block fails to be validated by the pool of nodes (e.g., because of network connectivity problems), the next validator proceeds to create a block with whatever transactions haven’t been processed.
4. The remaining validator nodes verify that the transactions in each block are legitimate for that time window, sign the block with their private keys, and propagate the signed block to the network.
5. Once a simple majority of validators have authored a block on top of a given signed block, finality is achieved for that given block, and the block is confirmed by the network and added to the chain.

## Additional Resources

* [AuRa Proof-of-Authority white paper](https://www.poa.network/for-users/whitepaper/poadao-v1/proof-of-authority)
* [“What is "proof of work" and "proof of stake"? On CoinBase](https://www.coinbase.com/tr/learn/crypto-basics/what-is-proof-of-work-or-proof-of-stake?utm\_source=google\_search\_nb\&utm\_medium=cpc\&utm\_campaign=9943088770\&utm\_content=100067298945\&utm\_term=\&utm\_creative=523125652224\&cb\_device=c\&cb\_placement=\&cb\_country=us\&cb\_city=open\&cb\_language=en\_us\&gclid=CjwKCAjwr56IBhAvEiwA1fuqGq9QAo4c30d8AZHEcgwZLd6wOoNPEtKLqet\_K4f-X\_PXq5l7bmBVqBoCXSEQAvD\_BwE)
* [“Blockchain Consensus: A Simple Explanation Anyone Can Understand” on Blockgeeks](https://blockgeeks.com/guides/blockchain-consensus/)
