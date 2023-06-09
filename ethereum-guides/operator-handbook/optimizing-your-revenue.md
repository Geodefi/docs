# Optimizing Your Revenue

## Better Performing Validators Mean More Revenue

#### It is important to underline that your performance gets you profit, instead of sharing everything with the other Node Operators all the time, with linear distribution.

Other Operators do not affect you, and you do not affect other Operators.

You will only get fees from the generated capital your validators provide.

By providing better returns, more market participants will choose to create validators with you.

Outperform the other Operators, and get more validators!&#x20;

### Use MEV&#x20;

{% hint style="success" %}
<mark style="color:green;">Node Operators also collect the same percentage of fees from the rewards / MEV profit from their validators!</mark>
{% endhint %}

You can get up to 10% of the MEV revenue and block rewards generated by your validators.

#### Node Operators need to provide the appropriate fee recipient for the block rewards and MEV profits.

Unlike other staking pools, which pools the MEV and block rewards directly, or even uses it to create more validators instantly; Geode sets them aside in a contract called `WithdrawalContract`.&#x20;

Every staking pool has a `WithdrawalContract`.

So, for every validator, there is a distinct address that comes from its origin Pool:

```javascript
Portal.readAddressForId(id, getBytes("WithdrawalContract"));
```

{% hint style="danger" %}
<mark style="color:red;">Fee theft is detected with Telescope...</mark>
{% endhint %}

### Lower Your Fees

Geode is a competitive marketplace, and you might attract more validators if you lower your fees.

### Lower Your Validator Period

By promising a faster return, you can attract more validators.
