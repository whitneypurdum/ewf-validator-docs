# Checking node status & logs



### **Check the block explorers!** <a href="#check-the-block-explorers" id="check-the-block-explorers"></a>

The block explorers allow you to search the specific addresses of your Volta and EWC nodes to see how recently they validated a block.

* [https://explorer.energyweb.org/](https://explorer.energyweb.org/)
* [http://volta-explorer.energyweb.org/](http://volta-explorer.energyweb.org/)

Once you’ve searched for your address in the block explorers (make sure to search for your EWC address in the EWC explorer and vice versa), navigate to the “Blocks Validated” page to see how recently it validated a block (ex: [https://volta-explorer.energyweb.org/address/0xaa31f1988d6049f3e4b54136a261ed22a7e4cf27/validations](https://volta-explorer.energyweb.org/address/0xaa31f1988d6049f3e4b54136a261ed22a7e4cf27/validations)). With \~30 validators and a 5 second block time, a functioning node validates a block once every \~2:30 minutes. Bookmark the “Block Validated” pages for both your Volta and EWC nodes to easily check if they’re validating.

Using the steps listed below, you can also view your validator node’s “Company Name” in each block it has sealed. The “Company Name” shows up in the extraData field of a block, but it's not shown directly in the explorer.

1. Determine the block number or block hash you want to check from the explorer
2. You can use the following commands to fetch block data:

`curl --data '{"method":"eth_getBlockByNumber","params":["0x_blocknumber_in_hex_here",true],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST https://volta-rpc.energyweb.org`&#x20;

`curl --data '{"method":"eth_getBlockByHash","params":["0x_blockhash_here",true],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST https://volta-rpc.energyweb.org`

1. Find the `extraData` field and copy the value,
   * e.g: **"extraData":"0x76616c696461746f722d35342e3135342e3130312e353454454f"**. \[This is the company name (or whatever info) you set during the installation encoded as hex]
2. Paste the value here to convert to text: [https://onlineutf8tools.com/convert-hexadecimal-to-utf8](https://onlineutf8tools.com/convert-hexadecimal-to-utf8)

### **SSH into your node and check the containers** <a href="#ssh-into-your-node-and-check-the-containers" id="ssh-into-your-node-and-check-the-containers"></a>

Once you SSH into your node, you can use the following commands to check the status of your server and docker containers running validator services.

Use the following command to make sure you have admin rights before running other commands

| `sudo -s` |
| --------- |

Run this command to list all running docker containers:

| `docker ps -a` |
| -------------- |

You should see these three containers with STATUS “Up **X** hours”

* `docker-stack_parity_1`
* `docker-stack_parity-telemetry_1`

### **Check your node’s resources** <a href="#check-your-nodes-resources" id="check-your-nodes-resources"></a>

If your node is hosted by a cloud provider, you will likely have access to a dashboard from that provider with information on the amount of disk space your node has available and other relevant info.

If you are SSH’d into your server, you can also run this command to check if your disk is nearing capacity:

| `df -h --total` |
| --------------- |

And to see how much disk space your docker containers are using, run:

| `docker system df -v` |
| --------------------- |

### **Check your node’s logs** <a href="#check-your-nodes-logs" id="check-your-nodes-logs"></a>

Logs can give you a view into

```
sudo -s
cd docker-stack
docker-compose logs
```

To save your logs and transfer them to your local machine use the following commands

`docker-compose logs > ~/YOURCOMPANY_logs.txt`

You will likely need to stop (ctrl + c) this after a little while as it doesn’t seem to auto-complete.

Make sure the logs contain whatever timeframe you’re interested in (e.g., when your node stopped syncing).

Now transfer them to the Downloads folder on your personal computer using this command in a fresh terminal:

`scp -P 2222 -i YOURKEYS.pem ubuntu@YOUR_INSTANCE:/home/ubuntu/YOURCOMPANY_logs.txt ~/Downloads/`

If you were successful, you should see a download bar complete and have the file in your Downloads folder.

### **Validator Dashboard** <a href="#validator-dashboard" id="validator-dashboard"></a>

\[Coming Soon]

* Public-facing dash that only links node attributes to a public address
* Address, # of peers, latest block, list of unsynced nodes
