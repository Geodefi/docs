# Securing Your Withdrawal Contract

#### Learn More About the Withdrawal Contracts:

{% content-ref url="../../key-concepts/withdrawal-contracts/" %}
[withdrawal-contracts](../../key-concepts/withdrawal-contracts/)
{% endcontent-ref %}

As a pool owner, it is your responsibility to keep your Withdrawal Contract up to date, or your pool will immediately go under <mark style="color:red;">**Recovery Mode**</mark>.

### Checking for Upgrades

```javascript
// compare these 2 version IDs:

const lastVersion = await Portal.getWithdrawalContractVersion();
const currentVersion = await WithdrawalContract.getContractVersion();

const needs_upgrade = lastVersion != currentVersion ;
```

### Fetching an Upgrade Proposal

Anyone can fetch an upgrade proposal and force your Staking Pool into Recovery Mode.

However, only the Controller can approve this upgrade proposal to effectively change the code:

```javascript
await WithdrawalContract.fetchUpgradeProposal();
```

### Upgrade

```javascript
await WithdrawalContract.upgradeTo(newImplementation);
```

{% hint style="success" %}
<mark style="color:green;">It is always best practice to be in touch with us, in order to be notified for potential upgrades:</mark>\
[_<mark style="color:blue;">**Join Geode's Discord**</mark>_](https://discord.com/invite/RC8fTTuJtm)
{% endhint %}
