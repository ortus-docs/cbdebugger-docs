---
description: Profile any object method call
---

# Objects Methods

<figure><img src="../.gitbook/assets/SCR-20230616-nidy.png" alt=""><figcaption><p>Object Profiling</p></figcaption></figure>

The ColdBox debugger allows you to profile the execution of **ANY** method in **ANY** CFC via our AOP pointcuts. All you need to do is add the `profile` annotation to a method or component declaration in your model/ORM objects. Once you do, the debugger will track the execution of those methods in the debug timers panel for you. First thing to do is make sure the setting is turned on:

```cfscript
requestTracker : {
	// Profile model objects annotated with the `profile` annotation
	profileObjects               : true,
	// If enabled, will trace the results of any methods that are being profiled
	traceObjectResults           : false,
}
```

The `traceObjectResults` if `true` will track the actual results of the method calls into your debugger timer panel. Careful, as we will serialize anything you send to us. Then add the `profile` annotation to any method or CFC.

```js
/**
 * Profile all methods in this component
 */
component profile{

}

// Add the profile to this method to track it
function saveAllObjects() profile{

}
```

Profiling objects is great because you can just annotate and forget. Nothing to turn off in production.  However, just note that doing AOP abstractions on more methods, the more slow downs you will experience, especially on transient objects.  We would recommend that you use it on specific methods only and be very wearisome of using the tracing of object results.
