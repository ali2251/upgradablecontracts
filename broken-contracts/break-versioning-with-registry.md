# Contracts To Hack

## Contract 1

```text
contract G_GAME
{
    function Play(string _response)
    external
    payable
    {
        require(msg.sender == tx.origin);   
        msg.sender.transfer(this.balance);
    }
    
    string public question;
    address questionSender;
    bytes32 responseHash;
 
    function StartGame(string _question,string _response)
    public
    payable
    {
        if(responseHash==0x0)
        {
            responseHash = keccak256(_response);
            question = _question;
            questionSender = msg.sender;
        }
    }
    
    function StopGame()
    public
    payable
    {
       require(msg.sender==questionSender);
       msg.sender.transfer(this.balance);
    }
    
    function NewQuestion(string _question, bytes32 _responseHash)
    public
    payable
    {
        require(msg.sender==questionSender);
        question = _question;
        responseHash = _responseHash;
    }
    
    function() public payable{}
}

*https://medium.com/coinmonks/an-analysis-of-a-couple-ethereum-honeypot-contracts-5c07c95b0a8ds
```



## Contract 2

Be a malicious company and steal funds from this contract by any means

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



