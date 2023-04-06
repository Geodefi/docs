# Switching Your Fee

#### Changing your fee doesn't affect the previously created validators!

Learn more about the Validator Lifecycle:

{% content-ref url="../../operator-marketplace/a-validators-lifecycle.md" %}
[a-validators-lifecycle.md](../../operator-marketplace/a-validators-lifecycle.md)
{% endcontent-ref %}

## Changing Your Fee

You can charge up to 10% of the pooled rewards for your _new_ validators.

```javascript
const new_fee = Math.floor(x * 10**10 /100) // x%

await Portal.switchMaintenanceFee(id, new_fee)
```

{% hint style="info" %}
#### 3 Day Rule

When a Operator's fee is changed, it takes 3 days for new fee to take effect.&#x20;

<mark style="color:blue;">Within this period of 3 days, the fee can not be changed again.</mark>

This applies to Pool Fees as well, and prevents misleading behavior within our marketplace.

However, you can stop proposing new validators before your cool-down period ends.
{% endhint %}

## Claiming Your Fees

#### Internal Wallet

Every ID has an Internal Wallet, which makes transferring Ether easier for both Geode's Portal, and it's users.

The Internal Wallet is the place where your fees will accrue over time.

```javascript
const wallet_balance = Portal.readUintForId(id, getBytes("wallet"));

await Portal.decreaseWalletBalance(id, wallet_balance);
```
