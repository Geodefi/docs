# ⚙ Permissionless Configurable Staking Pools

We learned how The Staking Library provides a firm foundation for Staking operations, and allows anyone to have a Staking Derivative:

{% content-ref url="../../the-staking-library/" %}
[the-staking-library](../../the-staking-library/)
{% endcontent-ref %}

Then, we learned how the Operator Marketplace makes staking operations much easier, and increases the user experience for both Pool Owners and Node Operators:

{% content-ref url="../../operator-marketplace/" %}
[operator-marketplace](../../operator-marketplace/)
{% endcontent-ref %}

Now, lets take a look at the Staking pools, and the superpowers of their Modular Architecture.

## One Transaction To Rule Them All!

During the same transaction for creation of a staking pool, the following functionalities can be configured:

### Private Pools - optional

* If a pool is Public, everyone can use it.&#x20;
* Private pools are only available to their owners and other whitelisted addresses.
* Pool owners can make pools public or private as they wish.
* Any contract with a `isWhitelisted()` function can be used by the Private Pools.

{% content-ref url="../../ethereum-guides/staking-pool-handbook/private-pools-and-whitelisting.md" %}
[private-pools-and-whitelisting.md](../../ethereum-guides/staking-pool-handbook/private-pools-and-whitelisting.md)
{% endcontent-ref %}

### Interfaces - optional

* **If you don't need an ERC20 for example, a pool can operate without an interface.**
* While gETH allows multiple interfaces, Portal only allows 1 interface per derivative for security reasons.
* Interfaces should be created on the initiation process. Currently, an interface **can** not be added after the pool initiation for security reasons.
* New interfaces require the approval of the Senate.
* Any interface can be chosen from the list below:

{% content-ref url="current-interfaces.md" %}
[current-interfaces.md](current-interfaces.md)
{% endcontent-ref %}

### Maintainers - optional

* **If you don't have a very active pool, you can choose your operators without a maintainer.**
* Pool tasks such as management of the Operators can be automated through maintainers.
* Adding a maintainer is not a security risk, any contract or address can be chosen as a maintainer. However, it is always best to DYOR.
* Maintainers can not steal Pool fees or Pool funds.

{% content-ref url="maintainers.md" %}
[maintainers.md](maintainers.md)
{% endcontent-ref %}

### Bound Liquidity Pools - optional

* **If you don't need liquidity, your pool doesn't need a bound liquidity pool.**
* **You can always change your mind later.**

{% content-ref url="../bound-liquidity-pools.md" %}
[bound-liquidity-pools.md](../bound-liquidity-pools.md)
{% endcontent-ref %}
