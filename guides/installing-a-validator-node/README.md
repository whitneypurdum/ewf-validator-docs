# Installing a Validator Node

## Pre-Installation Checklist:

1. Review the validator node [Host Machine Requirements](host-machine-requirements.md), [Operating System Requirements](operating-system-requirements.md), and [Recommended Security Settings](operating-system-requirements.md) carefully. Then choose a host environment (on-premise hardware or qualified cloud provider) and favored operating system. &#x20;
2. **Assign a static public IP address to the host.**&#x20;
   * Make sure that the public IP will not change over time.&#x20;
     * Additional information for AWS: [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)
     * Additional information for Azure: [https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-ip-addresses-overview-arm](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-network-ip-addresses-overview-arm)****
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

## How to install a validator node

{% hint style="info" %}
**Good to know: The overall process of installing a validator node is identical on both the Volta test network and the main Energy Web Chain. The only difference is the installation script used in Step 2 -  be sure that you use the correct installation script for the intended network!**&#x20;
{% endhint %}

****

1. Install the operating system and prepare the host machine according to the requirements (Step 1 in the Checklist above).&#x20;
2. Select the correct Client installation script matching the desired network and installed OS on the energyweb github:
   * For the VOLTA TEST NETWORK:  [https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate), or copy the desired client directory (OpenEthereum or Nethermind) from the **volta-affiliate** directory to the host
   * For the main **ENERGY WEB CHAIN**: [https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate), or copy the desired client directory (OpenEthereum or Nethermind) from the **ewc-affiliate** directory to the host
3. Make sure the latest system updates are installed by running :
   *   For Debian and Ubuntu:

       ```
       sudo apt-get update && sudo apt-get dist-upgrade
       ```

       For CentOS:

       ```
       sudo yum update
       ```
4.  Make the script executable with&#x20;

    ```
    chmod +x ./install-*.sh
    ```
5. Run the script (NOTE: _please do not use the_ `--auto` _parameter which can be used to take default for node-name and generate a random key_).
6. If the installation was successful, it should generate a .txt file (named **install-summary.txt**) that lists the **node address**, **IP address**, and **influxDB** **username/password**. You will need to provide these details via a form in the next step to successfully add your validator node to the [validator system contract](https://energyweb.atlassian.net/wiki/spaces/EWF/pages/702119975/Validator+set+contracts).&#x20;
   * If you encounter issues with the installation or the **install-summary.txt** file is not generated:
     1. First review any [open issues on Github](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/issues) to see if there is a known issue.
     2. If the issue is not already known, submit a question in the #validators or #technical\_questions channels in the [EWF Member Slack space](https://ewf-affiliates.slack.com) to troubleshoot.
7. Submit node installation details using the appropriate form below:
   1. For the VOLTA TEST NETWORK, enter details [here](https://share.hsforms.com/1t9po2Du9TgabWS28TQWx1A37vj2).&#x20;
   2. For the main **ENERGY WEB CHAIN,** enter details [here](https://share.hsforms.com/1UAF\_LAH1RMeYCN-pUY5pnQ37vj2).&#x20;
8. After submitting the installation summary via the form, you will receive a confirmation email with next steps and links to helpful resources. &#x20;
