# Private Pools and Whitelisting

{% hint style="success" %}
<mark style="color:green;">You can configure your pool as Public or Private on creation. However, pool owners can change this status easily.</mark>
{% endhint %}

#### Public Pools can be used by anyone

If you are a service provider willing to manage anyone's Ether, create a Public Pool.&#x20;

{% hint style="success" %}
<mark style="color:green;">Public Pools will show up within on Geode's App.</mark>
{% endhint %}

#### Private Pools can only be used by whitelisted addresses

If you are using a personal staking pool, or worried about KYC/AML, create a Private Pool.

{% hint style="success" %}
<mark style="color:green;">Private Pools do</mark> <mark style="color:green;"></mark><mark style="color:green;">**not**</mark> <mark style="color:green;"></mark><mark style="color:green;">show up on Geode's App.</mark>
{% endhint %}

### Making Your Pool Public

```javascript
Portal.setPoolVisibility(id, false);
```

### Making Your Pool Private

```javascript
Portal.setPoolVisibility(id, true);
```

### Whitelisting

#### You can use a whitelist to manage staker addresses on Private Pools

But you don't need to.

{% hint style="success" %}
<mark style="color:green;">A Pool Owner is able to use their private Pool without being whitelisted.</mark>
{% endhint %}

This whitelist should be a contract that has implemented **isAllowed()** function:

{% code title="IWhiteList.sol" %}
```solidity
interface IWhiteList {
  // @notice returns true if the address is allowed
  function isAllowed(address) external view returns (bool);
}
```
{% endcode %}

After making your pool private and creating your whitelisting contract with required functionality, simply notify Portal:

```javascript
Porta.setWhitelist(id, contract_address);
```

> Here is an **unupgradable** ,**unaudited**, **untested, simple** Whitelist contract for you 💕

```solidity
pragma solidity =0.8.7;

import "@openzeppelin/contracts/access/Ownable.sol";

interface IWhiteList {
  // @notice returns true if the address is allowed
  function isAllowed(address) external view returns (bool);
}

contract Whitelist is IWhitelist, Ownable {
  event Listed(address indexed account, bool isWhitelisted);

  mapping(address => bool) private whitelist;

  function isAllowed(
    address _address
  ) external view virtual override returns (bool) {
    return whitelist[_address];
  }

  function setAddress(address _address, bool allow) external virtual onlyOwner {
    require(whitelist[_address] != allow);
    whitelist[_address] = allow;
    emit Listed(_address, allow);
  }
}
```
