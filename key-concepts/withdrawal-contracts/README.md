# 🛡 Withdrawal Contracts

## <mark style="color:green;">Savior of the Stakers.</mark>

#### The Staking Library utilizes <mark style="color:purple;">Contract Owned Staking Derivatives</mark>. The contract in question is called the Withdrawal Contract.

Withdrawal Contracts are simple contracts:

They secure the staked funds and handle the withdrawal queues.&#x20;

### Every Staking Pool has a unique Withdrawal Contract.&#x20;

When a staking pool is created, the latest version of the Withdrawal Contract is deployed automatically.

The owner of the Withdrawal Contract is the owner of the staking pool.

#### Any tokens related to a validator end their journey in the Pool's Withdrawal Contract:

* Staking Rewards
* Block Rewards
* MEV profits
* Principle
* Fees

### Withdrawal Contracts Are Smart

**Like Portal not trusting it's Governance, Withdrawal Contracts don't trust Portal : it uses dual governance and limited upgradability.**

Changing the latest version of the Withdrawal Contracts requires the approval of the Senate.

Changing the implementation code of a specific Pool's Withdrawal Contract requires the approval of the Pool Owner.

Meaning, although they are upgradable, not even Geode Governance has access to the funds within the Withdrawal Contract.

### Upgrading Withdrawal Contracts

1. A new Withdrawal Contract is proposed by the Governance with the TYPE of `WITHDRAWAL_CONTRACT_UPGRADE`
2. Geode Senate Approves the new Withdrawal Contract. From now on, Portal refers to the new implementation address
3. Then, anyone can call `fetchUpgradeProposal`:
   1. `fetchUpgradeProposal` notifies the Portal.
   2. Portal proposes a new implementation of Withdrawal Contract with the TYPE of `UPGRADE`.
   3. Withdrawal Contracts pointing the old implementation enter into **Recovery Mode.**
   4. Owners can approve the proposal and migrate to a new implementation, exiting from  Recovery Mode.

{% hint style="success" %}
If the `fetchUpgradeProposal` **is called by the Owner, the proposal is also automatically approved.**
{% endhint %}

### <mark style="color:purple;">Recovery Mode</mark>

{% content-ref url="recovery-mode.md" %}
[recovery-mode.md](recovery-mode.md)
{% endcontent-ref %}

### <mark style="color:purple;">Withdrawal Queue</mark>

{% content-ref url="withdrawal-queue.md" %}
[withdrawal-queue.md](withdrawal-queue.md)
{% endcontent-ref %}
