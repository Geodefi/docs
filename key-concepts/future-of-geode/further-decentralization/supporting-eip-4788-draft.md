# Supporting EIP-4788 (DRAFT)

#### EIP-4788 vs EIP-4895&#x20;

[https://eips.ethereum.org/EIPS/eip-4788](https://eips.ethereum.org/EIPS/eip-4788) (WIP)

[https://eips.ethereum.org/EIPS/eip-4895](https://eips.ethereum.org/EIPS/eip-4895) (CFI for Shanghai Update)

There are currently two possible methods suggested for Withdrawal Operations on the Beacon Chain.

4788, is a version that supports trustless withdrawals from Smart Contracts living in the Execution Layer. This provides ease to the staking pools, however it is not going to be live soon.

4895, is a version that only allows withdrawals when Operator triggers. This is not so trustless as there is no way to enforce the validator. However, currently this is the version to be implemented.

#### Geode supports withdrawals with EIP 4895 and will support EIP-4788 when it is ready.

* Operator withdraws remotely with a key, without any limits other than validator timeline stated when it is created.
* Funds emerges within "**withdrawalContract**" of the Pool, without triggering the fallback.

Since it is not trustless to handle all this operation, currently we are optimizing it further and preparing for the EIP-4788.

However, it is not coming soon.
