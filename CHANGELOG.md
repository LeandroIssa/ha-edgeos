# Changelog

## 1.2.4

- Add line number to WebSocket error log messages
- Add more log messages for WebSocket

## 1.2.3

- Device and Entity registry - `async_get_registry` is deprecated, change to `async_get`

## 1.2.2

- Hotfix for `Handled %` before first message is being received (division by zero)

## 1.2.1

- Fixed incorrect lookup value for Rate (Sent / Received) per device
- Improved message parsing
- Added web socket messages counters to status binary sensor (Received, Ignored, Handled %)

## 1.2.0

BREAKING CHANGES!

- Added for each interface multiple statistics sensors instead of attributes under the main binary sensor of the interface
- Added for each device multiple statistics sensors instead of attributes under the main binary sensor of the device
- Removed: Uptime sensor, uptime in seconds will be part of the status binary sensor
- Removed: Store debug file from the integration's options
- New service: Generate Debug File to `.storage/edgeos.debug.json`

## 1.1.8

- Removed entity / device delete upon restarting HA

## 1.1.7

- Added support for long term statistics

## 1.1.6

- Upgraded code to support breaking changes of HA v2012.12.0

## v1.1.5

- Fixed integration fails to load with EdgeOS version older than 2.0.9 [\#53](https://github.com/elad-bar/ha-edgeos/pull/53)

## v1.1.4

- Prevent the component to get installed or run with EdgeOS Firmware v1

## v1.1.3

- Fixed monitored_devices appear as disconnected [\#32](https://github.com/elad-bar/ha-edgeos/pull/32) by [@shlomki](https://github.com/shlomki)
- Added documentation of how to set manually log level as debug

## v1.1.2

- Fixed hassfest error (missing iot_class)

## 2020-10-24

**Fixed bugs:**

- Fixed interface parameter that should indicate whether an interface connected or not (l1up vs. up) [\#34](https://github.com/elad-bar/ha-edgeos/pull/34)

## 2020-09-17

**Fixed bugs:**

- Integration setup errors caused by invalid credentials (User input malformed / Unknown error occurred)

## 2020-07-23

**Implemented enhancements:**

- Moved encryption key of component to .storage directory
- Removed support for non encrypted password (**Breaking Change**)

**Fixed bugs:**

- Better handling of password parsing

## 2020-07-21

**Fixed bugs:**

- Don't block startup of Home Assistant [\#36](https://github.com/elad-bar/ha-edgeos/pull/36)

## 2020-07-22

**Implemented enhancements:**

- Support MDI icons for HA 0.113 and above
- Removed NONE option from drop-down, NONE was workaround for a validation issue in Integration's Options and fixed as part of HA v0.112.0

## 2020-07-03

**Fixed bugs:**

- Fix error message on load due to duplicate entities being created - Entity id already exists - ignoring: \*. Platform edgeos does not generate unique IDs

## 2020-06-23

**Fixed bugs:**

- Error fix on failed attempt to access the router

## 2020-06-20

**Fixed bugs:**

- Re-run pre-commit
- Handle closing HA session better to avoid stuck upon restart
- Avoid closing manually sessions opened by HA

## 2020-06-12

**Fixed bugs:**

- Fix logic of reconnect to avoid HA core getting stuck during restart

## 2020-05-29

**Fixed bugs:**

- Fix `Entity id already exists` warning log message on startup

## 2020-05-17

**Fixed bugs:**

- Fix incorrect error message displayed when WebSocket or API request failed
- Fix retry mechanism of API requests
- Fix integration's options error when device or interface list is empty

## 2020-05-14

**Implemented enhancements:**

- Integration's options - Renamed `Update interval` to `Update entities interval` (will reset the value to default in the first run)
- Integration's options - Added `Update API interval` to set the interval in seconds of the component to access EdgeOS API to get new devices and router settings, default=60 [\#27](https://github.com/elad-bar/ha-edgeos/issues/27)
- Improved the logic of heartbeat to take place every 30 seconds for both WebSocket and API connections

**Fixed bugs:**

- Fix API disconnection that causes "Failed to load devices data" errors [\#29](https://github.com/elad-bar/ha-edgeos/issues/29)
- Fix error message on HA termination

## 2020-05-08 #2

**Fixed bugs:**

- Fix redundant calculation of bits to bytes as data is already bytes

## 2020-05-08 #1

**Implemented enhancements:**

- Consider away interval can be modified in integration's options, interval is in seconds, default=180

**Fixed bugs:**

- Fix default value of unit in integration's options

## 2020-05-06

**Fixed bugs:**

- Fix WebSocket disconnections [\#26](https://github.com/elad-bar/ha-edgeos/issues/26)

## 2020-05-02

**Implemented enhancements:**

- Improved device tracker is home logic to consider traffic instead of just DPI report
- Version validation upon adding new integration (Required at least v1.10)

## 2020-05-01

**Fixed bugs:**

- Fix device_tracker didn't work correctly. It is always displayed not home

**Implemented enhancements:**

- More enhancements to options, ability to change setup details
- Support new translation format of HA 0.109.0
- Added **main**.py to root directory for debugging

## 2020-04-28 #3

**Fixed bugs:**

- Invalid credentials to EdgeOS Router when using IP [\#25](https://github.com/elad-bar/ha-edgeos/issues/25)

## 2020-04-28 #2

**Fixed bugs:**

- Async login without sleep 1 second

## 2020-04-28 #1

**Fixed bugs:**

- Fix disabled entity check throws an exception in logs

## 2020-04-27

**Fixed bugs:**

- Fix disabled entities still being triggered for updates

## 2020-04-26

**Fixed bugs:**

- Fix disabled entities are getting enabled after periodic update (update interval)

## 2020-04-25

**Implemented enhancements:**

- Simplified the way calculating whether device is connected or not, based on report of traffic analysis instead of calculating amount of traffic (bps) over the last 3 minutes [\#24](https://github.com/elad-bar/ha-edgeos/issues/24)
- Moved service `edgeos.save_debug_data` to Integration -> Options as configuration (that being reset after doing the action once)
- Moved service `edgeos.log_events` to Integration -> Options as configuration to toggle upon need
- Added ability to configure the log level of the component from Integration - Options, more details in README

## 2020-04-20 #2

**Fixed bugs:**

- Fix connection maximum attempts and added keep-alive WS message every 30 seconds [\#21](https://github.com/elad-bar/ha-edgeos/issues/21)

## 2020-04-20 #1

**Fixed bugs:**

- Missing resource for update interval field [\#19](https://github.com/elad-bar/ha-edgeos/issues/19)

## 2020-04-18

**Implemented enhancements:**

- Added changelog
- Added ability to configure update entities interval in seconds (Integrations -> Integration Name -> Options) [\#19](https://github.com/elad-bar/ha-edgeos/issues/19) [\#15](https://github.com/elad-bar/ha-edgeos/issues)
- Added instructions how to install in HACS [\#16](https://github.com/elad-bar/ha-edgeos/issues/16)
- Added password encryption upon saving the integration settings
- Improved drop-down logic to choose device trackers, monitored devices and interfaces [\#9](https://github.com/elad-bar/ha-edgeos/issues/9)
- Moved code to new file structure
- More logs added for easier debugging

**Fixed bugs:**

- Login failure initiated reconnect mechanism instead of die gracefully
