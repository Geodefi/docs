# ⛏ Maintainers

#### Allowance

The Operator Marketplace works with `Allowances` and `Approvals`, like ERC20.

Every 32 ETH represents 1 validator, 1 balance.

Staking Pools can approve any subset of Node Operators for any amount of validators.

Node Operators can create any number of validators for the mentioned pool, up to their allowance.

While simple, and conventional, this task can be a burden for bigger Staking Pools.

Furthermore, this logic can be easily automated and not require any further user interaction.

### These Automators Are Called <mark style="color:purple;">Maintainers</mark>

The pool's owner, a script, smart contract, or a third party can be the maintainer of a pool.

Setting a maintainer is easy, and doesn't require anyone's approval other than the Staking Pool Owner.

Every Pool can have 1 Maintainer.

### It Is Safe To Trust Any Maintainers As They Don’t Have Many Permissions

* <mark style="color:green;">Can set validator allowance.</mark>
* **Can not** change pool status to private/public.
* **Can not** set a whitelist.
* **Can not** deploy a liquidity pool.
* **Can not** access to stakers' funds.
* **Can not** claim any fees.
* **Can not** switch MaintenanceFee.
* **Can not** change Maintainer.
* **Can not** change Controller.

## Node Operators Can Use Maintainers Too

A Node Operator on the Marketplace is owned by its Controller.&#x20;

But again, Staking Operations can be easily automated.

* <mark style="color:green;">Can switch Validator Period.</mark>
* <mark style="color:green;">Can propose new validators.</mark>
* <mark style="color:green;">Can stake to beacon.</mark>
* **Can not** claim any fees.
* **Can not** switch MaintenanceFee.
* **Can not** change Maintainer.
* **Can not** change Controller.
