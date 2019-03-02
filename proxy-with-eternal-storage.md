# Proxy with Eternal Storage

Proxy with eternal storage is pretty much the same as a normal proxy, except the contract it delegates to is an Eternal storage contract which we saw earlier, Nothing changes in the proxy contract. 

{% hint style="danger" %}
This is by far the most complex way to upgrade contracts and the documentation around it is quite tricky to understand, only use this approach if you can simplify the implementation and handle things properly and that may pay in the long run.
{% endhint %}

