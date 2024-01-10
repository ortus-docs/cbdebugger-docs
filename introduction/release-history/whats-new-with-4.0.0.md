---
description: 2022-NOV-22
---

# What's New With 4.0.0

### Added

* ColdBox 7 support
* New `TimerDelegate` that can be used to add timer functions to any model
* Timer service rewritten to support nesting and included metadata
* Ability to open views and layouts from the execution timers in any Code Editor
* New `WireBoxCollector` which is only used if enabled. This greatly accelerates the performance of the request collector since before they where in the same collector.
* Ability to open CFCs that are profiled by the WireBox Collector in any Code Editor.
* Ability to open the Handler events that are profiled by the Request Collector in any Code Editor.
* New life-cycle events: `onDebuggerUnload`, `onDebuggerLoad`
* Ability for the custom `timeIt()` functions to accept metdata to store in the execution timer
* New `Slowest` Queries panel for cborm, acf, and qb/quick
* New visualizer total db time as well as request time including percentage of the request time
* Ability to export a profiler in json
* Ability to sort the visualizer's profilers

### Fixed

* Timer service reconstructing the timer hashes and profilers twice.
* `timeIt()` helper was not passing the closure correctly
* If doing a fwreinit on the visualizer, the current profiler was still being show even thought it was empty. Add an empty check to avoid the big bang!
* Empty response codes for Adobe, due to their incredibly weird Response object nesting.
* Migration to java random id's for speed

### Changed

* Tracers are now streamlined and stored alongside the request profilers
* Small UI fixes on request profiler HTTP methods
* WireBox collecting is now done by the WireBox collector not the Request Collector.
* Adobe 2016 Dropped
