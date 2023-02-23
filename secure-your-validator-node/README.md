---
description: Importance to secure validator node and some best practice to secure it
---

# Secure Your Validator Node

## Rationale

In EnergyWebChain network, validator nodes are typically network's stakeholders and they are usually trusted organizations . These validator nodes are responsible for network consensus, verifying state transitions, validating transactions and adding them to the EWC blockchain.

Thus these validator nodes are responsible for maintaining the integrity of the network by ensuring that all transactions are valid. They also play an important role in preventing malicious actors from manipulating the network or adding fraudulent transactions to the blockchain.

### Importance to secure the validator node <a href="#importance-to-secure-of-validator-node" id="importance-to-secure-of-validator-node"></a>

There are several reasons to secure and protect validator node:

* Validator nodes hold sensitive information, such as private keys, keystore file, secret etc which must be protected to ensure the security of the network.
* Trust is a critical aspect of any blockchain network, and if a validator node is compromised, it can lead to a loss of trust in the network among its users and stakeholders.
* If a validator node is compromised, it can potentially allow malicious actors to add fraudulent transactions to the blockchain, which can undermine the integrity of the entire network.
* A secure validator node is important for maintaining the performance and scalability of the network, as it ensures that the network can handle a high volume of transactions without any issues.

> _**Securing a validator node is critical to the overall security and integrity of the network, and it is essential to maintaining the trust and confidence of its users, members and stakeholders.**_
>
> _**For these the validator members' must have infrastructure to protect the validators from any kind of attacks.**_

#### Protect your validator node from unauthorized access <a href="#accessing-validator-node" id="accessing-validator-node"></a>

In EnergyWebChain (Proof of Authority) network, the validator nodes are run by recognized enterprises, organizations. These nodes are responsible for validating transactions and blocks. It's important to ensure that access to validator nodes is properly secured and controlled.

#### Here are some best practices for securing validator nodes from an access perspective

* Limit access to validator nodes to only those users who need it, as this helps to prevent unauthorized access and reduces the attack surface. This can be achieved by using role-based access control (RBAC) and granting access only to users with specific job functions.
* The principle of least privilege states that users should only have the minimum level of access necessary to perform their job function. This helps to prevent unauthorized access and misuse, as users are only able to access the nodes that they need to perform their job.
* Monitor and log access to validator nodes, this helps to detect and respond to any suspicious or malicious activity, and to identify potential security breaches. Access logs should be regularly reviewed and analyzed to identify any unusual activity, such as repeated login attempts or attempts to access nodes that the user does not have access to.
* Configure firewalls to block unauthorized access to validator nodes and restrict access to specific ports and IP addresses.
* It is important to train employees on the importance of security and on the proper procedures for accessing validator nodes. This helps to prevent accidental security breaches and to ensure that employees understand the importance of following security best practices.

Securing validator nodes from an access perspective requires a combination of technical and procedural measures. By limiting access to only necessary users, using RBAC, monitoring and logging access, organizations can ensure that validator nodes are secure.

These are just a few of the many best practices that organizations can use to secure their validator nodes.

> _**It's important to mention that, even following all the steps mentioned above, there's no guarantee that a validator node will never be compromised; it's important to have an incident response plan in place and to be prepared to take action in the event of a security incident.**_

#### Secure your validator node <a href="#secure-your-validator-node" id="secure-your-validator-node"></a>

Securing validator nodes in a on-premise environment or cloud platform is always a complex process. Here are some steps that can be taken to secure validator nodes:

* Use virtual machines that have been configured to meet security best practices, such as using secure images, applying security patches, and limiting access to specific ports and IP addresses.
* Take advantage of cloud-native security features, such as firewalls, intrusion detection and prevention systems, and encryption services, to protect validator nodes from external threats.
* Firewalls can be used to block unauthorized access to validator nodes and to restrict access to specific ports and IP addresses, also control inbound and outbound traffic to validator nodes and to restrict access to specific ports and IP addresses.
  * _It’s worth to note that validator node should listen only p2p port (30303); other than that node should not listen on any other port._
* Use a virtual private cloud (VPC) to create a private, isolated network for validator nodes, which can help prevent unauthorized access or eavesdropping.
* Use identity and access management (IAM) to control access to validator nodes and to ensure that only authorized users can access them.
* Use monitoring and logging tools to track and record activity on validator nodes, which can help detect and respond to any suspicious or malicious activity.
* Monitoring network activity can help detect and respond to any suspicious or malicious activity that may be targeting validator nodes.
* Regular security audit helps to identify and resolve any security weaknesses or vulnerabilities of validator nodes.
* Regularly updating software and applying security patches can help protect validator nodes from known vulnerabilities.
* Use a cloud security provider to manage and secure validator nodes, which can help to ensure that they are configured and maintained in accordance with security best practices.
* Follow Linux best practices like
  * Disable root login and password authentication for SSH
  * Disable non-essential SSH subsystems
  * Disable unwanted services and daemons

By following these practices, organizations can help prevent unauthorized access, reduce the attack surface, data breaches, and other security incidents and maintain the trustworthiness of the blockchain and ensure the security of their validator nodes.

> _**It's important to mention that security in on-premise environment or cloud platforms is an ongoing process; it's worth to stay up-to-date with the latest security best practices and to continuously monitor and update the security of validator nodes.**_

> **EWF strongly recommends that your organization implements a robust internal governance process and security policy for managing the validator node private keys, accessing the node, and managing its EWT balance.**

### Recommended links to check

* [AWS Best Practices for Security, Identity, & Compliance](https://aws.amazon.com/architecture/security-identity-compliance/)
* [Azure security best practices and patterns](https://learn.microsoft.com/en-us/azure/security/fundamentals/best-practices-and-patterns)
* [Google Cloud security best practices center](https://cloud.google.com/security/best-practices)
* [DigitalOcean - Recommended Security Measures to Protect Your Servers](https://www.digitalocean.com/community/tutorials/recommended-security-measures-to-protect-your-servers)
* [23 Linux Server Security Tips and Best Practices](https://betterprogramming.pub/23-linux-server-security-tips-and-best-practices-b8c59b9b9e3e)
