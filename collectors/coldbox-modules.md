---
description: Profile ColdBox Module registration and activation
---

# ColdBox Modules

The `modules` collector can be activated and it will profile and track all of your application's ColdBox modules.  Specifically the registration and activation execution times.  You can also reload and unload the modules if needed.

```cfscript
modules   : { enabled : false, expanded : false }
```

### Configuration

<table><thead><tr><th width="149">Key</th><th width="120">Type</th><th width="147">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><code>enabled</code></td><td>Boolean</td><td>false</td><td>Enable the collector</td></tr><tr><td><code>expanded</code></td><td>Boolean</td><td>false</td><td>Expand the panel by default or not</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/SCR-20230616-ntjx.png" alt=""><figcaption></figcaption></figure>
