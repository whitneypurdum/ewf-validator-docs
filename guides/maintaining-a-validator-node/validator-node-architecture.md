# Validator Node Architecture

The System architecture of a validator node on the Energy Web Chain is made up of two main components. (Note: the original node architecture featured a node control component, but it was never used and formally deprecated in 2020).&#x20;

![High-level Validator Node Architecture](<../../.gitbook/assets/Screen Shot 2022-02-28 at 2.25.31 PM.png>)

&#x20;**Client**: The OpenEthereum or Nethermind client that connects the validator to the Energy Web Chain, collects transactions and proposes blocks according to the [AuRa consensus algorithm](https://openethereum.github.io/Aura.html). Read the documentation of the OpenEthereum client [here](https://openethereum.github.io/), and the Nethermind client [here](https://docs.nethermind.io/nethermind/ethereum-client/download-sources). \


**Telemetry**: There is a monitoring system on the validator node that uses Telegraf to securely send telemetry to an [InfluxDB](https://www.influxdata.com/) that is connected to [Grafana](https://grafana.com/) and the EWC Validator Data Warehouse & Dashboard. The use of telemetry is opt-in. Validators can disable it if they have their own monitoring system in place that allows for real time tracking of all relevant metrics.

Telemetry data includes:

* CPU usage of the host machine
* Memory usage of the host machine
* Disk usage of the host machine
* Number of connected peers
* List of visible P2P peers
* Current block (latest block synced by the node)
* Network latency to 3 different and major locations (e.g. cloudflare, google, amazon)
* Network throughput
* Network error rate
* Number of SSH keys for the host machine
* Service status for SSH, docker and the parity container
* SHA256 hashes of key system components/binaries
* Current chain specification file (or hash)

As this is sensitive data, we rely on well established industry solutions to transfer these metrics off the validator node. Telegraf is a server agent that plugs into many different services to collect data. Telegraf collects relevant metrics from the host machine and the custom-built parity metrics collector which allows Telegraf to receive the metrics from the parity client. For more information on Telegraf visit: [https://docs.influxdata.com/telegraf/v1.10/](https://docs.influxdata.com/telegraf/v1.10/)

The collected metrics are then stored in an InfluxDB database and can be visualized using the monitoring tool Grafana. For more information on influxDB visit: [https://docs.influxdata.com/influxdb/v1.7/](https://docs.influxdata.com/influxdb/v1.7/)

For more information on Grafana visit: [https://grafana.com/docs/](https://grafana.com/docs/)

The use of telemetry is opt-in. Validators can disable it if they have their own monitoring system in place that allows for real time tracking of all relevant metrics.\


All components are run in separate docker containers managed by docker compose. For additional information on docker visit: [https://docs.docker.com/](https://docs.docker.com/) and [https://docs.docker.com/compose/](https://docs.docker.com/compose/)
