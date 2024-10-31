# Changing the Validator Config File

To change parameters of the validator client you have to change the config file of your validator node.

In the host, make sure you have root access and go into the config folder

| <pre><code>sudo -s 
cd docker-stack/config
</code></pre> |
| -------------------------------------------------------- |

Now you can edit the parity-signing.toml file that should look similar to this:

```
[parity]
chain = "/parity/config/chainspec.json"
no_persistent_txqueue = true

[rpc]
disable = false
port = 8545
interface = "0.0.0.0"
cors = []
apis = ["eth", "net", "parity", "web3"]

[websockets]
disable = false
interface = "0.0.0.0"
port = 8546

[ipc]
disable = true

[secretstore]
disable = true

[network]
port = 30303
min_peers = 25
max_peers = 50
discovery = true
warp = false
allow_ips = "all"
snapshot_peers = 0
max_pending_peers = 64

[footprint]
db_compaction = "ssd"

[snapshots]
enable = false

[mining]
force_sealing = true
usd_per_tx = "0.000000000000000001"
usd_per_eth = "1"
price_update_period = "hourly"
min_gas_price = 1
gas_cap = "4000000"
gas_floor_target = "4000000"
tx_gas_limit = "4000000"
extra_data = "validator-XXX"
engine_signer = "0xXXX"

[account]
password = ["XXX"]
keys_iterations = XXX
```

Most parameters should not be changed. But there are several parameters that can be adapted.

### Warp Sync <a href="#changingthevalidatorconfigfile-minimumgas-price" id="changingthevalidatorconfigfile-minimumgas-price"></a>

If your node is having trouble syncing after a client update, restarting the node, or an unplanned outage, you can speed up the syncing process by enabling warp sync:

* Under \[network] change: `warp = true`
* Restart docker container: `docker-compose up -d`

For more information, see [https://openethereum.github.io/Warp-Sync](https://openethereum.github.io/Warp-Sync)

### Minimum Gas-Price <a href="#changingthevalidatorconfigfile-minimumgas-price" id="changingthevalidatorconfigfile-minimumgas-price"></a>

The minimum gas price defines the lowest price that you allow to be paid for a transaction in Wei/Gas to still be included into a block by your validator node. Every transaction that has a gas price below that will be ignored. What price to set should depend largely on the transaction volume at the current moment. Every validator can choose this parameter individually. If it is too low, there is little spam protection and spammers can just fill up the blocks for little cost. If it is too high, it unjustifiably increases the price per transaction and might deter usage.

**usd\_per\_tx** defines the amount of USD to be paid for a basic transaction of sending tokens. The minimum gas price is set accordingly.

**usd\_per\_eth** defines the USD value of one token.

**price\_update\_period** defines the time that is allowed to pass between each gas price update. T may be daily, hourly, a number of seconds, or a time string of the form "2 days", "30 minutes" etc.

**min\_gas\_price** defines the minimum gas price in Wei/Gas and overrides usd\_per\_tx.

### Block Gas Limit <a href="#changingthevalidatorconfigfile-blockgaslimit" id="changingthevalidatorconfigfile-blockgaslimit"></a>

Validators can choose the size of the blocks and thereby the number of transactions to include in a block. The bigger the blocks, the higher the transaction throughput. But if the block is too big, executing all transactions in that block might create problems with latency. Therefore the EWF will advise on a target blockgas limit. Once the limit is changed in the config file it will slowly increase until it has reached the defined limit. If validators do not agree on a limit, it will increase and decrease depending on who proposed the block.

**gas\_cap** defines the absolute maximum amount of gas that will be allowed in a block depending on the transaction volume.

**gas\_floor\_target** defines the block size that the validator node targets when creating a new block.

**tx\_gas\_limit** defines the maximum gas amount that is allowed for a single transaction.

\


You can read about all possible configurations here: [https://openethereum.github.io/Configuring-OpenEthereum.html](https://openethereum.github.io/Configuring-OpenEthereum.html)



To restart the validator node, run

| <pre><code>docker-compose restart parity
</code></pre> |
| ------------------------------------------------------ |

The parity client should now be running with the new configurations.
