---
description: >-
  This page provides troubleshooting tips if your validator node is not
  connecting to peers.
---

# Problems connecting to peers

### Wait a little bit longer <a href="#wait-a-little-bit-longer" id="wait-a-little-bit-longer"></a>

If you are not connected to any peers right away, often it can help to just wait a little longer and give the node a little time to connect to other peers. If the node is still not connected after a couple of minutes, there is probably a problem.

### Sync your local time <a href="#sync-your-local-time" id="sync-your-local-time"></a>

If you have trouble connecting to peers you should first check if the local time on your device is exact. Go to [http://time.is/](http://time.is/) and ensure it says: “Your time is exact”. If your time is not exact, go to System Preferences and make sure it is synchronized.

To make sure that your clock is always synchronized you can also use the ntp-pool-project, a big virtual cluster of timeservers providing reliable easy to use NTP service for millions of clients: [http://www.pool.ntp.org/en/](http://www.pool.ntp.org/en/)

Basic instructions on how to set up ntp-pool can be found here: [http://www.pool.ntp.org/en/use.html](http://www.pool.ntp.org/en/use.html)

More detailed instructions for different operating systems can be found here:

Mac: [https://www.macworld.com/article/1140509/timeservers.html](https://www.macworld.com/article/1140509/timeservers.html)

Linux: [https://www.digitalocean.com/community/tutorials/how-to-configure-ntp-for-use-in-the-ntp-pool-project-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-configure-ntp-for-use-in-the-ntp-pool-project-on-ubuntu-16-04)

Windows: [http://www.satsignal.eu/ntp/setup.html](http://www.satsignal.eu/ntp/setup.html)

### Delete nodes.json <a href="#delete-nodes.json" id="delete-nodes.json"></a>

If your node cannot connect to other peers, it might help to remove your nodes.json file to reestablish a connection. You can find the nodes.js file at the same directory where you store your keys under chain/Volta/network. If you don't know where that is, you can look at the path specified at "Keys Path" when you start the client in the terminal.

Usually it sits at:&#x20;

`$HOME/Library/Application\ Support/io.parity.ethereum/chains/ewc/network/nodes.json`

or

`$HOME/.local/share/io.parity.ethereum/chains/ewc/network/nodes.json`

or

`$HOME\AppData\Local\Parity\Ethereum\chains\ewc\network\nodes.json`

Make sure the client is not running. Delete the file and than restart the client. A new nodes.js file will be created and you will hopefully connect to peers again.

### Manually add peers when starting the client <a href="#manually-add-peers-when-starting-the-client" id="manually-add-peers-when-starting-the-client"></a>

First download this file that contains the enodes of our new bootnodes here: [Volta\_bootnodes.txt](https://energyweb.atlassian.net/wiki/download/attachments/530808833/Volta\_bootnodes.txt?version=1\&modificationDate=1557236943684\&cacheVersion=1\&api=v2) . Afterwards you can start the client with the reserved-peers flag like this:

| `parity --chain CHAIN_NAME --reserved-peers PATH/TO/bootnodes.txt 1. parity --chain volta --reserved-peers PATH/TO/bootnodes.txt 2. parity --chain energywebchain --reserved-peers PATH/TO/bootnodes.txt` |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

_**Or follow the below steps (recommended)**_

1. Download the [Volta\_bootnodes.txt](https://energyweb.atlassian.net/wiki/download/attachments/530808833/Volta\_bootnodes.txt?version=1\&modificationDate=1557236943684\&cacheVersion=1\&api=v2) file in the node instance and save it in `$(pwd)/docker-stack/config/` directory
2. Edit the `parity-signing.toml & parity-non-signing.toml` file
   1. Add the following line in `[network]` section
   2. `reserved_peers = "/parity/config/bootnodes"`
   3. Recreate the containers. `docker-compose up -d --force-recreate`

### Manually add peers <a href="#manually-add-peers" id="manually-add-peers"></a>

If you are not able to find any peers or you want to connect to a specific peer you can add peers manually.

Make sure that the parity API's are enabled by starting the client with the flag

| `--jsonrpc-apis parity,parity_set` |
| ---------------------------------- |

To manually add a peer open your terminal and use the parity\_addReservedPeer function. This adds the peer to the list of peers your node is trying to connect to (more info [here](https://openethereum.github.io/JSONRPC-parity\_set-module.html#parity\_addreservedpeer)):

| `curl --data '{"method":"parity_addReservedPeer","params":["COPY PEER ID HERE"],"id":1,"jsonrpc":"2.0"}'` `-H "Content-Type: application/json"` `-X POST localhost:8545` |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

The Peer ID that you need for this function are called enodes and have this format (this is one of our bootnodes, it should already be on your nodes list by default): enode://59c9250cb805409e84c9cd0038e97d8e5e4605b928663675869ebdfd4c251d80ccad76267a5eb2f4362ddceb5ec671f7595463adfc0a12e9f68dbf233072db41@54.70.158.106:30303

To get information about your peers you can use the parity\_netPeers function (more info [here](https://openethereum.github.io/JSONRPC-parity-module.html#parity\_netpeers)):

| `curl --data '{"method":"parity_netPeers","params":[],"id":1,"jsonrpc":"2.0"}'` `-H "Content-Type: application/json"` `-X POST localhost:8545` |
| ---------------------------------------------------------------------------------------------------------------------------------------------- |

The output will not be very easily readable, use this website to format it into something you can read: [https://jsonformatter.curiousconcept.com/](https://jsonformatter.curiousconcept.com/)

At the very top it will give you the number oft active, connected and max peers. Active means, they are actively synchronizing the chain, a `0` basically means you are already fully synchronized or have no peers at all. Connected are all peers, which you are listening to for new blocks and transactions, ideally this should not be `0`. Max is just the maximum number of peers you can connect to.

Below that you will see a list of peers your node is trying to connect to. Peers with non-empty protocols have completed handshake and are currently connected to you. You can find them quickly by searching for "difficulty" or "head".

### Allow UDP traffic <a href="#allow-udp-traffic" id="allow-udp-traffic"></a>

If all this still does not resolve the problem, you should check if there is some firewall in place that causes the problem and make sure your network does not block UDP traffic.

### Report Problem <a href="#report-problem" id="report-problem"></a>

Of course there is always the possibility that there is a problem with your version of the client. Make sure that you are using the newest version. If the problem persists, open an issue in the parity github and report the problem, as there is probably something wrong with the client: [![](https://github.com/fluidicon.png)GitHub - openethereum/parity-ethereum: The fast, light, and robust client for Ethereum-like networks.](https://github.com/paritytech/parity)
