# ERC20InterfaceUpgaradable.sol

## Important changes to the ERC20 implementation

#### ERC20Interface will be using the balance info coming from gAVAX, so there is no _\_balances_&#x20;

```solidity
    /**
     * @dev gAVAX ERC20 interface doesn't use balance info, catches it from ERC1155.
     * mapping(address => uint256) private _balances;
    **/ 
    function _transfer(...) internal virtual {
        ...
        unchecked {
            _ERC1155.safeTransferFrom(sender,recipient,_id,amount,"0x00");
        }
        ...
    }
```

#### There is also a function for _pricePerShare,_ so it is easy for any code to keep track of underlying AVAX balances.

```solidity
function pricePerShare() public view returns(uint){
            return _ERC1155.pricePerShare(_id);
    }
```

#### Balance info for the used ID's ERC20interface will show the gAVAX balance info.&#x20;

```solidity
function balanceOf(address account) public view virtual override returns (uint256) {
        return _ERC1155.balanceOf(account,_id);
    }
```

#### TotalSupply info for the used ID's ERC20interface will show the gAVAX totalSupply info.&#x20;

```solidity
    /**
     * @dev gAVAX ERC20 interface doesn't use totalSupply info, catches it from ERC1155.
     * uint256 private _totalSupply;
    **/ 
    function totalSupply() public view virtual override returns (uint256) {
        return _ERC1155.totalSupply(_id);
    }
```

{% hint style="danger" %}
**Note, these code pieces should NOT be used in production.**
{% endhint %}

### See it on [Diffchecker.](https://www.diffchecker.com/0PlrxJT9)

### See it on [Github.](https://github.com/Geodefi/Portal-Avax/blob/dev/contracts/Portal/gAvaxInterfaces/ERC20InterfaceUpgradable.sol)
