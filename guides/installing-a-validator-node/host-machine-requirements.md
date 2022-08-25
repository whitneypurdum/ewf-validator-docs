# Host Machine Requirements

You can choose to run your validator node either On-Premise on your own hardware or on a virtual machine / cloud computing instance of your choosing. If you have any questions please contact the EWF NetOps team: [netops@energyweb.org](mailto:netops@energyweb.org)

_**The following specifications are strongly recommended, but validators are free to configure their host machine at their discretion in accordance with relevant internal policies or requirements. Please note that hosting a node on a machine with insufficient CPU, storage, RAM, and/or networking capacity may result in node failure (e.g. unable to connect to peers, unable to synchronize, unable to seal blocks) and require extra labor to reconfigure the host machine.**_&#x20;

#### **On-Premise Hardware**

A on-premise node should have these specs or higher. For security reasons these resources  must be reserved for the validator node and not shared with other workloads.

1. Modern Multi-core x64 CPU (at least 4 threads, preferably Xeon-class)
2. 8GB RAM (preferably ECC)
3. Local SSD storage, 300 GB free capacity for blockchain, redundant in RAID-1
4. 1 GBit NIC

#### Cloud Environments

The following specifications are strongly recommended based on the most common cloud environments used by existing EW Chain validators. You may select any cloud provider of your choosing

**Amazon AWS**

The following EC2 instance sizes are appropriate to run validators. These resources should be reserved for the validator node and not shared with other workloads.

* m5.xlarge
* m5.2xlarge
* m5a.xlarge
* m5a.2xlarge
* c5.xlarge
* c5.2xlarge

The default EBS storage assigned (normally 8GB) is not large enough to run the node. Make sure to run the node with following EBS storage settings:

* General Purpose SSD (gp2)
* at least 300GB size

**Microsoft Azure**

The following Azure Virtual Machine sizes are suitable to run a validator. These resources should be reserved for the validator node and not shared with other workloads.

* D4s\_v3
* DS3\_v2
* B4ms

Use Premium SSD as attached storage with a size of at least 300GB.

**Google Cloud**

The following Google Cloud Virtual Machine sizes are suitable to run a validator node. These resources should be reserved for the validator node and not shared with other workloads.&#x20;

* n2-standard-4 and above: https://cloud.google.com/compute/docs/general-purpose-machines#n2\_machines

**Digital Ocean**

The following Digital Ocean Virtual Machine sizes are suitable to run a validator. These resources should be reserved for the validator node and not shared with other workloads.

* General Purpose Droplet: 16 GB memory, 4vCPU
* CPU-Optimized Droplet: 8 GB memory, 4vCPU

Use Block Storage as attached SSD storage with a size of at least 300 GB.&#x20;

## **Connectivity Requirements**

The following requirements should be met to ensure proper operation:

* Wired connection with 100 MBit/s symmetric link to the internet
* Low latency connection to next internet hop (<5ms)
* No data volume limitations

Even though we recommend a 100MBit/s connection, that connection will likely not be saturated by the node. You can expect 10-30MBit/s when the chain is under load. Traffic will mainly flow on port 30303 (udp/tcp).

##



