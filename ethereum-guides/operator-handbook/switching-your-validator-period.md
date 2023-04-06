# Switching Your Validator Period

## Changing Your Validator Period

Your validator Period can be 90 - 1825 days, and should be defined in seconds.

```javascript
const new_period_in_days = <x> * 24 * 60 * 60;
await Portal.switchValidatorPeriod(id, new_period_in_days)
```

{% hint style="info" %}
#### 3 Day Rule

When a Operator's period is changed, it takes 3 days for new period to take effect.&#x20;

<mark style="color:blue;">Within this 3 day time span, the period can not be changed again.</mark>

However, you can stop proposing new validators before your cool-down period ends.
{% endhint %}
