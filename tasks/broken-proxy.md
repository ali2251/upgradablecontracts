# Broken Proxy

Try this:

```text
contract Proxy {
    
    address public implementation;
    
    function setAddress(address a) external {
        implementation = a;
    }
    
    function () external payable {
        address impl = implementation;
         assembly {
    let ptr := mload(0x40)
    calldatacopy(ptr, 0, calldatasize)
    let result := delegatecall(gas, impl, ptr, calldatasize, 0, 0)
    let size := returndatasize
    returndatacopy(ptr, 0, size)

    switch result
    case 0 { revert(ptr, size) }
    default { return(ptr, size) }
 }
        
    }
    
}

```

And use this contract to delegate to:

```text
contract Score {
    uint public score;
    
    function setScore(uint _score) external {
        score = _score;
    }
}
```

Fix this contract.

Try This

```text
contract Score {
    bytes32 myHash = keccak256("This is awesome");
    uint public score;
    
    function setScore(uint _score) external {
        score = _score;
    }
}
```



