# Keeping Data and Logic Separately via Eternal Storage

Eternal Storage means to define all possible data types such that no more types will be needed in the future. Lets take an example of storing unsigned integers \(uint\), if we can give a unique name to every uint we want to store then we can store as many uint's as we want as long as we keep giving them unique names and an efficient way to achieve this is through `mapping` where the key is `bytes32`. The `bytes32` comes from taking `keccak256(UNIQUE_NAME)` where `UNIQUE_NAME` is the name we want to call our variable which stores a `uint`

```text
string score = "score";
bytes32 hash = keccak256(score);

mapping(bytes32 => uint) uintStorage
```

Following this pattern, the eternal storage can be implemented by mappings for each data types as follows:

```text
  mapping(bytes32 => uint256) internal uintStorage;
  mapping(bytes32 => string) internal stringStorage;
  mapping(bytes32 => address) internal addressStorage;
  mapping(bytes32 => bytes) internal bytesStorage;
  mapping(bytes32 => bool) internal boolStorage;
  mapping(bytes32 => int256) internal intStorage;
  
  Taken from: https://github.com/zeppelinos/labs/blob/master/upgradeability_using_eternal_storage/contracts/EternalStorage.sol
```

Each of these types can be used with Logic Contract keeping a track of all variable names it uses to store the values. The eternal storage contract is completely agnostic to the actual values keys which are used, for example, if a value is no longer needed, the logic contract can stop referencing the value and instead use a new variable name for it. 



![Figure 4](https://lh4.googleusercontent.com/pBczexYzFxab-flF3w2xpdpumbbE8wQdqX4tt_Wkp1hoVPpCKXYy3NDxwdGgaJ0mQQLTemi3fgsHU0OJBVUHTF6WkYYwdAJnJWh_Vbi0PFX-WbExNttbCgn_NFwF-dfPwnUYk5XSWQ)



{% hint style="info" %}
This pattern can be used in the exact same way as Keeping data and logic separately, however the complexity of implementing the same approach in this is significantly higher and mistakes are much more likely. 
{% endhint %}

