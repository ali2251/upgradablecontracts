# Proxy

The most famous pattern to be discussed within the Ethereum community, all the patterns which we have discussed so far have a disadvantage that the **`address`**changes every time an upgrade is carried out, this means that all users have to be aware of the current version of the contract, which isn't feasible a lot of the time, for example, if a user was offline for 2 months, he wouldn't know how many upgrades have happened and what the latest version of the contract is, hence the scams can jump in and steal users funds. 

The proxy pattern provides a common ground \(`address`\) regardless of the number of upgrades, but an important thing to note is that it adds a lot of **trust** on the company doing the upgrade honestly, it is often argued that the owner of the proxy can be a multi-signature wallet held by the company but it still means that `m of n`trusted members needs to collude to perform a dishonest upgrade which again, isn't great.

The proxy works by utilising `delegatecall` function from EVM which in simple words lets a contract use some logic from another contract but using its own storage. In other words:

| identical to `callcode` but also keep `caller` and `callvalue` |
| :--- |
| [https://solidity.readthedocs.io/en/v0.5.4/assembly.html?highlight=delegatecall](https://solidity.readthedocs.io/en/v0.5.4/assembly.html?highlight=delegatecall) |

![Figure 5](.gitbook/assets/image%20%282%29.png)

When a user calls V1 contract through proxy, the `msg.sender`of v1 is not the Proxy but the actual user who initiated the call, this is because the `msg.sender and msg.value` is passed along with the delegatecall and any state mutations done in V1 contract will actually be stored in Proxy.



![Figure 6](.gitbook/assets/image%20%283%29.png)



To perform an upgrade, all that the proxy has to do is just point to the new address \(V2\) and now all users will access the new version of the contract without having to change anything. This opens up a lot of interesting possibilities because the upgrades can be performed seamlessly, however there are limitations of the proxy contract, such as the storage layout of the contract should not be modified and if its done, then the storage will be corrupted, leaving you to start again. 

![Figure 7](https://lh4.googleusercontent.com/r6cOMmtWFupuiZ-jUfLbijGZTlY4dhArik3rEo5NKk5Q15M9k9EnZ_TyrXCoBzhvwGebA6LCkeDdXOg50g3jAJCnVNCe09bSOHcuDqIWS7btC8jCyYDdsAsybcKbqRk5Ki6JzxZJtA)

So far, we have only talked about structure, let's see how it looks in practice.

```text
 assembly {
    let ptr := mload(0x40)
    calldatacopy(ptr, 0, calldatasize)
    let result := delegatecall(gas, _impl, ptr, calldatasize, 0, 0)
    let size := returndatasize
    returndatacopy(ptr, 0, size)

    switch result
    case 0 { revert(ptr, size) }
    default { return(ptr, size) }
 }
```

{% hint style="danger" %}
Be careful about using the proxy pattern, it requires specialised knowledge and understanding of the EVM
{% endhint %}



