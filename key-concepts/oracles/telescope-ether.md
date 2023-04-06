# Telescope Ether

#### Telescope-Ether currently has 3 responsibilities:

## Reporting the Derivative Prices

Oracle updates the Price **Merkle Root** at least once a day and possibly more frequently.

1. All validator pub-keys of a pool are stored in Portal.
2. Oracle fetches all the pub-keys and validator specific details like fee etc.
3. Total Ether amount is calculated from the validator balances, and claimable portion of the Withdrawal Contract balance.
4. Total of the Fee is deducted from the total Ether.
5. New price is calculated with respect to totalSupply.
6. A Merkle Tree is created containing all the prices of all the pools.
7. A Merkle Root of the Merkle Tree is sent to Portal by Oracle.
8. Anyone can sync prices of the derivative to the Oracle price with valid proofs collected from watchers.
9. Updated price will be valid for the **next 24 hours, or until the next Merkle Root update**.

> Derivative prices can be synced by anyone with the correct Merkle Proofs.&#x20;

> A valid price is required whenever a deposit or a withdrawal operation is requested.

## Updating the Verification Index

Operators can create new validators on behalf of a staking pool, up to the allowance amount set by the maintainer of the pool.

Validator creation is a 3 step process:

1. Validator Proposal
2. Proposal Verification
3. Pooled Staking

Every validator has a unique index **`(0:n]`**

Oracle verifies the proposed validator pub-keys by simply stating the latest verified index.&#x20;

While doing so, the faulty proposals that have a lower index than the new verificationIndex are excluded.

{% hint style="danger" %}
These faulty proposals are called **aliens** and this pubkeys can not be ever used again.
{% endhint %}

## Regulating the Operator Marketplace

#### Alienation

Alienation process results in Node Operator being imprisoned for the next 14 days, meaning it can not access to the Portal at all.

#### All possible reasons of alienation:

* [Withdrawal credential frontrunning](https://bit.ly/3Tkc6UC)
* Faulty sig1
* Faulty sig31
* Stealing the block rewards from staking pools. Obviously this causes imprisonment.
* Validator is not exited by Operator although the `expectedExit` has past. Anyone can blame a validator and effectively imprison the Operator until the exit happens.
