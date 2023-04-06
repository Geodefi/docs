# 🌀 Portal

## The Staking Gateway

**Geode Finance utilizes a Modular Architecture, making things **<mark style="color:purple;">**safer**</mark>** for stakers, and **<mark style="color:purple;">**easier**</mark>** for Pool Providers**.

<figure><img src="../../.gitbook/assets/geodeLibrary.png" alt=""><figcaption></figcaption></figure>

#### The most crucial component is The Portal.

* Creation and maintenance of the configurable staking pools.
* Minting new tokens.
* Securing the Ether until it is staked in a validator.
* Onboarding new Operators to the marketplace.
* Management and regulation of the Operator marketplace.
* Allowing new functionalities to be implemented with ease.
* Securing it's own codebase from Governance.
* Various tasks of Oracle.

#### To achieve these tasks and improve the staking user experience for everyone:

1. We need to make sure every Staking Pool and Node Operator is isolated in a well organized storage space. We can also add new functionalities with ease:

{% content-ref url="isolated-storage.md" %}
[isolated-storage.md](isolated-storage.md)
{% endcontent-ref %}

2. We need to define the different parties that will use this storage space, in a secure and generalized way. Thereby preventing any third party access:

{% content-ref url="dual-governance.md" %}
[dual-governance.md](dual-governance.md)
{% endcontent-ref %}

3. We need to define the ownership of the funds explicitly, in a way that Portal doesn't hold any responsibility after validator creation:

{% content-ref url="../withdrawal-contracts/" %}
[withdrawal-contracts](../withdrawal-contracts/)
{% endcontent-ref %}

4. We need to create an upgradability pattern **for both Portal and Withdrawal Contracts**, so we can prevent Governance from changing these mechanisms inconveniently or maliciously.

{% content-ref url="limited-upgradability.md" %}
[limited-upgradability.md](limited-upgradability.md)
{% endcontent-ref %}

5. Now, we can implement The Staking Library. It should manage and provide a wide variety of features for the staking derivatives:

{% content-ref url="../permissionless-configurable-staking-pools/" %}
[permissionless-configurable-staking-pools](../permissionless-configurable-staking-pools/)
{% endcontent-ref %}

6. We need to have a marketplace for Pools and Operators to communicate easily:

{% content-ref url="../../operator-marketplace/" %}
[operator-marketplace](../../operator-marketplace/)
{% endcontent-ref %}

6. We need to have a generalized approach on price updates, that supports infinitely many staking pools:

{% content-ref url="../oracles/telescope-ether.md" %}
[telescope-ether.md](../oracles/telescope-ether.md)
{% endcontent-ref %}
