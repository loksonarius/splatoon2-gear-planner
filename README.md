# splatoon2-gear-planner

_Web app to plan out your multiplayer gear for Splatoon 2_

## Goals

The following are the specific goals that will guide development of this
project:

- Provide full functionality both online and offline
- Work across all major web browsers with maximal accessibility
- Work as a native app on mobile phones that support PWAs
- Require minimal operational effort for future updates and upkeep
- Provide a reproducible and understandable developer experience to promote
  collaboration
- Provide _only_ the core experience needed for a gear planner, specifically:
  - Laying out ability slots
  - Calculating stat changes based of AP
  - Store loadouts for future reference

## Technical Plan

### The App

The core project is meant to be a PWA that is served from a static site. The
site should be hosted operation-less and generated automatically when published
through GitHub pages. The generated site will include the needed files to be
stored as an offline-capable PWA inlcuding the `manifest.json` and the service
worker code for caching.

There will be a core model of the app representing the state of the selected
load out in terms of ability slots and weapons. A separate library will be
called with the calculated AP totals to return a complete stats report. This
report will then be rendered by updating values on some HTML elements in a modal
component whenever "Stats" button is pressed. This model is simple enough to be
implemented without the use of frameworks or such tools. Most of the UI,
including modals and callbacks will be staticly generated during publishing.

### The Library

The core of stats calculations will be performed by a separate library. This
library will contain in-memory paramters for all player abilities and weapon
stats along with the necessary formulas to calculate changes based of AP. This
separate library will expose a single function that takes in an AP map to crunch
numbers with.

This library will be developed separate to the app for two main reasons:

- its functionality is basic and self-contained, and can be useful outside of
  the context of the app, this page, or even gear planning
- its implementation, sourcing, and general operations are more complex and
  follow a different lifecycle than that of this app

## Credit

The original project was made by
[devipotato](https://github.com/DeviPotato/splat2-calc/) and was forked for
updates and maintenance by [selicia](https://github.com/selicia/splat2-calc/). I
thank and credit both of these developers for the work put into this.

Thanks to [leanny](https://github.com/leanny) for their data mining efforts.

:warning:
**Initial development in progress, don't expect anything at all!**
:warning:
