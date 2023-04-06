# Changing an Operator's Owner

## <mark style="color:purple;">CONTROLLER</mark>

"**CONTROLLER**" key stands for the owner of the ID of a given Operators.

### Who Is the Current Owner?

<pre class="language-javascript"><code class="lang-javascript"><strong>const getBytes = (key) => {
</strong> return Web3.utils.toHex(key);
};

const owner = Portal.readAddressForId(id, getBytes("CONTROLLER"))
</code></pre>

### Set a New Owner

#### 1. Which address is the new owner?

This might be a developer's address, a developers' multisig, or a Token address.&#x20;

#### <mark style="color:red;">2. Double check the new address of your Controller.</mark>

#### 3. Call `changeIdCONTROLLER()` in Portal with ID of your Operator, and the address of your new Controller.&#x20;

```solidity
Portal.changeIdCONTROLLER(uint256 id, address newCONTROLLER)
```

#### Changing your Controller is easy, however it will override the ability of the previous Controller <mark style="color:red;">immediately</mark>.&#x20;

{% hint style="danger" %}
<mark style="color:red;">**After changing your CONTROLLER, you will not be able to take this action back by using your old CONTROLLER address.**</mark>
{% endhint %}
