---
description: >-
  The idea of this document is to explain all the smart contract upgrade
  mechanisms used and give detailed examples of each to help further educate and
  explore trustless upgradable mechanisms.
---

# Smart Contract Upgradability

## What is Smart Contract Upgradability?

Smart Contracts are this immutable piece of code which runs on the public chain and serves as the ultimate source of truth. The idea is that two parties agree on the rules of the game and they cant be changed, now this has many applications including decentralised exchanges, casino games and many more.

Its awesome that we can run some code which cannot be altered by anyone in the world and its a unique property which traditional servers dont provide, however in software engineering, we need to upgrade the code to fix bugs and add new features, but there seems to be a conflict between having immutable code and performing an upgrade. In this document, we will explore various different methodologies for upgrading contracts which are used by many companies today and each of them have their own advantages and disadvantages.  

{% hint style="info" %}
 Smart Contract Upgradability is in early stages and it should be used with caution
{% endhint %}



