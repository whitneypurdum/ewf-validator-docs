---
description: >-
  This page provides step-by-step instructions for how to install a validator
  node in the Volta test network and the production Energy Web Chain network.
---

# Validator Node Installation Instructions



{% hint style="info" %}
**Good to know: The overall process of installing a validator node is identical on both the Volta test network and the main Energy Web Chain. The only difference is the installation script used in Step 2 -  be sure that you use the correct installation script for the intended network!**&#x20;
{% endhint %}

{% hint style="warning" %}
We recommend using the Nethermind Validator Installation Script, as the OpenEthereum Client is no longer in development and has been deprecated. You can find the validator installation scripts here:

1. Volta:[https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate/nethermind](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate/nethermind)
2. EWC:\
   [https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate/nethermind](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate/nethermind)
{% endhint %}



1. Install the operating system and prepare the host machine according to the requirements (Step 1 in the previous checklist).&#x20;
2. Select the correct Client installation script matching the desired network and installed OS on the energyweb github:
   * For the VOLTA TEST NETWORK:  [https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate), or copy the recommended client directory ([Nethermind](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/volta-affiliate/nethermind)) from the **volta-affiliate** directory to the host
   * For the main **ENERGY WEB CHAIN**: [https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate), or copy the recommended client directory ([Nethermind](https://github.com/energywebfoundation/ewc-validator-node-install-scripts/tree/master/ewc-affiliate/nethermind)) from the **ewc-affiliate** directory to the host
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
