# Validators code of conduct

The defining feature of the Energy Web Chain is its Proof of Authority consensus mechanism, which relies on reputable entities with valid authority in the global energy sector (i.e. actual market influence) to credibly maintain trust in the network. The adoption and success of the EW Chain is dependent on maintaining an engaged, active community of validators.

Like any community, the EWC validators must be aligned on a common set of principles and follow mutually-agreed upon rules. This Code of Conduct defines the operational and governance expectations and responsibilities for EWC validator organizations. The Code was formally adopted by a supermajority vote in December 2020 and amended by majority vote in December 2021.&#x20;

### Community Expectations for EW Chain Validators

Organizations hosting validator nodes must:

* Proactively contribute to the EW Chain community in one or more of the following ways:
  * **Developing Applications & projects**: Building or participating in projects, applications, or markets that utilize the open-source EW-DOS technology stack.
  * **Contribution to EW-DOS open-source code**: Submitting pull requests to any of the open-source EW-DOS repositories, including the EW Chain, Utility Layer, and Toolkits.&#x20;
  * **Contributing to Community Fund Proposals**: Identifying opportunities to leverage the Community Fund to support the development or integration of other relevant technologies/projects into the EW Chain or broader EW-DOS stack.
  * **Contributing to Governance Proposals**: Creating, responding to, and participating in threads (topic discussions) and formal voting proposals in the governance forum on a regular basis.
  * **Community Building**: Identifying and recruiting other organizations (e.g. energy market participants, regulators, researchers, technology partners) to participate in projects and/or the EWF community.
* Actively participate in the EWC Validator Community:
  * At least one representative from each validator organization should attend the monthly governance meetings on a regular basis.
  * At least one representative from each validator organization should regularly (at least monthly) engage in the EWC governance forum to create or respond to different topics and proposals.
  * Engaging in discussions and helping answer questions from peers in the dedicated validator communication and support channels.
* Hold themselves and peer validators accountable to:
  * Act with honesty, integrity, and openness in working in the best interest of the EWC community.
  * Comply with all applicable laws, rules, and regulations, particularly anti-bribery, anti-corruption, and anti-money-laundering laws, rules, and regulations.
  * Avoid conflicts of interest between the validator organization (and its core business) and the EWC (and EWC community).
* Refrain from the following unacceptable behavior:
  * **Non-participation**: Organizations cannot just “set it and forget it”; if an organization sets up a validator node and subsequently never joins calls, participates in discussions, or contributes the the EWC community in any way then they will face a penalty or be removed from the validator set.
  * **Obvious rent-seeking**: The EW Chain is operated by and designed for the energy industry; its purpose (i.e. utility) is to support novel digital solutions that help advance the global energy transition. Validators who are transparently motivated solely by EWT block rewards, abuse their position as validators to create deleterious effects on EWT markets, and/or do not contribute to the mission and success of the EWC ecosystem as described above, will face temporary suspension and/or expulsion from the validator set. Rent-seeking is defined as validators liquidating greater than 10% of their block reward balance within any given 30-day period.&#x20;
  * **Lack of communication**: Organizations who do not respond to official validator communications in the event of an operational or governance task will face temporary suspension and/or possible expulsion.

### EW Chain Validator Organizational Accountability

Organizations who host EW Chain validator nodes are responsible for the following:

* **Keeping their node healthy and private keys secure**. This includes implementing best practices for key management, regular maintenance / updates to the node host environment, and proactively alerting the EWC community if they identify any potential bugs, vulnerabilities, or risks that can impact validator nodes. Validator organizations are expected to perform node updates in a timely manner to support EWC network upgrades.&#x20;
* **Monitoring their node**. Proactively monitoring their node for issues and identifying faults that result in the node failing to successfully seal blocks.&#x20;
* **Maintaining internal technical expertise to be self-sufficient**. Each organization must possess sufficient internal technical resources to perform routine maintenance on the node / host environment as well as independent troubleshooting and fault diagnosis using the Wiki, Github, and the validator Slack channels (i.e. other validators in the community) as primary support tools.
* **Responding to official EWC validator communications in a timely manner.** Validator organizations are expected to maintain an accurate contact list and respond to communications related to the operation and governance of the EWC.&#x20;
* **Dedicating time to participate in meetings and governance decisions**. At least one representative from each validator organization should plan on dedicating sufficient time each month to participate in calls, review documentation, and engage in the governance forum.

