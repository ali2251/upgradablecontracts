# Proxy with Inheritance

## Task 5

* Implement a basic Proxy contract which has the following code in its fallback function

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
 
 *https://blog.zeppelinos.org/proxy-patterns/
```

* Add functions to Proxy for setting the delegated address and getting the delegated address
* Implement the Score contract as before and use the Proxy contract with remix 
* Implement ScoreV2 and change the proxy address to point to that



![Safe approach](https://lh4.googleusercontent.com/r6cOMmtWFupuiZ-jUfLbijGZTlY4dhArik3rEo5NKk5Q15M9k9EnZ_TyrXCoBzhvwGebA6LCkeDdXOg50g3jAJCnVNCe09bSOHcuDqIWS7btC8jCyYDdsAsybcKbqRk5Ki6JzxZJtA)



