# Versioning with Registry

The only difference with this is that given the company is not malicious, we can have versioned contract which all work simultaneously, \(How cool is that!\). Implementing this pattern is just like extending proxy, we add another contract called Registry \(non-upgradable\), and the proxy will call the registry to get the address to delegate to for a particular user and delegate accordingly. 

![](https://lh4.googleusercontent.com/7xC1BDVdZX573BgTsq20iJXANFooFLuNYwFJhUU1K6RHDBBpAAmk_DwQCf2Yso5Ud0E2itNMRcyaIYbA1ZT9TtqDIkLCpuzpvDuflW_vXR4tzhj2t3f7q3YhpoZYh740sQ-JeZjnYQ)

 

