# Using a Bound Liquidity Pool

Learn more about the benefits of using a bound liquidity pool with your staking pool:

{% content-ref url="../../key-concepts/bound-liquidity-pools.md" %}
[bound-liquidity-pools.md](../../key-concepts/bound-liquidity-pools.md)
{% endcontent-ref %}

#### You can have a bound Liquidity Pool created upon initiation:

{% content-ref url="initiating-a-customizable-staking-pool.md" %}
[initiating-a-customizable-staking-pool.md](initiating-a-customizable-staking-pool.md)
{% endcontent-ref %}

#### You can also create a bound Liquidity Pool after initiation:

```javascript
Portal.deployLiquidityPool(id);
```

{% hint style="danger" %}
<mark style="color:red;">You can not deactivate a Bound Liquidity Pool later.</mark>
{% endhint %}
