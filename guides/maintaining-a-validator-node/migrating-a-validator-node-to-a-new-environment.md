# Migrating a validator node to a new environment

Sometimes an organization needs to migrate their validator node into a new environment. Common reasons for this include:

* Changing infrastructure providers (e.g. switching cloud or on-premise vendors)
* Wanting to upgrade host environment configuration
* Rotating access due to security procedures or policies.&#x20;

If you are currently operating a validator node on Volta of the EW Chain and need to migrate it from its existing host environment to a new one, there are two options:

## **Install a new node and retire the existing one**&#x20;

* This option requires [provisioning a new host environment and following the installation procedures to establish an entirely new node](../installing-a-validator-node/) (note: this will result in a new address, private key, EWT balance, etc.). Once your new node is installed, the current one will be removed from the network and you will be able to retire / deprecate the legacy node and host environment.&#x20;
* The benefits of this approach are:
  * It is easy to replicate the node installation process, so the overall migration is simpler;&#x20;
  * You don't have to worry about independently modifying the installation script;&#x20;
  * You can maintain continuity by simultaneously retiring the original node and adding the new one to the network;&#x20;
* The drawbacks of this approach are:
  * You must determine a secure way to maintain access to the legacy block rewards held on the original node address;&#x20;
  * Depending on your organization's IT policies and procedures, it may be more complex and costly to procure multiple host environments during the migration.&#x20;
  * You may need to replicate or modify  access management policies and procedures for the new environment.&#x20;

{% hint style="warning" %}
If you elect to install new node, make sure you transfer any EWT held in the original node address to a separate wallet that you can continue to access going forward, and/or maintain the private key to the original node to access old block reward balances.&#x20;
{% endhint %}



## **Migrate your existing node to a new environment** &#x20;



* This option involves migrating the existing node (i.e. maintaining the same address and private key) to a new host environment. To do this, you must extract the private key from the existing environment and then re-run a modified installation script in the new environment, using the private key of the validator node.&#x20;
* The benefits of this approach are:
  * You maintain continuity by keeping the same address and private key;&#x20;
  * You don't need to operate two validator nodes (and thus host environments) simultaneously.&#x20;
* The drawbacks of this approach are:
  * Depending on the parameters of the existing vs. new environment, you may need to modify configurations and access management.&#x20;
  * You must securely extract the private key from the existing node, temporarily store it, and import it into the new environment.&#x20;
  * You will experience a period of "downtime" throughout the migration, during which your organization's validator node will not be operational.&#x20;

Follow the steps to migrate existing nodes to new node:

1. Collect and store the following necessary info from original (existing) Instance -
   * You can stop containers in old instance. `docker-compose down`
   * Value of `Validator Address`, `InfluxDB Username`, `InfluxDB Password` . You’ll find this info in `install-summary.txt` file.
   * Value of `docker-stack/.secret`
   * `docker-stack/chain-data/keys/$CHAINNAME/UTC--*` \[CHAINNAME can be `Volta` or `EnergyWeb`]
   * \[optional] keep a backup of `docker-stack/` dir.
2. Prepare a new host environment as described in the installation instructions, and access the appropriate installation script to install a node in the new environment.&#x20;
3. Comment out  lines 170-213 (all the lines related to creating accounts / keys) from the script
   1. Comment out or delete everything from `echo "Creating Account..."` \[line 170] **till** `docker rm -f parity-keygen` \[line 213]
      * [Volta validator installation script](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate/openethereum)
      * [EWC validator installation script](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate/openethereum)
4. Then run the modified script in the new instance -
   1.  You can see in the screen of this message along with other logs - This is normal as we commented out keys line.

       `Creating Account... ls: cannot access './chain-data/keys/Volta/': No such file or directory`

       &#x20;
5. The End Result would be the the following . `Validator Address`, `Enode`, `InfluxDB Username` and `InfluxDB Password` field would be empty

```
==== EWF Affiliate Node Install Summary ====
Company: Company_Name
Validator Address: 
Enode: 
IP Address: New_IP_ADDESSS
InfluxDB Username: 
InfluxDB Password: 
```

6\. In the new Instance, There is the `docker-stack/` dir. Enter to the directory and run `docker-compose ps`\
You will get this. The containers are not up, it will remain `Restarting` state

```
	             Name                            Command                 State      Ports
-------------------------------------------------------------------------------------
docker-stack_parity-telemetry_1   docker-entrypoint.sh node  ...   Restarting        
docker-stack_parity_1             /bin/parity --config /pari ...   Restarting      
```

* run the command to stop container `docker-compose down`

&#x20;

1. The `.secret` file in `docker-stack/` dir needs to be updated with the older one (from the original node).&#x20;

{% hint style="info" %}
The`.secret` file is in only `readonly` mode. Change mode before updating with old value. `chmod 644 .secret`&#x20;
{% endhint %}



1. The `.env` file in `docker-stack/` dir needs to be updated.
   1. Update the `VALIDATOR_ADDRESS=` field with old value (from the original node).
   2. Update the `PARITY_KEY_FILE=./chain-data/keys/Volta/UTC--*` with correct name.
2. In the `docker-stack/config/parity-signing.toml`, the following 1 value need to be updated. In the new instance, this value would be empty. Update the value with old `Validator Address`
   * `engine_signer = "0x...."`
3. In the new Instance, `docker-stack/chain-data/` directory is there. We need to create `keys/$CHAINNAME` directory. CHAINNAME can be `Volta` or `EWC`, depending on which chain you are running. Here is an example of `Volta` chain
   * `mkdir -p docker-stack/chain-data/keys/Volta/` \[CHAINNAME = Volta]
   * Copy the `UTC--*` file from old instance to `docker-stack/chain-data/keys/Volta/` dir or create that file in `docker-stack/chain-data/keys/Volta/` dir with exact same name and same value.
   * \[Optional] If you want exact sync of database, you can copy db files from the old instance to the new instance -
     * DB Path - `docker-stack/chain-data/chains/Volta/db/`
   * Run `docker-compose up -d`
   * Check logs of parity container -
     * `docker-compose logs -f --tail 100 parity`
     * `docker-compose logs -f --tail 100 parity_telemetry`
