# How To Transfer EWT from a Validator Node

{% hint style="warning" %}
#### **Disclaimer: This page documents the use of an unofficial tool; while it is commonly used by validators, it wasn't professionally audited and comes with no guarantees whatsoever. Use the validator tool, Docker image, NPM package, and following guide at your own risk.** <a href="#disclaimer-its-an-unofficial-tool-it-wasnt-professionally-audited-and-comes-with-no-guarantees-whats" id="disclaimer-its-an-unofficial-tool-it-wasnt-professionally-audited-and-comes-with-no-guarantees-whats"></a>
{% endhint %}

## **Prerequisites** <a href="#disclaimer-its-an-unofficial-tool-it-wasnt-professionally-audited-and-comes-with-no-guarantees-whats" id="disclaimer-its-an-unofficial-tool-it-wasnt-professionally-audited-and-comes-with-no-guarantees-whats"></a>

1. Check Docker Image, NPM Package
   1. Docker Image:
      1. [ewf-validator-tool](https://hub.docker.com/r/aznagy/ewf-validator-tool)
      2. [ewf-validator-tool:latest](https://hub.docker.com/layers/aznagy/ewf-validator-tool/latest/images/sha256-66e86c3989d2345f9b231f40a5a327bd824a1b0ea400d4fa5e739e1c4049e96b?context=explore)
   2. Github Repo of [ewf-validator-tool](https://github.com/ngyam/validator-tool)
   3. NPM Package [ewf-validator-tool](https://www.npmjs.com/package/ewf-validator-tool)
2. In the Validator Node - get the path of the following two files -
   1. **keyfile** - `UTC--*`
      1. In Parity/OpenEthereum Validator Node, the path of keyfile is -
         * `$HOME/docker-stack/chain-data/keys/$CHAINNAME/UTC--*` \[CHAINNAME can be `Volta` or `EnergyWeb`]
   2. **secret file** - `.secret`
      1. In Parity/OpenEthereum Validator Node, the path of secret file is -
         * `$HOME/docker-stack/.secret`

## **Execution of** `ewf-validator-tool` **Using Docker** <a href="#execution-of-ewf-validator-tool-using-docker" id="execution-of-ewf-validator-tool-using-docker"></a>

1. Put the the value before execution:
   1. **KEYFILE\_PATH :** path of keyfile in old validator node
   2. **SECRETFILE\_PATH :** path of secret file in old validator node
   3. **NEW\_ADDRESS :** Address of wallet or new node address
   4. **TOKEN\_AMOUNT:** Amount of token to be taken out
   5. **HTTPS\_RPC\_URL :**
      1. Volta HTTPS\_RPC\_URL: `https://volta-rpc.energyweb.org`
      2. EnergyWeb HTTPS\_RPC\_URL: `https://rpc.energyweb.org`
2. Command to transfer token
   1. Before execute take `superuser` privilege - `sudo -s` or run docker with `sudo`

`docker run -it -v "$KEYFILE_PATH":/keyfile -v $SECRETFILE_PATH:/keypass aznagy/ewf-validator-tool:latest transferto $NEW_ADDRESS $TOKEN_AMOUNT -r $HTTPS_RPC_URL`

**Example:**

_Here is an example_

(**It is Nethermind validator node, that’s why the path of keyfile and secret file are different than Parity validator node**)

1. Transfer token from Volta Validator Node to Hardware Wallet -
   1. **KEYFILE\_PATH :** keyfile path of my Validator Node
      * `/home/ubuntu/docker-stack/keystore/UTC--2020-12-21T16-47-06.412446000Z--5125254ec2e024d8226cf4c389512c43802a76a1`
   2. **SECRETFILE\_PATH :** secret file path of my Validator Node
      * `/home/ubuntu/docker-stack/keystore/.secret`
2. **NEW\_ADDRESS :** Address of my wallet `0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35`
3. **TOKEN\_AMOUNT:** `0.01`
4. **HTTPS\_RPC\_URL :** Volta HTTPS\_RPC\_URL: `https://volta-rpc.energyweb.org`

_**Command**_

_**Transfer Token**_

```
docker run -it -v "/home/ubuntu/docker-stack/keystore/UTC--2020-12-21T16-47-06.412446000Z--5125254ec2e024d8226cf4c389512c43802a76a1":/keyfile -v /home/ubuntu/docker-stack/keystore/.secret:/keypass aznagy/ewf-validator-tool:latest transferto 0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35 0.01 -r https://volta-rpc.energyweb.org1
```

_**Output**_

```
Connected to Volta (test network)
Successful transaction!
{
  "blockHash": "0xbca95daf204c80a6c1cf49005128213e0adb0803942ef34fba066f0c5e23f551",
  "blockNumber": 9763320,
  "contractAddress": null,
  "cumulativeGasUsed": 21000,
  "from": "0x5125254Ec2E024D8226cf4c389512c43802a76A1",
  "gasUsed": 21000,
  "logs": [],
  "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "status": true,
  "to": "0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35",
  "transactionHash": "0xef7fd88dff637b5528fd706500f855077eb8e88a29a2a0738e394d1459f56542",
  "transactionIndex": 0
}
```

``

### _**Check in the Explorer**_

1. URL\_Token\_out => \[Address of Old Validator Node] [0x5125254Ec2E024D8226cf4c389512c43802a76A1](https://volta-explorer.energyweb.org/address/0x5125254Ec2E024D8226cf4c389512c43802a76A1/transactions)

![](../../.gitbook/assets/2020-12-24\_12h26\_23.jpg)

1. URL Token\_In => \[Address of wallet] [0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35](https://volta-explorer.energyweb.org/address/0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35/transactions)

![](<../../.gitbook/assets/2020-12-24\_12h26\_14 (2).jpg>)

### _**Check with validator-tool command:**_ `payout check` _**and**_ `payout changeto`

1. `payout check` command

```
docker run -it -v "$KEYFILE_PATH":/keyfile -v $SECRETFILE_PATH:/keypass aznagy/ewf-validator-tool:latest payout check $OLD_NODE_ADDRESS -r $HTTPS_RPC_URL1
```

_**Example**_:

```
docker run -it -v "/home/ubuntu/docker-stack/keystore/UTC--2020-12-21T16-47-06.412446000Z--5125254ec2e024d8226cf4c389512c43802a76a1":/keyfile -v /home/ubuntu/docker-stack/keystore/.secret:/keypass aznagy/ewf-validator-tool:latest payout check 0x5125254Ec2E024D8226cf4c389512c43802a76A1 0.01 -r https://volta-rpc.energyweb.org1
```

_**Output**_:

```
Connected to Volta (test network) 
Successful call! Payout address of 0x5125254Ec2E024D8226cf4c389512c43802a76A1 is: 0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35
```

2\. `payout changeto` command

```
docker run -it -v "$KEYFILE_PATH":/keyfile -v $SECRETFILE_PATH:/keypass aznagy/ewf-validator-tool:latest payout changeto $NEW_ADDRESS -r $HTTPS_RPC_URL
```

_**Example**_:

```
docker run -it -v "/home/ubuntu/docker-stack/keystore/UTC--2020-12-21T16-47-06.412446000Z--5125254ec2e024d8226cf4c389512c43802a76a1":/keyfile -v /home/ubuntu/docker-stack/keystore/.secret:/keypass aznagy/ewf-validator-tool:latest payout changeto 0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35 -r https://volta-rpc.energyweb.org
```

_**Output:**_

```
Connected to Volta (test network)
Change of payout address successful!
{
  "blockHash": "0xef89937584dcc102a3684431a9b46112b617b5d3a4d362e7e9eb4d90e4d6db32",
  "blockNumber": 9763698,
  "contractAddress": null,
  "cumulativeGasUsed": 23494,
  "from": "0x5125254Ec2E024D8226cf4c389512c43802a76A1",
  "gasUsed": 23494,
  "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "status": true,
  "to": "0x1204700000000000000000000000000000000002",
  "transactionHash": "0xd5206399f5a0b6227975720408af216abf4d090abc11e1753885eabfe5e55362",
  "transactionIndex": 0,
  "events": {}
}
```

``

## Run Validator Tool using npm package <a href="#run-validator-tool-using-npm-package" id="run-validator-tool-using-npm-package"></a>

_If you want to execute validator tool on host machine or local machine without using docker, follow the following process._

### **Prerequisite**: <a href="#prerequisite" id="prerequisite"></a>

1. Install node and npm
   * [nodejs v8 or higher ](https://nodejs.org/en/download/)and LTS (recommended)
   * npm comes with nodejs installation.
   * check nodejs and npm version
     * `node -v`
     * `npm -v`
2. Install [ewf-validator-tool](https://www.npmjs.com/package/ewf-validator-tool) NPM Package on machine
   * `npm install -g ewf-validator-tool`
   * Check validator-tool is installed

`validatortool --version 21.0.3`

### **Execution of** `ewf-validator-tool` <a href="#execution-of-ewf-validator-tool" id="execution-of-ewf-validator-tool"></a>

1. From the old (original) Validator Node - get the path or grab the value of the following two files - \[_If you want to run it on your local machine, just to collect the value of_ `keyfile` _and_ `.secret` _file.]_
   1. **keyfile** - `UTC--*`
   2. In Parity/OpenEthereum Validator Node, the path of keyfile is -
      * `$HOME/docker-stack/chain-data/keys/$CHAINNAME/UTC--*` \[CHAINNAME can be `Volta` or `EnergyWeb`]
   3. **secret file** - `.secret`
      1. In Parity/OpenEthereum Validator Node, the path of secret file is -
         * `$HOME/docker-stack/.secret`
   4. **HTTPS\_RPC\_URL :** Volta HTTPS\_RPC\_URL: `https://volta-rpc.energyweb.org`
2. **Command**
   1. **Transfer Token**
      1. You can directly give the path of the `keyfile` and `.secret` file Or
      2. the keyfile value is stored in `UTC-keyfile` and value of `.secret` is stored in `Secretfile`

`validatortool transferto $NEW_ADDRESS -k "$PATH_OF_KEY_FILE" 0.05 -s $PATH_OF_SECRETFILE -r $HTTPS_RPC_URL`

_**Example**_

`validatortool transferto 0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35 -k "$HOME/docker-stack/chain-data/keys/$CHAINNAME/UTC--*" 0.05 -s $HOME/docker-stack/.secret -r https://volta-rpc.energyweb.org`

or

`validatortool transferto 0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35 -k "UTC-keyfile" 0.05 -s Secretfile -r https://volta-rpc.energyweb.org`

b. `payout check` command

`validatortool payout check $OLD_VALIDATOR_NODE -r $HTTPS_RPC_URL`

_**Example**_

`validatortool payout check 0x5125254Ec2E024D8226cf4c389512c43802a76A1 -r https://volta-rpc.energyweb.org`

c. `payout changeto` command

`validatortool payout changeto $NEW_ADDRESS -r $HTTPS_RPC_URL`

_**Example**_

`validatortool payout changeto $0x4933915c40477Db3a9AccA3Fa12DaA8ba5D4fD35 -r https://volta-rpc.energyweb.org`

You should get similar output if you run the validator-tool using docker. To get a glimpse of output, please check the above section.
