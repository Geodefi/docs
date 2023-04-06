# 🪙 Staking Derivatives

#### Simple.

When a user stakes their collateral, they are given a corresponding amount of a derivative.

The sole purpose of this derivative is to increase its value over time, representing the yield acquired from the staking operations.

After the Shanghai Upgrade on Ethereum goes live, these derivatives can be used to claim the corresponding Ether.

Thus, completing its mission of rewarding the staker.

#### Not so simple.

Unfortunately, Staking Derivatives differ tremendously from each other.

* **Status of the Derivative**: This can be a number in a database, an upgradable ERC20, an immutable and open-source one, etc.
* **Security of the Principal**: Withdrawal keys can be lost, databases can be hacked, contracts can be attacked.&#x20;
* **Quality of the Pool Operations:** it can be expensive to maintain your smart contracts in an ever-changing environment.
* **Quality of the Node Operations**: Decentralized Operators, Industrial Operators, Pooled Operators, etc.
* **The Percentage of the Backed Collateral**: Some derivatives allow synthetic minting, meaning it isn't even 100% backed, while others are backed more than 100%.
* **Legal Obstacles:** Obviously an increasing problem.

{% hint style="info" %}
### "Liquid" Staking Derivatives

Staking Derivatives that are represented with ERC20 tokens, which can then be used within DeFi.&#x20;

Can be issued by anyone, without any premise.
{% endhint %}

## G-Derivatives: gETH and gAVAX

### Establishing a Secure, Global Standard.

#### G-derivatives are <mark style="color:purple;">**immutable ERC-1155 contracts**</mark> that are utilized for internal accounting within Geode's staking library.

The Staking Library defines it's operations by way of this ERC-1155 contract.&#x20;

Since it is immutable, this contract ensures the underlying balance of the staked asset without any possibility of alteration.

Users, and approved contracts, can manage and transfer their tokens directly or via interfaces.

With a little magic, they can even be used in other forms; such as ERC20!

Thus allowing any Staking Derivative to be a <mark style="color:purple;">Liquid</mark> Staking Derivative.

{% hint style="success" %}
Using a single ERC1155, instead of multiple ERC20s, provides better DeFi compatibility in the future. For example, A DeFi app can onboard all Geode-hosted derivatives at once, without tracking and updating multiple token addresses.
{% endhint %}

## Let's dive in

G-Derivatives are _Databases_ of <mark style="color:purple;">Balances</mark> and <mark style="color:purple;">Prices</mark> with extra <mark style="color:purple;">Scalability (interfaces).</mark>

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2Fer1zzrzebhprc2IWX2y9%2Fuploads%2FrD3jpCVkEu0b0sOf5ktZ%2FgDer.png?alt=media&#x26;token=a1c3cda2-1bd3-4d1a-8714-86b5069eb9bc" alt=""><figcaption></figcaption></figure>

{% content-ref url="g-derivatives/" %}
[g-derivatives](g-derivatives/)
{% endcontent-ref %}
