# Better Grbl Support Plugin for Octoprint

![grbl](https://raw.githubusercontent.com/gnea/gnea-Media/master/Grbl%20Logo/Grbl%20Logo%20250px.png)

This plugin was inspired by mic159's Grbl Support plugin (https://plugins.octoprint.org/plugins/octoprint-grbl-plugin/).  His plugin gets you 90% of the way there for adding Grbl support to Octoprint but had a couple limitations and lacked some bells and whistles from a UI and configuration perspective.

**Better Grbl Support** utilizes mic159's gcode receiver parser (with minor changes at the moment) and does much, much more:

* Replaces Octoprint's Control tab with its own Grbl Control tab
* Execute bounding box (framing) routines based on origin location and supplied dimensions
* Computes selected file dimensions and pre-populates framing length/width fields
* Click on the webcam image to enlarge it to its native resolution
* Updates Grbl state data automatically (State / X location / Y location / Speed / Power), even whle printing!
* Weak Laser Toggle, Sleep, Reset, and Unlock buttons conveniently placed within the Grbl Control tab
* Rewrites Octoprint's annoying hardcoded M115 (Hello) queries as M5 requests
* Rewrites M105 (temperature updates) as Grbl status updates
* Suppresses M110 (reset line #) requests
* Rewrites M400 (Finish moves) using Grbl Dwell
* Reswrites M114 (current position) using Grbl Positioning
* Implements M999 for reseting Grbl (^X)
* Hides the Octoprint Control, Temperature and GCode Viewer tabs
* Optionally adds Laser Commands and State sections to the Control tab
* Suppresses status update reporting during GCODE streaming
* No need to ignore firmware errors or track down other Octoprint nuance settings
* Automatically disables Model Size Detection
* Automatically disables sending checksums
* Automatically disables the Printer Safety Check plugin
* Most configuration options are configurable via Plugin Settings

## Setup

Install via the bundled [Plugin Manager](https://github.com/foosel/OctoPrint/wiki/Plugin:-Plugin-Manager)
or manually using this URL:

    https://github.com/synman/OctoPrint-Bettergrblsupport/archive/master.zip

**NOTE:** Installing this pluging directly from the URL above ensures you always have the latest version, but this comes with risk.  I do not follow a traditional gitflow which means commits to the master branch may not be fully tested and could cause unforeseen issues. Proceed at your own risk.  

## Configuration

There are some meaningful caveots regarding the installation and configuration of this plugin.  If you use it in a multi-printer / profile environment it will very likely cause problems for your other profiles as it makes **GLOBAL** configration changes behind the scenes.  A future version may resolve this, but understand that currently multi-profile installations are not currently supported.

Furthermore, a number of global configuration changes are made blindly and I have no way of reverting these changes.  Be prepared to manually edit your config.yaml and/or manually revert global settings if you uninstall / disable this plugin to restore your Octoprint installation to its prior state.

Pay special attention to the following config.yaml configuration parameters:

* appearance / components / temperature tab
* controls (any / all customizations made to it)
* feature / temperatureGraph
* feature / gcodeVisualizer
* feature / modelSizeDetection
* serial / neverSendChecksum
* serial / checksumRequiringCommands
* serial / helloCommand
* plugins / _disabled / printer_safety_check
* appearance / components / disabled / tab

## Screenshots

![Main UI](https://plugins.octoprint.org/assets/img/plugins/bettergrblsupport/better_grbl_support_main.png)

![Configuration UI](https://plugins.octoprint.org/ssets/img/bettergrblsupport/better_grbl_support_settings.png)
