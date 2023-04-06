# 🚨 Prison

#### Prison isolates the Node Operators from the Marketplace, in case they act in a faulty or malicious manner:

* Invalid validator proposal.
* Not withdrawing validator funds before the expected exit time.
* Not routing the block rewards, or MEV rewards to the Withdrawal Contract. &#x20;

The Prison Sentence for any of these infractions is 14 days.

{% hint style="info" %}
In the case that a Node Operator with a good track record is imprisoned for an honest mistake, Governance can bail out the imprisoned Operator early.
{% endhint %}

{% hint style="info" %}
Geode Governance can also imprison a Node Operator from the Marketplace, which is  indefinitely effective.
{% endhint %}

> **What happens when an operator is imprisoned?**
>
> 1. Can not propose new validators.
> 2. Can not stake to beacon chain for previously accepted validator proposals.
> 3. Can not change their parameters such as fees, validatorPeriod...
> 4. Can not access to `wallet`, effectively, can not claim their rewards.
