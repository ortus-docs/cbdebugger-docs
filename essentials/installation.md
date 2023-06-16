# Installation

Leverage [CommandBox](https://www.ortussolutions.com/products/commandbox#download) to install into your ColdBox app:

```bash
box install cbdebugger --savedev
```

This will activate the debugger in your application and render out at the end of a request or by visiting the debugger request tracker visualizer at `/cbdebugger`.

You will now have to [configure](configuration.md) the debugger for it to start tracking your application.

{% embed url="https://s3.amazonaws.com/apidocs.ortussolutions.com/coldbox-modules/cbdebugger/4.2.0/index.html" %}
Latest API Docs
{% endembed %}

### WireBox Mappings

Once the module is activated, the following model objects will be available for you:

* `debuggerService@cbdebugger` - The main debugger service
* `JVMUtil@cbdebugger` - Useful for creating thread dumps and heap dumps
* `timer@cbdebugger` - Useful to time operations

### WireBox Delegates

We ship the following delegates:

* `TimerDelegate@cbdebugger`

You can use it to add timing capabilities to any CFC:

```cfscript
component delegates="TimerDelegate@cbdebugger"{

    ...
    
    cbTimeIt( "processData", ()=> {
        ... code to time
    }

}
```

The available methods for delegation are:

```cfscript
/**
 * Start a timer with a tracking label
 *
 * @label The tracking label to register
 *
 * @return A unique tracking hash you must use to stop the timer
 */
function startCBTimer( required label )

/**
 * End a code timer with a tracking hash. If the tracking hash is not tracked, we ignore it
 *
 * @labelHash The timer label hash to stop
 */
function stopCBTimer( required labelHash )

/**
 * Time for the execution of the passed closure that we will execute for you
 *
 * @label    The label to use as a timer label
 * @closure  The target to execute and time
 * @metadata A struct of metadata to store in the execution timer
 */
function cbTimeIt(
	required label,
	required closure,
	struct metadata = {}
)
```

### Mixin Helpers

We also add several helpers to all interceptors, layouts, views, and handlers:

```cfscript
/**
 * Method to turn on the rendering of the debug panel on a request
 */
any function showDebugger()

/**
 * Method to turn off the rendering of the debug panel on a request
 */
any function hideDebugger()

/**
 * See if the debugger will be rendering or not
 */
boolean function isDebuggerRendering()

/**
 * Start a timer with a tracking label
 *
 * @label The tracking label to register
 *
 * @return A unique tracking hash you must use to stop the timer
 */
function startCBTimer( required label )

/**
 * End a code timer with a tracking hash. If the tracking hash is not tracked, we ignore it
 *
 * @labelHash The timer label hash to stop
 */
function stopCBTimer( required labelHash )

/**
 * Time for the execution of the passed closure that we will execute for you
 *
 * @label The label to use as a timer label
 * @closure The target to execute and time
 * @metadata A struct of metadata to store in the execution timer
 */
function cbTimeIt( required label, required closure, struct metadata = {} )

/**
 * Shortcut to get a reference to the ColdBox Debugger Service
 */
function getCBDebugger()

/**
 * Push a new tracer into the debugger. This comes from LogBox, so we follow
 * the same patterns
 *
 * @message The message to trace
 * @severity The severity of the message
 * @category The tracking category the message came from
 * @timestamp The timestamp of the message
 * @extraInfo Extra info to store in the tracer
 */
DebuggerService function cbTracer(
	required message,
	severity  = "info",
	category  = "",
	timestamp = now(),
	extraInfo = ""
)
```

### Optional Requirements

#### cborm Collector

* Hibernate extension (on Lucee)
* `orm` package on ACF 2021+

#### Adobe SQL Collector

* `cbdebugger` package on ACF 2021+
* Check `Database Activity` on the debugger page or cfconfig setting

```json
debuggingShowDatabase : true
```

#### Lucee SQL Collector

Enable debug logging and database activity in the Lucee Debugging screens or via cfconfig:

```json
"debuggingDBEnabled":"true"
"debuggingEnabled":"true"
```
