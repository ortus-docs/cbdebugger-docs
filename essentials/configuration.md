# Configuration

The debugger is highly configurable, and we have many settings to assist you in your development adventures and performance tuning.  The debugger works by activating data collectors and configuring them.  Please note that the more collectors you activate, the **slower** your application can become. By default, we have pre-selected defaults, which add negligible performance to your applications.

### Collectors

The ColdBox Debugger collectors are powerful listeners used for debugging and analyzing applications built on ColdBox. These collectors gather various types of information and statistics during the execution of an application, allowing developers to gain insights into the application's behavior and performance.

The collectors are designed to capture data related to different aspects of an application, such as request information, execution times, database queries, cache usage, and log messages.  Please note that each collector can have its own configuration options.

<table><thead><tr><th width="207">Collector</th><th width="103" data-type="checkbox">Enabled</th><th>Description</th></tr></thead><tbody><tr><td><a href="../collectors/adobe-sql.md"><code>acfSql</code></a></td><td>false</td><td>Tracks all SQL calls made by Adobe</td></tr><tr><td><a href="../collectors/async.md"><code>async</code></a></td><td>true</td><td>Tracks ColdBox executors and tasks</td></tr><tr><td><a href="../collectors/cachebox.md"><code>cachebox</code></a></td><td>false</td><td>Monitors and tracks Cache Providers</td></tr><tr><td><a href="../collectors/cborm.md"><code>cborm</code></a></td><td>false</td><td>Tracks all SQL calls made via cborm criteria queries or helpers</td></tr><tr><td><a href="../collectors/collections.md"><code>collections</code></a></td><td>false</td><td>Tracks the <code>rc</code> and <code>prc</code> collections in the debugger.</td></tr><tr><td><a href="../collectors/lucee-sql.md"><code>luceeSql</code></a></td><td>false</td><td>Tracks all SQL calls made by Lucee</td></tr><tr><td><a href="../collectors/coldbox-modules.md"><code>modules</code></a></td><td>false</td><td>Monitors module registration and activations</td></tr><tr><td><a href="../collectors/qb-quick.md"><code>QB/Quick ORM</code></a></td><td>false</td><td>Tracks all SQL calls made via <code>qb</code></td></tr><tr><td><a href="request-tracker.md"><code>requestTracker</code></a></td><td>true</td><td>Tracks incoming ColdBox requests</td></tr><tr><td><a href="../collectors/tracers.md"><code>tracers</code></a></td><td>true</td><td>Enables tracer messages in a request profile</td></tr></tbody></table>

### Config

If you are in ColdBox 6, add the following configuration settings to the `moduleSettings` structure in your `config/Coldbox.cfc` or if you are in ColdBox 7+ you can create a `config/modules/cbdebugger.cfc` and add your configuration.  Here is the default configuration CBDebugger ships with:

```cfscript
{
	// This flag enables/disables the tracking of request data to our storage facilities
	// To disable all tracking, turn this master key off
	enabled          : true,
	// This setting controls if you will activate the debugger for visualizations ONLY
	// The debugger will still track requests even in non debug mode.
	debugMode        : controller.getSetting( name = "environment", defaultValue = "production" ) == "development",
	// The URL password to use to activate it on demand
	debugPassword    : "cb:null",
	// This flag enables/disables the end of request debugger panel docked to the bottem of the page.
	// If you disable i, then the only way to visualize the debugger is via the `/cbdebugger` endpoint
	requestPanelDock : true,
	// Request Tracker Options
	requestTracker   : {
		// Store the request profilers in heap memory or in cachebox, default is memory
		storage                      : "memory",
		// Which cache region to store the profilers in
		cacheName                    : "template",
		// Track all cbdebugger events, by default this is off, turn on, when actually profiling yourself :) How Meta!
		trackDebuggerEvents          : false,
		// Expand by default the tracker panel or not
		expanded                     : false,
		// Slow request threshold in milliseconds, if execution time is above it, we mark those transactions as red
		slowExecutionThreshold       : 1000,
		// How many tracking profilers to keep in stack
		maxProfilers                 : 50,
		// If enabled, the debugger will monitor the creation time of CFC objects via WireBox
		profileWireBoxObjectCreation : false,
		// Profile model objects annotated with the `profile` annotation
		profileObjects               : false,
		// If enabled, will trace the results of any methods that are being profiled
		traceObjectResults           : false,
		// Profile Custom or Core interception points
		profileInterceptions         : false,
		// By default all interception events are excluded, you must include what you want to profile
		includedInterceptions        : [],
		// Control the execution timers
		executionTimers              : {
			expanded           : true,
			// Slow transaction timers in milliseconds, if execution time of the timer is above it, we mark it
			slowTimerThreshold : 250
		},
		// Control the coldbox info reporting
		coldboxInfo : { expanded : false },
		// Control the http request reporting
		httpRequest : {
			expanded        : false,
			// If enabled, we will profile HTTP Body content, disabled by default as it contains lots of data
			profileHTTPBody : false
		}
	},
	// ColdBox Tracer Appender Messages
	tracers     : { enabled : true, expanded : false },
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
	},
	// CacheBox Reporting
	cachebox : { enabled : false, expanded : false },
	// Modules Reporting
	modules  : { enabled : false, expanded : false },
	// Quick and QB Reporting
	qb       : {
		enabled   : false,
		expanded  : false,
		// Log the binding parameters
		logParams : true
	},
	// cborm Reporting
	cborm : {
		enabled   : false,
		expanded  : false,
		// Log the binding parameters
		logParams : true
	},
	// Adobe ColdFusion SQL Collector
	acfSql   : { enabled : false, expanded : false, logParams : true },
	// Lucee SQL Collector
	luceeSQL : { enabled : false, expanded : false, logParams : true },
	// Async Manager Reporting
	async    : { enabled : true, expanded : false }
};
```

### Master Switch

You can enable or disable the request tracking globally via the `enabled` master switch

```
enabled : false
```

### Debug Mode

The [ColdBox debugger can be placed](configuration.md#debug-mode) in production environments and be enabled via our URL password actions.  This allows you to profile your application and then turn on the debugger just for YOU via our debugging cookies.

{% hint style="warning" %}
Please note that you can also add a `cbSecurity` rule if needed and add further security, which we recommend.
{% endhint %}

```cfscript
// This setting controls if you will activate the debugger for visualizations ONLY
// The debugger will still track requests even in non debug mode.
debugMode        : controller.getSetting( name = "environment", defaultValue = "production" ) == "development",
// The URL password to use to activate it on demand
debugPassword    : "cb:null"
```

### Request Panel Dock

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>Request Panel Dock</p></figcaption></figure>

You can enable/disable the rendering of our request panel dock which shows the profiling of the request.

```cfscript
// This flag enables/disables the end of request debugger panel docked to the bottem of the page.
// If you disable it, then the only way to visualize the debugger is via the `/cbdebugger` endpoint
requestPanelDock : true
```
