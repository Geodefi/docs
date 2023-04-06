# gETH vs gAVAX

#### Improvements to G-Derivatives resulted in some differences between these two ERC1155 contracts.

## <mark style="color:blue;">Avoiders</mark>

gAVAX is developed with the assumption that the staker would choose which Staking Pool to stake with. However, it is not hard to see that when people start building on top of Geode, they might want to avoid this assumption.&#x20;

_Avoiders_ simply prevent the effect of any Interfaces on their g-derivative balance. For example, they can not use their token as an ERC20, as they can not use the ERC20-interface to communicate with the ERC1155 contract.&#x20;

```solidity
/**
* @notice Mapping of user addresses who chose to restrict the usage of interfaces
**/
mapping(address => bool) private _interfaceAvoiders;

function isAvoider(address account) public view virtual returns (bool) {
   return _interfaceAvoiders[account];
}

/**
* @notice One can desire to restrict the affect of interfaces on their gETH,
* this can be achieved by simply calling this function
* @param isAvoid true: restrict interfaces, false: allow the interfaces,
**/
function avoidInterfaces(bool isAvoid) external virtual {
   _interfaceAvoiders[_msgSender()] = isAvoid;
   emit InterfacesAvoided(_msgSender(), isAvoid);
}
```

{% hint style="info" %}
gAVAX lacks this improvement.
{% endhint %}

## <mark style="color:blue;">Denominator</mark>

The ERC1155 standard does not support "decimals" natively, as ERC20 does. However, both "pricePerShare" and "Balances" need to be denominated in some way. As our auditors warned us, we did not use decimals key as it is already reserved.

```solidity
uint256 private constant _denominator = 1 ether;

/**
* @notice a centralized denominator = 1e18
*/
function denominator() external view virtual returns (uint256) {
    return _denominator;
}

```

{% hint style="info" %}
gAVAX lacks this improvement.
{% endhint %}

## <mark style="color:blue;">priceUpdateTimestamp</mark>

Some DeFi applications, such as a DWP, can be improved with the date of the latest price update from Telescope. It is logical to keep this data here, instead of Portal.

```solidity
function priceUpdateTimestamp(uint256 id) external view returns (uint256) {
    return _priceUpdateTimestamp[id];
}

function _setPricePerShare(uint256 _price, uint256 _id) internal virtual {
    _pricePerShare[_id] = _price;
    _priceUpdateTimestamp[_id] = block.timestamp; // added this line
}
```

{% hint style="info" %}
gAVAX lacks this improvement.
{% endhint %}
