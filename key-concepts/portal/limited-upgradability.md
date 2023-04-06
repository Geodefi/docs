# ⚠ Limited Upgradability

## Global Trustlessness

Geode Finance cannot upgrade the source code of it's contract infrastructure without the approval of their users.&#x20;

This creates a more secure implementation and prevents any harmful events that can be caused by a Governance Token, thus removes the trust between users and the developers.

{% hint style="success" %}
#### <mark style="color:green;">Limited Upgradability is used within both Portal and Withdrawal Contract.</mark>
{% endhint %}

### Upgrading the Portal

1. A new implementation address is proposed by Governance.
2. Proposal can be approved by Senate.
3. Upgrade is now allowed.

### Upgrading Withdrawal Contracts

1. New Withdrawal Contract is proposed by the Governance with the TYPE of `WITHDRAWAL_CONTRACT_UPGRADE`
2. Senate Approves the new Withdrawal Contract. From now on Portal references to the new implementation address
3. Then, anyone can call `fetchUpgradeProposal`:
   1. `fetchUpgradeProposal,` notifies the Portal.
   2. Portal proposes a new implementation on Withdrawal Contract with the TYPE of `UPGRADE`.
   3. Withdrawal Contracts pointing the old implementation enters into **Recovery Mode.**
   4. Owners can approve the proposal and migrate to a new implementation, exiting from the Recovery Mode.

{% hint style="success" %}
If the `fetchUpgradeProposal` **is called by the Owner, the proposal is also automatically approved.**
{% endhint %}
