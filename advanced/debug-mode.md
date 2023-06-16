---
description: Turn the debugger on/off when needed
---

# Debug Mode

The debugger can be enabled via URL commands if needed in public facing applications with a combination of two url keys:

* `debugMode:boolean` - Control to turn the debugger on/off
* `debugPassword:string` - The secure password to use to enable the debugger

Please see the [configuration](../essentials/configuration.md#debug-mode) on how to add the default debug mode and debug password.  If your debug password is validated and you turn on debug mode a secured cookie will be stored for you and you will be able to visualize the debugger.  Once you turn it off, then it will remove this cookie for you.

```
https://myapp.com/cbdebugger?debugmode=true&debugpass=mys3cret3key
```

{% hint style="warning" %}
Please note that you can also add a `cbSecurity` rule if needed and add further security, which we recommend.
{% endhint %}
