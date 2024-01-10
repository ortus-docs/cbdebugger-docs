---
description: Profile all calls made by Hyper as http/s
---

# Hyper HTTP Collector

You can use the `hyper` configuration structure to configure the `hyper` panel in the debugger. This will track all outgoing http/s calls made by the Hyper module in your debugger.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Hyper Panel</p></figcaption></figure>

{% hint style="info" %}
Hyper exists to provide a fluent builder experience for HTTP requests and responses. It also provides a powerful way to create clients, i.e. Builder objects with pre-configured defaults like a base URL or certain headers.

#### [https://forgebox.io/view/hyper](https://forgebox.io/view/hyper) <a href="#requirements" id="requirements"></a>
{% endhint %}

```cfscript
// Hyper Collector
hyper    : {
	enabled         : false,
	expanded        : false,
	logResponseData : false,
	logRequestBody  : false
}
```

<table><thead><tr><th width="206">Key</th><th width="126">Type</th><th width="89">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><code>enabled</code></td><td>Boolean</td><td>false</td><td>Enable the collector</td></tr><tr><td><code>expanded</code></td><td>Boolean</td><td>false</td><td>Expand the panel by default or not</td></tr><tr><td><code>logResponseData</code></td><td>Boolean</td><td>false</td><td>Log the response from the API Call</td></tr><tr><td><code>logRequestBody</code></td><td>Boolean</td><td>false</td><td>Logs the request body</td></tr></tbody></table>



