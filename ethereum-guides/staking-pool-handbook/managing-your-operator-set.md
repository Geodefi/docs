# Managing Your Operator Set

## Choose Freely!

Assume your balance is the number of validators within your pool.&#x20;

Your maintainer will be giving allowances to the Node Operators, and meanwhile, the Node Operators will compete to get as many validators as possible.

You can think of it as ERC-20 approvals. You are approving a certain amount of validators to be run by a Node Operator.

```javascript
Planet.approveOperators(
         poolId,
         [operatorIds],
         [allowances]
    );
```

### How To Choose?

There are number of factors to pay attention to while choosing your Node Operators:

* Choose Operators with lower fees, but make sure to consider whether they'll be sufficient for the task.
* Do not centralize around one, or even a few Operators -- try to spread your risk of being slashed as much as possible.
* Pay attention to **validatorPeriod** parameter of the Operators:
  * **A shorter period means better peg protection, and happier stakers.**
  * **A longer period means better yields.**
* Consider how many validators are they already running within Geode. Too many? Too little? Do your bit for validator diversification.
