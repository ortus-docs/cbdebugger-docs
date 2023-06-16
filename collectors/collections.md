---
description: Profile the request collections in ColdBox
---

# Collections

You can use the `collections` configuration structure to configure the `collections` panel in the debugger. This will dump out the `rc` and the `prc` collections with the final snapshot of their data.  We recommend that you only enable this collector with the appropriate dump top levels as it can completely crash your server trying to dump out all the variables in the collections.

{% hint style="danger" %}
**WARNING** : This collector can crash your server. Make sure you have limits and use it wisely.
{% endhint %}

```cfscript
// Request Collections Reporting
collections : {
	// Enable tracking
	enabled      : false,
	// Expanded panel or not
	expanded     : false,
	// How many rows to dump for object collections
	maxQueryRows : 50,
	// How many levels to output on dumps for objects
	maxDumpTop   : 5
}
```

<table><thead><tr><th width="174">Key</th><th width="120">Type</th><th width="147">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><code>enabled</code></td><td>Boolean</td><td>false</td><td>Enable the collector</td></tr><tr><td><code>expanded</code></td><td>Boolean</td><td>false</td><td>Expand the panel by default or not</td></tr><tr><td><code>maxQueryRows</code></td><td>Integer</td><td>50</td><td>Number of rows to show for query dumps</td></tr><tr><td><code>maxDumpTop</code></td><td>Integer</td><td>5</td><td>How many levels to output on object dumps</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/SCR-20230616-nyjp (1).png" alt=""><figcaption></figcaption></figure>



