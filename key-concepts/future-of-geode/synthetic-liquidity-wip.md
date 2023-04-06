# Synthetic Liquidity (WIP)

{% hint style="info" %}
Utilizing this feature will require a **Bound Liquidity Pool**.
{% endhint %}

### Why?

Synthetic Liquidity will allow less than 100% collateralization ratio to be introduced for a staking derivative.

However, Synthetic Liquidity is only created on deposits and burned on withdrawals.

This way, we can allow a continuous liquidity flow to bound liquidity pool, without creating any issues on the supply model.&#x20;

### How much?

Staking Pool Owners can set a parameter up to x% for synthetic minting.&#x20;

x is potentially between 10-25.

### Example for **10%** Synthetic Liquidity

> The price of the derivative on the following example will be 1 Ether.

1. User puts 100 Ether in Portal to be used for Staking Operations.
2. 90 Ether is added to the Pool.
   * Decreases the pool APR.
3. Portal mints 110 Ether worth of gETH, 110 gETH
   * Created tokens are not backed by any collateral.
4. 100 Ether worth of gETH is given back to staker, 100 gETH
5. 10 Ether and 10 Ether worth of gETH (10 gETH) is put into Bound Liquidity Pool.
   * Increases the Pool APR.
6. The LP tokens are given to the Withdrawal Contract.
7. When user comes back with 100 gETH, which can represent more than 100 Ether, respective LP tokens are burned, and the remaining Ether amount will be filled by Validator Withdrawals.
