---
description: An overview of the different methodologies for upgrading smart contracts
---

# Overview

Now that we know what smart contract upgradability is, we can look at different ways that Ethereum Smart Contracts are Upgraded.

#### **Migration**

The contract is deployed without thinking about upgradability~~\*~~ and when new features needs to be added, a new contract is deployed and the data is migrated from the old contract to the new contract manually. The advantage of this method is that the entire contract can be rewritten without any regard for how the original contract was written, the disadvantage being that the data has to manually transferred to the new contract which includes a lot of potential for error and security implications. 

For example, Imagine you are updating a standard [ERC20](https://en.wikipedia.org/wiki/ERC-20) contract which has a mapping of balances, doing migration its very much possible that balances are assigned wrong or the company maliciously steal the users funds.

#### Upgrade

An upgrade is a mechanism through which the data is kept while updating the logic of the contract, there are many patterns through which an upgrade can be achieved. The main implications of an upgrade is the friction it introduces to the users, for example, a migration causes all the users to start using a different contract and verify that their funds are safe, however; there are approaches which lets the company do an upgrade without the user having to update the address but it does add the trust factor.

There are the following known methodologies for updating smart contracts:

* Keeping the data and logic separately
* Keeping the data and logic separately via Eternal Storage
* Permissionning system
* Proxy 
  * Proxy with Eternal Storage 
  * Proxy with Unstructured Storage



