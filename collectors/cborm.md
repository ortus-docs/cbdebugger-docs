---
description: Profile all cborm queries
---

# CBORM

The `cborm` collector can be activated if you are using the ColdFusion ORM and our cborm module.  It will then track all calls made with criteria queries, query executions and much more.

```cfscript
cborm   : { enabled : false, expanded : false, logParams : true }
```

### Configuration

<table><thead><tr><th width="149">Key</th><th width="120">Type</th><th width="147">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><code>enabled</code></td><td>Boolean</td><td>false</td><td>Enable the collector</td></tr><tr><td><code>expanded</code></td><td>Boolean</td><td>false</td><td>Expand the panel by default or not</td></tr><tr><td><code>logParams</code></td><td>Boolean</td><td>true</td><td>Log the binding query parameters</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/SCR-20230616-nrsx.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/SCR-20230616-nrud.png" alt=""><figcaption></figcaption></figure>
