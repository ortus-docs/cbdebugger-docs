# What's New With 4.2.0

### Added

* New `HyperCollector` so you can now track hyper requests if enabled
* `Timer` can now add timers a-la-carte via the `add()` method
* New fast and furious and tiny SQL/JSON Formatter
* New `LuceeSqlCollector` you can use to profile all SQL calls in Lucee
* New `luceeSql` configuration to control the Lucee SQL calls collector
* Changed the `instance` argument to `any` in the `debuggerService.openInEditorURL` to allow for a flat representational string of the URL to open in the editor.
* Ability to download a heap dump snapshot from the visualizer

### Changed

* The request panel dock is now a real dock and the only one presented, the rest are only show in the visualizer
* The `requestTracker.expanded` option is now removed, it's always expanded for visualizer and contracted for the dock

### Improved

* Updated test harness UI to make it easier to create debugging events

### Fixed

* Dumb whitespace added by CFML engines when doing inline `<pre>#method()#</pre>` calls.
* Better error handling when Debugger assets are not compiled instead of a cryptic error message: `The parameter [str] to function [closure_m] is required but was not passed in.`
