# Using Maintainers

### Why Use Maintainers?

For an Operator, ownership and maintenance are two tasks with different risk factors.

#### To make things easier for you, we've introduced Maintainers:

A special address that has limited capabilities.

#### Keep the ownership of your Operator safe with a multisig setup, while allowing a script to automate your daily tasks.

Learn more about them here:

{% content-ref url="../../key-concepts/permissionless-configurable-staking-pools/maintainers.md" %}
[maintainers.md](../../key-concepts/permissionless-configurable-staking-pools/maintainers.md)
{% endcontent-ref %}

### Setting Your Maintainer

You can set any address as your maintainer, <mark style="color:red;">but it is not safe to trust random addresses!</mark>

You will be held responsible for faulty validator proposals, and other mistakes that your maintainer makes.

```javascript
Portal.changeMaintainer(id, newMaintainer);
```
