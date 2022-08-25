# Updating the Client

_**Note: As of October 27, 2021, all EWC nodes should run a London-compatible client: OpenEthereum (**_[_**v3.3.0-rc.11**_](https://github.com/openethereum/openethereum/releases/tag/v3.3.0-rc.11) _**or later) or Nethermind (**_[_**v1.11.3**_](https://github.com/NethermindEth/nethermind/releases) _**or later)**_\
\


| **What** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Purpose  | <p>Documentation to update Validator Node client in preparation for London Upgrade:</p><ul><li>For nodes running OpenEthereum client(v3.2.5) or earlier, the update is to OpenEthereum (<a href="https://github.com/openethereum/openethereum/releases/tag/v3.3.0-rc.11">v3.3.0-rc.11</a>) or later version</li><li>For nodes running Nethermind client (v1.10.72) or earlier, the update is to Nethermind (<a href="https://github.com/NethermindEth/nethermind/releases">v1.11.3</a>)</li></ul> |
|          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### The update schedule <a href="#the-update-schedule" id="the-update-schedule"></a>

OpenEthereum and Nethermind clients compatible with AuRa are released in a regular rhythm. The process for implementing regular updates is described below. Emergency updates (i.e. in the event of a known security vulnerability with a specific client version) will be accelerated.

All EWC client updates are tested by the Energy Web Chain Technical Committee to ensure compatibility with the EW Chain AuRa consensus mechanism. **The Technical Committee strongly recommends validators and other node (e.g. RPC) operators refrain from updating their clients until compatibility with the current version is confirmed on this page.** Once an update is tested, the Technical Committee will communicate to validators and the broader community via Slack and Telegram that it is safe to install the new version; this page will also be updated regularly. For security/stability reasons, we recommend rolling out the update in waves, first on Volta and then the production EW Chain.

## Updating the client <a href="#updating-the-client" id="updating-the-client"></a>

{% hint style="info" %}
Good to know! Client updates don’t change any of the following:

* Node Address
* Node key
* Private key
* Secret
{% endhint %}

{% hint style="warning" %}
Before applying the upgrade, ensure the validator node instance has the [following requirements](../installing-a-validator-node/host-machine-requirements.md):
{% endhint %}

| **CPU**                                  | **Memory(GiB)**                           | **Network Capacity(GiB)**                             | **Storage(GB) and Type** |
| ---------------------------------------- | ----------------------------------------- | ----------------------------------------------------- | ------------------------ |
| <p>4 (Minimum)</p><p>8 (Recommended)</p> | <p>8 (Minimum)</p><p>16 (Recommended)</p> | <p>Up to 5 (Minimum)</p><p>Up to 10 (Recommended)</p> | Minimum 300, SSD         |



### Manual Upgrade <a href="#manual-upgrade" id="manual-upgrade"></a>

_**As the upgrade to OpenEthereum**_ _**v3.3.0-rc.11 does not involve any config changes or require db resync, it should be relatively simple.**_

#### **1. Download and verify the new image:**  <a href="#1.-download-and-verify-the-new-image-hardbreak" id="1.-download-and-verify-the-new-image-hardbreak"></a>

Download the node software (Openethereum v3.3.0-rc.11 or later)

`docker pull openethereum/openethereum:v3.3.0-rc.11`

\
Verify the downloaded software to make sure no one has changed something during data transfer

`docker image inspect openethereum/openethereum:v3.3.0-rc.11 | jq -r '.[0].Id'`

The result should be:

`sha256:58ef9c2b1c475fe875fed8d291978bbaac6b19951aa9e8a4686342bbed086fab`

\
If that's the case, proceed to the next step. If not, repeat the process above to download and verify the new image.&#x20;

#### **2. Make a backups & update image version** <a href="#2.-make-a-backups-and-update-image-version" id="2.-make-a-backups-and-update-image-version"></a>

* Stop the containers:

```
cd $HOME/docker-stack
docker-compose stop
```

* Make a backup of docker-compose.yml:

`cp $HOME/docker-stack/docker-compose.yml $HOME/docker-stack/docker-compose.yml_backup`

* Make a backup of .env file:

`cp $HOME/docker-stack/.env $HOME/docker-stack/.env_backup`\


* Make a backup of DB \[Optional]:

{% hint style="danger" %}
**change the text $CHAIN\_NAME** to`Volta` or `EnergyWebChain`
{% endhint %}

`cp -r chain-data/chains/$CHAIN_NAME/ ./$CHAIN_NAME_backup`

* Modify and save .env file (lines 3 & 9):

{% hint style="danger" %}
**DO NOT** override other existing variables!
{% endhint %}

`vim $HOME/docker-stack/.env`

| **new .env** |
| ------------ |

```
VALIDATOR_ADDRESS=$YOUR_VALIDATOR_ADDRESS
EXTERNAL_IP=$YOUR_VALIDATOR_IP_ADDRESS
PARITY_VERSION=openethereum/openethereum:v3.3.0-rc.11
PARITYTELEMETRY_VERSION=1.1.0
IS_SIGNING=signing
PARITY_KEY_FILE=./chain-data/keys/EnergyWebChain/UTC--XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
CHAINSPEC_CHKSUM=
CHAINSPEC_URL=https://example.com
PARITY_CHKSUM=sha256:58ef9c2b1c475fe875fed8d291978bbaac6b19951aa9e8a4686342bbed086fab
```

\
Modify and save docker-compose.yml file (line no.4):

`vi $HOME/docker-stack/docker-compose.yml`

#### New docker-compose.yml

```
version: '2.0'
services:
  parity:
    image: openethereum/openethereum:v3.3.0-rc.11
    restart: always
    command:
      --config /parity/config/parity-signing.toml
      --nat extip:${EXTERNAL_IP}
    volumes:
      - ./config:/parity/config:ro
      - ./chain-data:/home/openethereum/.local/share/io.parity.ethereum/
      - ./.secret:/parity/authority.pwd:ro
    ports:
      - 30303:30303 
      - 30303:30303/udp
      - 127.0.0.1:8545:8545

  parity-telemetry:
    image: energyweb/parity-telemetry:1.1.0
    restart: always
    environment:
      - WSURL=ws://parity:8546
      - HTTPURL=http://parity:8545
      - PIPENAME=/var/spool/parity.sock
    volumes:
      - /var/spool/parity.sock:/var/spool/parity.sock
```

#### Restart the containers

```
cd $HOME/docker-stack
docker-compose up -d --force-recreate
```

#### Check whether the node is running & syncing

```
cd $HOME/docker-stack

# Check openetherereum logs
docker-compose logs -f --tail 100 parity

# Check telemetry logs
docker-compose logs -f --tail 100 parity-telemetry

```
