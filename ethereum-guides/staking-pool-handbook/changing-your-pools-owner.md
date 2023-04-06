# Changing Your Pool's Owner

## <mark style="color:purple;">CONTROLLER</mark>

The "**CONTROLLER**" key stands for the owner of the ID of a given staking pool.

### Who Is the Current Owner?

```javascript
 const getBytes32 = (key) => {
    return ethers.utils.formatBytes32String(key);
  };

const owner = Portal.readAddressForId(id, getBytes32("CONTROLLER"))
```

### Set a New Owner

#### 1. Which address is the new owner?

This might be a developer's address, a developers' multisig, or a token address.&#x20;

#### <mark style="color:red;">2. Double check the address of your new Controller.</mark>

#### 3. Call `changeIdCONTROLLER()` in Portal with the ID of your Pool, and the address of your new Controller.&#x20;

```solidity
Portal.changeIdCONTROLLER(uint256 id, address newCONTROLLER)
```

#### 4. Change the Owner of Your Withdrawal Contract

Since the Withdrawal Contracts do not trust Portal, you will need to transfer its ownership as well.

```javascript
const getBytes32 = (key) => {
    return ethers.utils.formatBytes32String(key);
};

const wcAddress = Portal.readAddressForId(id, getBytes32("withdrawalContract");

await wcAddress.changeController(newController);
```

{% hint style="danger" %}
<mark style="color:red;">If your Pool's Owner is not the Withdrawal Pool's Owner, it will go into</mark> <mark style="color:red;"></mark><mark style="color:red;">**Recovery Mode**</mark> <mark style="color:red;"></mark><mark style="color:red;">until you change it's ownership:</mark>
{% endhint %}

{% content-ref url="../../key-concepts/withdrawal-contracts/recovery-mode.md" %}
[recovery-mode.md](../../key-concepts/withdrawal-contracts/recovery-mode.md)
{% endcontent-ref %}

#### Changing your Controller is easy, however it will override the ability of the previous Controller <mark style="color:red;">immediately</mark>.&#x20;

{% hint style="danger" %}
<mark style="color:red;">**After changing your CONTROLLER, you will not be able to take this action back by using your old CONTROLLER address.**</mark>
{% endhint %}
