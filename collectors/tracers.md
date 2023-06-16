---
description: Send message tracers to store in the request tracker
---

# Tracers

The CBDebugger ships with a LogBox appender called the `TracerAppender` that if enabled it will intercept all log calls into the ColdBox Debugger tracers panel.  It will show the log with it's log level and even the complex extra information.  The default log levels for the appender are:

* **min** : fatal
* **max** : debug

```cfscript
tracers     : { enabled : true, expanded : false },
```

<table><thead><tr><th width="149">Key</th><th width="120">Type</th><th width="147">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><code>enabled</code></td><td>Boolean</td><td>false</td><td>Enable the collector</td></tr><tr><td><code>expanded</code></td><td>Boolean</td><td>false</td><td>Expand the panel by default or not</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
