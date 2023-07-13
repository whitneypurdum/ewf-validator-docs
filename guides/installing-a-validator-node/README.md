---
description: >-
  This page provides an overview of the steps required to install a validator
  node on the Energy Web Chain.
---

# Installing a Validator Node

{% hint style="info" %}
Be sure to follow the below steps in order!&#x20;
{% endhint %}

## Pre-Installation Checklist:

1. Review the validator node [Host Machine Requirements](host-machine-requirements.md), [Operating System Requirements](operating-system-requirements.md), and [Recommended Security Settings](operating-system-requirements.md) carefully. Then choose a host environment (on-premise hardware or qualified cloud provider) and favored operating system. &#x20;
2. **Assign a static public IP address to the host.**&#x20;
   * Make sure that the public IP will not change over time.&#x20;
     * Additional information for AWS: [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)
     * Additional information for Azure: [https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-ip-addresses-overview-arm](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-ip-addresses-overview-arm)
3. **Verify that the host is dedicated only for the EW Chain Validator client.**
   * If yes, proceed to the next step.
   * If no, remove all other processes / applications from the host, or create a new isolated instance.
4. **Verify that you have the correct installation script for your chosen OS here:** [**https://github.com/energywebfoundation/ewc-validator-node-install-scripts**](https://github.com/energywebfoundation/ewc-validator-node-install-scripts)
   1. If yes, then proceed to the next step.
   2. If no, choose the correct installation script before proceeding.
5. **Review the default safe firewall settings set up by the installation script.**
   1. Do these settings comply with your company's firewall settings or will you have to adapt them afterwards?
      1. If the default settings comply with your company’s policies, proceed to the next step.
      2. If the default settings do not comply with your company’s policies, adapt the settings as necessary. If you encounter issues or conflicts with internal IT policies, you can post in the [EWC Validator Knowledge Base](https://discuss.energyweb.org/c/knowledge-base/15) to discuss resolution options.
6. **Review the installation script and verify that there are no errors or discrepancies with your system setup (link above).**
   1. If errors are observed, open an Issue in the installation script Github repository or post to ta relevant topic in the [Validator Knowledge Base](https://discuss.energyweb.org/c/knowledge-base/15) to resolve.\
      \

7. **Make sure you have read and understand the operational and governance rules and responsibilities as outlined in the** [**Validator Code of Conduct**](https://energy-web-foundation.gitbook.io/energy-web/technology/the-stack/trust-layer-energy-web-chain/energy-web-chain-governance)**.**\

8. **Read the** [**documentation on the validator architecture**](https://energyweb.atlassian.net/wiki/spaces/EWF/pages/715915274/Validator+Node+Architecture) **to ensure you have a robust understanding of the inner workings:**&#x20;
   * Optional: Read the [documentation on the system contracts](https://energyweb.atlassian.net/wiki/spaces/EWF/pages/702054413/System+contracts) to familiarize yourself with the overall system.\
     \

9. **Confirm that you have at least two ways to contact EWF and the valdiator community if you encounter problems:**
   * NetOps distribution list: [netops@energyweb.org](mailto:netops@energyweb.org)
   * Join the #validator channel on Slack: [https://ewf-affiliates.slack.com/messages](https://ewf-affiliates.slack.com/messages)
   * Join the #technical-discussions channel on Slack: [https://ewf-affiliates.slack.com/messages](https://ewf-affiliates.slack.com/messages)
10. **Ensure that you are prepared to receive and securely handle value-bearing Energy Web Tokens (“EWT”) from block rewards at the time your validator is added to the validator set**_**.**_
    * EWF strongly recommends that your organization implements a robust internal governance process and security policy for managing the validator node private keys, accessing the node, and managing its EWT balance.
    * If you would like to hold block rewards in an address separate from the validator node, you can change the block reward payout address. Please see [instructions for calling the _setPayoutAddress_ function in the Reward Contract for further](https://energyweb.atlassian.net/wiki/spaces/EWF/pages/701923337/Reward+contract) details. _Please note that it is not possible to reallocate transaction fees to a separate account, so all validator nodes will accrue and maintain a balance of EWT from transaction fees._
11. _**Once all of the above steps are completed, install your validator node following the instructions**_ [_**here**_](validator-node-installation-instructions.md)_**.**_&#x20;

##

##

##
