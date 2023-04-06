# Initiating a Customizable Staking Pool

## Before Initiation:

### 32 Ether

Creating a Pool is **permissionless**, anyone can claim any pool name.

To prevent sybil attacks, initiation requires **exactly 1 validator worth of funds**. However, you can **deposit more Ether later.**

However, this amount will be used to create your first validator.

### Pool ID

Every Pool will have a **unique** ID.

It will be used for your Pool operations, and you can find your ID from both our frontend or Portal.

```javascript
const pool_ID = Portal.generateId(pool_name, 5);
```

### Maintainers

Maintainers are useful to automate pool owners' daily tasks, such as choosing your Node Operators.

{% content-ref url="../../key-concepts/permissionless-configurable-staking-pools/maintainers.md" %}
[maintainers.md](../../key-concepts/permissionless-configurable-staking-pools/maintainers.md)
{% endcontent-ref %}

## Initiate Your Pool!

Geode uses an initiator function to set some parameters for your staking pool and derivative.

```javascript
Portal.initiatePool(
    NAME,
    fee,
    interfaceVersion,
    maintainer,
    interface_data,
    config,
    {value: 32 Ether}
);
```

1. **NAME**: Unique name of your Pool. <mark style="color:red;">Can not be changed later.</mark>
2. **FEE**: Maintenance fee that will be charged for your services as the pool owner. 10^10 represents 100%, can be set to up to 10% (10^9). <mark style="color:blue;">Can be changed later.</mark>
3. **Interface Version**: Can be empty, or can be any interfaces from the list below. <mark style="color:red;">Can not be changed later.</mark>

{% content-ref url="../../key-concepts/permissionless-configurable-staking-pools/current-interfaces.md" %}
[current-interfaces.md](../../key-concepts/permissionless-configurable-staking-pools/current-interfaces.md)
{% endcontent-ref %}

4. **Maintainer**: Any other address that will manage your pool's Node Operators. Can be a community owned Maintainer, or the address of an automation script, etc. <mark style="color:blue;">Can be changed later.</mark>
5. **Interface Data**: some interfaces require data to be present along with a gETH address and Pool id.
6. **Config**: initial configuration of your Pool as:
   1. **True** if a private pool - <mark style="color:blue;">Can be changed later.</mark>
   2. **True** if uses an interface<mark style="color:blue;">.</mark> <mark style="color:red;">Can not be changed later.</mark>
   3. **True** if uses a liquidity Pool - <mark style="color:blue;">Can be changed later.</mark>

{% hint style="info" %}
Note that, if you create private pool, you will need to create a Whitelisting Contract and register it.

However, Pool CONTROLLERs are allowed to use the pool even without creating and registering a contract.&#x20;
{% endhint %}

{% content-ref url="private-pools-and-whitelisting.md" %}
[private-pools-and-whitelisting.md](private-pools-and-whitelisting.md)
{% endcontent-ref %}

### Example of Pool Creation Transaction

### Basic Pool Initiation

The below transaction creates a **Private** Staking Pool with **no maintenance fee**_**,**_ **no interface**, and **no Liquidity Pool**:

<pre class="language-javascript"><code class="lang-javascript">// Pool
const your_address="0xabcdf....abcdf";
const pool_name= "IceBear's Pool";

// send the transaction
<strong>Portal
</strong>    .initiatePool(
        0,
        0,
        your_address,
        pool_name,
        "0x",
        [true, false, false])
    .send({
        value: String(32e18),
    });

pool_ID = Portal.generateId(pool_name, 5);
</code></pre>

### Complex Initiation

The below transaction creates a **Public** Staking Pool with a **5% maintenance fee**, and **ERC20InterfacePermitUpgradable** interface, which also has a bound **Liquidity Pool**:

```javascript
const getBytes = (key) => {
  return Web3.utils.toHex(key);
};

const intToBytes32 = (x) => {
  return ethers.utils.hexZeroPad(ethers.utils.hexlify(x), 32);
};


// EDIT HERE
// Pool
const your_address="0xabcdf....abcdf";
const pool_name= "IceBear's Pool";
const pool_fee = 5 // 5%
// interfaces = ["ERC20", "ERC20Permit"];
const interface_version = "ERC20Permit";
const interface_name = "IceBear Staked Ether";
const interface_symbol= "IETH"
// Config
const is_private_pool = false;
const use_interface = true;
const use_liquidity_pool = true;
// EDIT HERE



// DO NOT TOUCH HERE
const name_bytes = getBytes(interface_name ).substr(2);
const symbol_bytes = getBytes(interface_symbol).substr(2);
const interface_data =
  intToBytes32(nameBytes.length / 2) + nameBytes + symbolBytes;
const interface_id =  await Portal.generateId(interface_version, 31);
const denominator=10 ** 10;
await Portal
    .initiatePool(
    Math.floor((pool_fee * denominator) / 100),
    interface_id,
    deployer.address,
    getBytes(pool_name),
    interfaceData,
    [is_private_pool , use_interface , use_liquidity_pool ],
    {
      from: deployer,
      log: true,
      value: String(32e18),
    },
  );
  
  const pool_ID = Portal.generateId(pool_name, 5);
  console.log("your pool id:", pool_ID);
```
