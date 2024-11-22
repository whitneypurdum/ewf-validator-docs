# EWC Validator Node Operational Functions

EWC validator nodes can:

* Establish consensus about the state of the network by verifying the work / behavior of other validator nodes;
* Reject blocks / transactions that violate input/output protocols defined by AuRa and the EVM state transition function;&#x20;
* Implement permissioning functions as described [here](https://openethereum.github.io/Permissioning) (note: permissoining functions can only be implemented via a majority governance decision).&#x20;

EWC validator nodes CANNOT:

* Inspect or approve the contents of individual transactions;
* Unilaterally verify transactions (any given transaction is only finalized after n/2 blocks, with n=total validators);
* Associate identities with on-chain accounts;
* Unilaterally modify account permissions, network topology, or network state.
