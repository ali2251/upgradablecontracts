# Keeping data and logic separately

## Task 2

Using the same logic as the previous exercise, we will build the same Score contract but by keeping the data and logic separately.

1. Implement the data contract which stores uint for score
2. implement the logic contract which uses the data contract
3. Deploy the contracts and test that you can update the value of score
4. Implement LogicV2 contract which as before updates the `setter` function such that it adds 1 to the value being set
5. Perform the upgrade and disable logicV1 contract
6. Do the above 6 steps but for a simple token contract

## Additional Tasks

* Extend the Storage contract with StorageV2 which calls Storage to access the old storage and for any new storage, keeps it within itself
* Extends StorageV2 with StorageV3 which either talks to both Storage and StorageV2 or Just talks to Storage.
* Use inheritance to support extending the contract and override the functions to call super contract if function not changed in this implementation  

