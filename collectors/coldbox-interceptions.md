---
description: Profile any ColdBox Interception Call
---

# ColdBox Interceptions

![Interception Call](https://raw.githubusercontent.com/coldbox-modules/cbdebugger/development/test-harness/includes/images/debugger-timers.png)

In an event-driven framework like ColdBox, there are tons of events that fire within traditional request/response transactions. You can activate our tracker and we will trace and profile interception calls. Activate it via the settings first:

```js
// Profile Custom or Core interception points
profileInterceptions         : true,
// By default all interception events are excluded, you must include what you 
// want to profile
includedInterceptions        : [ "onUserSave", "ORMPostLoad" ],
```

Once activated, you can add a collection of interception points to profile in your application. We will track them for you and even if they are ORM calls we will tell you which entity initiated the call.
