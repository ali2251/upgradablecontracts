# Proxy with Unstructured Storage

Unstructured storage is implemented by Zeppelin and they have the best [docs](https://docs.zeppelinos.org/docs/pattern.html) around it.

The basic idea is to store the address of delegated contract in a random place in memory, this works because the possibility of clash is negligible and no one ever has to care about the memory pointer for the address.

Update the proxy implementation to unstructured storage.

{% hint style="info" %}
Use inline assembly and opcodes for storing and retrieving data from the contract
{% endhint %}



