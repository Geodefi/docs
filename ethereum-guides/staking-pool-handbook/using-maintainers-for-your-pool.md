# Using Maintainers for Your Pool

### Why Are Maintainers Needed?

Not really needed per se...

Maintainers can be useful for bigger staking pools to automate some operations. Currently, its primary use for Staking Pools is **choosing new Operators and distributing the incoming deposits**.

Learn more about them here:

{% content-ref url="../../key-concepts/permissionless-configurable-staking-pools/maintainers.md" %}
[maintainers.md](../../key-concepts/permissionless-configurable-staking-pools/maintainers.md)
{% endcontent-ref %}

{% hint style="info" %}
At any given point, a Staking Pool can have **1 maintainer** **at most.**
{% endhint %}

### Setting Your Maintainer

```javascript
Portal.changeMaintainer(id, new_maintainer_address);
```

You can set any address as your maintainer, it is <mark style="color:green;">safe to trust</mark>, as they can not do much harm 🙂

{% hint style="info" %}
If you have a script that will update your allowances as new stake comes in, set it as your Maintainer.&#x20;
{% endhint %}

If you want to use third party maintainers, we will provide some contracts in the future.

These will be community owned maintainers and will help you optimize your validators towards Profitability or Further decentralization.