### Code of Conduct Requirements & Enforcement

The following requirements were adopted by a majority vote in December 2021 and are effective immediately. These requirements are in addition to all existing terms of the Code and will be automatically monitored on a forward basis using the Validator dashboard (2022 onwards).

**Validator Node Health Requirements**

1. Each Validator node must achieve at least 95% uptime on a rolling 30-day basis (equivalent to no more than 36 hours of unplanned outages over the preceding 30-day period). A node is considered failed if it falls more than 120 blocks behind the latest block and/or fails to seal a block at its designated slot for 5 or more consecutive authority rounds. Node outages during regularly-scheduled network upgrades or planned maintenance windows are excluded from this requirement.

**Governance & Community Participation Requirements**

1. Energy Web Validators must participate in at least 75% of governance meetings and 90% of voting events on a rolling 6-month basis. Participation is defined as having one or more representatives from the Validator organization attending meetings and having one representative from the organization casting a vote in open proposals within the governance forum, respectively.
2. Each quarter, all Energy Web Validators must demonstrate at least one specific example of community participation as defined in the Code (i.e. Developing Projects & Applications, Contribution to open-source EW-DOS source code, Contributing to Governance Proposals, Contributing to Community Fund Proposals, Community Building).

**Energy Web Token (EWT) Block Reward Requirements**

As leaders and stewards of the EWC, Validators commit to responsibly managing liquidation of EWT reward balances so as to not create deleterious effects on EWT markets. Validators qualify to transfer block rewards from payout addresses to known exchanges if three requirements are met:

1. Time requirement: Validators must successfully host a node and comply with the Validator Code of Conduct for a period of 6 consecutive months following initial Validator node activation.
2. Balance requirement: Validators must maintain a minimum balance of block rewards equal to or greater than the trailing 6-month average reward earned per validator (for example, if the average validator earned 15,000 EWT total in block rewards in the preceding 6 months, all validators must maintain a balance of at least 15,000 EWT in their payout addresses to remain eligible).
3. Rent-seeking requirement: Once the time and balance requirements above are met, Validators may only transfer a maximum of 10% of their current block reward balance within any given 30-day period to known exchange addresses.&#x20;

Current block reward balance is defined as the sum of EWT held in the Validator’s payout address(es) and EWT used in the Energy Web ecosystem on a rolling 12 month basis for business activity including but not limited to paying Energy Web Membership dues, Energy Web Chain transaction fees, procuring Utility Layer services, and staking EWT.

These requirements are designed to incentivize Validators to use EWT earned from block rewards in the Energy Web ecosystem.

Validator adherence to the Code of Conduct will be automatically monitored using the Energy Web Validator dashboard, which will collect data from the Validator governance forum, node telemetry, and the EWC itself to assign a quantitative performance score for each of the above categories.

The performance of each Validator will be made public via the dashboard so Validators and the wider community can hold each Validator accountable for maintaining compliance.

The Code will be enforced objectively as follows:

* Single violation, defined as an initial breach of any one of the above categories, will result in an immediate two-week suspension of the validator node.
* Secondary violation, defined as a breach of two categories concurrently, a breach of the code as listed below, or a second violation of a single category within a rolling 12-month period, will result in an immediate four-week suspension of the validator node. Reinstatement of the node is contingent upon the Validator submitting a written plan to remedy past violations and maintain compliance with the Code of Conduct within the governance forum.
  * Failure to perform necessary node updates as part of a planned network upgrade;&#x20;
* Significant violation, defined as a breach of all three categories concurrently, a breach of the code as listed below, or two or more secondary violations within a rolling 12-month period, will result in permanent expulsion from the EW Chain validator community.
  * Experiencing a major security failure in which a validator node's host machine and/or private keys are compromised by unauthorized actors;&#x20;
  * Engaging in illegal, unethical, or anticompetitive behavior;&#x20;
