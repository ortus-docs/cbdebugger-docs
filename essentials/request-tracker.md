---
description: Debugger Request Tracker
---

# Request Tracker

![Request Tracker](https://raw.githubusercontent.com/coldbox-modules/cbdebugger/development/test-harness/includes/images/debugger-visualizer.png)

Apart from debugging the incoming request and presenting the debugger at the end of the request (Request Dock Panel), you can also navigate to `/cbdebugger` and visualize the Debugger request tracker. This panel will monitor ALL incoming requests to your application: REST, SOAP, Ajax, etc.

You can execute several commands from this visualizer:

* Clear all request history
* Reinit ColdBox
* Shutdown the debugger visualizer
* Refresh the requests
* Auto-refresh the requests
* Produce a Java Heap Dump

Each request is also tracked and visualized according to its activated collectors.

<figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

### Storage

You can use the `requestTracker.storage` setting to configure where the request trackers are stored.  The default values are:

* `memory` : The default, which stores the trackers in memory
* `cachebox` : Store the request trackers in a CacheBox provider via the `cacheName`
  * `cacheName` : Cache region to store the profilers. The default is the `template` cache region.

```cfscript
// Store the request profilers in heap memory or in cachebox, default is memory
storage : "memory",
// Which cache region to store the profilers in
cacheName : "template",
```

### Max Profilers

The debugger comes pre-configured to store a stack of 50 requests in memory.  You can change this via the following setting:

```cfscript
// How many tracking profilers to keep in stack
maxProfilers : 50,
```

### Track Debugger Events

If you wanted to profile even the debugger itself you can use the `trackDebuggerEvents` flag if needed.

```cfscript
// Track all cbdebugger events, by default this is off, turn on, when actually profiling yourself :) How Meta!
trackDebuggerEvents : false,
```

### Slow Execution Painting

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

The debugger can paint requests in a different color if they are executing slower than the threshold setting shown below.  Please note that the threshold is in milliseconds.

```cfscript
// Slow request threshold in milliseconds, if execution time is above it, we mark those transactions as red
slowExecutionThreshold : 1000,
```

### Execution Timers

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

Each request tracker has a panel called `ExecutionTimers` which shows all the timers the debugger was able to track during that request.  You can configure it via the following settings:

```cfscript
// Control the execution timers
executionTimers              : {
	expanded           : true,
	// Slow transaction timers in milliseconds, if execution time of the timer is above it, we mark it
	slowTimerThreshold : 250
},
```

The `expanded` is just a simple boolen to control if the panel is open by default, which it is.  The `slowTimerThreshold` is in milliseconds and when a timer passes that threshold it will be painted red; like the screenshot above.

### ColdBox Info Panel

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

You can control if the ColdBox information panel is open or closed by default via the `coldboxInfo` setting:

```cfscript
coldboxInfo : {
    expanded : false
}
```

### HTTP Request Panel

<figure><img src="../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

You can also configure the HTTP Request panel to do your bidding:

```cfscript
// Control the http request reporting
httpRequest : {
	expanded        : false,
	// If enabled, we will profile HTTP Body content, disabled by default as it contains lots of data
	profileHTTPBody : false
}
```

You can have the panel open or closed and even chose if the HTTP Body request will be stored or not.

<figure><img src="../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Be careful to not go overboard with profiling the HTTP Body because it can be very large.
{% endhint %}

### Exception Tracking

<figure><img src="../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p>Request History Exceptions</p></figcaption></figure>

All requests that produce exceptions are also tracked and special exception collectors are activated automatically to store the produced exception:

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>Exception Data</p></figcaption></figure>

It will store the stack trace and the tag context of the exception so you can visualize it and fix your bug.  It will also have links to open the offending code in VSCode or your favorite editor right from the debugger.  You can even open and navigate the tag context in your IDE from the debugger.

You can also see all the collectors and their information to the point of the exception:

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
