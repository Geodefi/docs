# ⛑ Recovery Mode

### &#x20;All the Reasons for Recovery Mode

* Withdrawal Contract is paused by the Owner.
* Withdrawal Contract's owner is no longer the Pool's Owner.
* Withdrawal Contract needs to be upgraded to a new version.
* Withdrawal Contract is expired (not likely).

### Under Recovery Mode

{% hint style="success" %}
These operations will continue after the problem is solved, and the Withdrawal Contract has exited Recovery Mode.&#x20;
{% endhint %}

* **Withdrawal Queues and Token transfers continue as usual. 🙂**
* **No more minting** is allowed by the Portal, meaning `deposit()`calls _might_ fail.
* **No more validator proposals** can be activated, meaning `stakeBeacon()` calls _will_ fail.
