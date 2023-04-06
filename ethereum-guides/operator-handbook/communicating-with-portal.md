# Communicating with Portal

## Portal is The Main Gateway to Trustless Staking

Learn more about Portal here, if you want:

{% content-ref url="../../key-concepts/portal/" %}
[portal](../../key-concepts/portal/)
{% endcontent-ref %}

#### Portal utilizes a Modular Architecture build on top of an Isolated Storage.

This is good for us, because we can add any functionality without minding the backward compatibility. It is good for the users because no one can touch their instance of the contract storage.&#x20;

However, this means, sadly, things are not that direct...

Learn more about it here, if you want:

{% content-ref url="../../key-concepts/portal/isolated-storage.md" %}
[isolated-storage.md](../../key-concepts/portal/isolated-storage.md)
{% endcontent-ref %}

### TYPE

{% hint style="info" %}
We have already learned a bit about IDs while initiating our Operator.
{% endhint %}

There are many TYPEs that are supported by Portal. Modules like Withdrawal Contract, Liquidity Pools, Interfaces...&#x20;

However, as Node Operators, we are only interested in two of them: **Operator** and **Pool**.&#x20;

#### Representation of an Operator' storage space:

```javascript
const OPERATOR = {
"CONTROLLER": <address>,
"NAME": <bytes>,
"TYPE": 4 <uint>,
"initiated": <uint>,
"maintainer": <address>,
"totalProposedValidators": <uint>,
"totalActiveValidators": <uint>,
"feeSwitch": <uint>,
"priorFee": <uint>,
"fee": <uint>,
"periodSwitch": <uint>,
"priorPeriod": <uint>,
"validatorPeriod": <uint>,
"wallet": <uint>,
"released": <uint>
};
```

#### Representation of a Pool's storage space:

```javascript
const POOL= {
"CONTROLLER": <address>,
"NAME": <bytes>,
"TYPE": 5 <uint>,
"initiated": <uint>,
"maintainer": <address>,
"surplus": <uint>,
"secured": <uint>,
"allowance": {<OPERATOR>: <uint>},
"proposedValidators": {<OPERATOR>: <uint>},
"activeValidators": {<OPERATOR>: <uint>},
"interfaces": [<address>],
"private": <uint>, // 1 = true
"whitelist": <address>,
"withdrawalCredential": <bytes>,
"withdrawalContract": <address>,
"liquidityPool": <address>,
"liquidityPoolVersion": <uint>,
"feeSwitch": <uint>,
"priorFee": <uint>,
"fee": <uint>,
"wallet": <uint>,
"validators": [<bytes>]
};
```

> _surplus, allowance and withdrawalContract are super important for us!_&#x20;

### Reading variables from Portal

#### First, some helpers:

```javascript
const getBytes32 = (key) => {
  return ethers.utils.formatBytes32String(key);
};

const getBytes = (key) => {
 return Web3.utils.toHex(key);
};
```

#### Reading UINT variable:

```javascript
await PORTAL.readUintForId(
  id,
  getBytes32("surplus")
);
```

#### Reading ADDRESS variable:

```javascript
await PORTAL.readAddressForId(
  id,
  getBytes32("CONTROLLER")
);
```

#### Reading BYTES variable:

```javascript
await PORTAL.readBytesForId(
  id,
  getBytes32("withdrawalCredential")
);
```

### Reading Arrays from Portal

#### Reading UINT array:

```javascript
await PORTAL.readUintArrayForId(
  id,
  getBytes32("something"),
  index
);
```

#### Reading ADDRESS array:

```javascript
await PORTAL.readBytesArrayForId(
  id,
  getBytes32("interfaces"),
  index
);
```

#### Reading BYTES array:

```javascript
await PORTAL.readAddressArrayForId(
  id,
  getBytes32("validators"),
  index
);
```

### Reading Relational Data from Portal

#### Reading UINT data:

```javascript
await PORTAL.readUintForId(
  poolId,
  await PORTAL.getKey(operatorId, getBytes32("allowance"))
);
```

#### Reading ADDRESS data:

```javascript
await PORTAL.readAddressForId(
  poolId,
  await PORTAL.getKey(operatorId, getBytes32("something"))
);
```

#### Reading BYTES data:

```javascript
await PORTAL.readBytesForId(
  poolId,
  await PORTAL.getKey(operatorId, getBytes32("something"))
);
```

## <mark style="color:purple;">Thats it!</mark>
