---
description: Debugger Request Tracker
---

# Request Tracker

![Request Tracker](https://raw.githubusercontent.com/coldbox-modules/cbdebugger/development/test-harness/includes/images/debugger-visualizer.png)

A part from debugging the incoming request and presenting the debugger at the end of the request, you can also navigate to `/cbdebugger` and visualize the Debugger request tracker. This panel will monitor ALL incoming requests to your application: rest, soap, ajax, etc.

You can execute several commands from this visualizer:

* Clear all request history
* Reinit ColdBox
* Shutdown the debugger visualizer
* Refresh the requests
* Auto refresh the requests
* Produce a Java Heap Dump

You can then select a specific request and open the request report with all the tracked information.

{% hint style="info" %}
Please note that the request tracker in the debugger has a configurable capacity for requests. By default we track the last 50 requests into the application. You can either increase it or reduce it to your hearts content. Just note that the more you track, the more memory it consumes unless you offload it to an external cache.
{% endhint %}

```js
requestTracker : {
    ...
    // How many tracking profilers to keep in stack: Default is to monitor the last 20 requests
    maxProfilers : 50,
    ...
}
```
