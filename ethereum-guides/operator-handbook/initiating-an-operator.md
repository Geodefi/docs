# Initiating an Operator

### Operator ID

Every Operator has a **unique** ID.

This ID will be used to distinguish you from other entities within Geode.

```javascript
// 4? the TYPE parameter that defines Operators
const type_operator = 4; 
const pool_ID = Portal.generateId(operator_name, type_operator);
```

> Want to see all the IDs of a type?&#x20;

```javascript
const type_operator = 4; 
const type_pool = 5; 
const allIds= Portal.allIdsByType(_type, index);
// index = [0,n] : probably stop calling when you see uint256(0)
```

> What are Maintainers?

Maintainers are useful to automate an operator's daily tasks, such as creating validators!

{% content-ref url="../../key-concepts/permissionless-configurable-staking-pools/maintainers.md" %}
[maintainers.md](../../key-concepts/permissionless-configurable-staking-pools/maintainers.md)
{% endcontent-ref %}

## Initiate Your Operator!

> You can totally do this from [<mark style="color:blue;">Etherscan</mark> ](https://goerli.etherscan.io/address/0xb0334f08dec465ec180f1af04c6d7d3737407083#writeProxyContract#F15)if you want.

Portal uses an initiator function to set some parameters for your unique ID.

> <mark style="color:purple;">You can send some Ether on initiation!</mark> It will be added to your internal wallet.&#x20;
>
> Internal wallet will come handy on validator creation. Don't worry, you can take it out later.

```javascript
// EDIT THESE
const fee = 5; // 5%, [0, 10]
const validatorPeriod = 180; // 180 days, [90, 1825]
const maintainer_address= <your_address_here>;
const initial_wallet = 5e18; // you might use Bignumber.js for this one

// KEEP THESE
const denominator = 10**10;
const dayToSecond = 86400;

await Portal.initiateOperator(
    id,
    Math.floor((fee * denominator) / 100),
    validatorPeriod * 86400,
    maintainer_address,
    {value: initial_wallet }
);
```

1. **ID:** your operator ID
2. **FEE**: Maintenance fee that will be charged from validator rewards, block rewards, and MEV rewards. 10^10 represents 100%, can be set to up to 10% (10^9). <mark style="color:blue;">Can be changed later.</mark>
3. **Validator Period**: Every validator has an expiration date. Should be between 90 - 1825 days, given in seconds. <mark style="color:blue;">Can be changed later.</mark>
4. **Maintainer**: Your automation script's address. <mark style="color:blue;">Can be changed later.</mark>
