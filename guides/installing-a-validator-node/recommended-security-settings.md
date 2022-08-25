# Recommended Security Settings



Running a validator node requires raised awareness of host and node security as authorities are a main attack surface to disturb operation of the blockchain. The following security rules **are strongly recommended**:

* No services are permitted to run on the same host that are not part of the validator node package
* All incoming connections on all ports except SSH (22/tcp) and the P2P (30303/tcp, udp) port have to be firewalled on the host with DROP rules. To guarantee proper network etiquette, incoming ICMP has to be accepted.
* SSH access is only allowed for non-root users
* SSH access is only allowed through RSA keys
* OpenEthereum or Nethermind client RPC endpoints (HTTP, WebSocket) have to be disabled
* System updates have to applied regularly and in a timely manner
* Regular (monthly) run of rootkit detectors
* If you are using AWS please also check out the additional [AWS Security guide](https://energyweb.atlassian.net/wiki/spaces/EWF/pages/703037441/AWS+Security+Guide).
