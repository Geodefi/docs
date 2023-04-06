# Manage Your Maintenance Fee

#### Changing your fee doesn't affect the previously created validators!

Learn more about the Maintenance Fee:

{% content-ref url="../../operator-marketplace/maintenance-fee.md" %}
[maintenance-fee.md](../../operator-marketplace/maintenance-fee.md)
{% endcontent-ref %}

## Changing Your Fee

```javascript
const new_fee = x * 10**10 /100 // x%

await Portal.switchMaintenanceFee(id, new_fee)
```

{% hint style="info" %}
#### 3 Day Rule

When a Pool's fee is changed, it takes 3 days for new fee to take effect.&#x20;

<mark style="color:blue;">Within this 3-day period the fee cannot be changed again.</mark>

This applies to Operator Fees as well, and prevents misleading behavior within our marketplace.
{% endhint %}

## Claiming Your Fees

#### Internal Wallet

Every ID has an Internal Wallet, which makes transferring Ether easier for both Geode's Portal, and it's users.

The Internal Wallet is the place where your fees will accrue over time.

```javascript
const wallet_balance = Portal.readUintForId(id, getBytes("wallet"));

await Portal.decreaseWalletBalance(id, wallet_balance);
```
