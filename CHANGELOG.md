# Changelog

- Latest production version: v3.1.4.5(382)
- Latest beta version: v4.0.2(4002)

This changelog is for SD Maid v4. For older logs: [v3](changelogV3.txt), [v2](changelogV2.txt), [v1](changelogV1.txt).

## [Unreleased]
- TBD

## [4.0.2] - 2015-12-31 (BETA)
### Core
- Added: If the busybox setup fails, the final explanation screen will now show an actual error message with details.
- Added: Exclusion for SD Maid from the databases tool.
- Added: SD Maids install ID is now shown in overview for debug purposes and can be copied by tapping it.
- Added: Creating a file or directory called "sdm_force_debug_run" on the sdcard will trigger a debug run on SD Maids next launch.
- Improved: New Clutter database entries.
- Improved: Recognition of specific su binaries and apps.
- Improved: Logging output and tagging.
- Improved: Compatibility check of native busybox binaries. Now ensuring the mount command delivers usable output.
- Changed: Changing the worker count in advanced settings now automatically restarts SD Maid.
- Changed: The changelog is no longer an in app screen but shown from http://sdmaid.darken.eu/changelog .
- Fixed: Crash when granting SD Maid storage access/permission and the setup activity was recreated.
- Fixed: Rare crash during rootcheck on not correctly rooted devices.
- Fixed: Warnings during reading the changelog.
- Fixed: Possible crash on network issues during update check.
- Fixed: Debug run not correctly elevating the debug level.
- Fixed: Build fingerprint not being included in debug run logs.
- Fixed: Possible UI crash when resuming the UI and an action just finishes.
- Fixed: Crash when trying to determine ownership of a system app without source dir.
- Fixed: Crash caused by file forensics failing on files stored in secondary storage if that storage was mounted within the primary storage (e.g. /mnt/sdcard/external_sd).
- Removed: Some tracking because pirates are too dumb to download the correct apks and I'm getting spammed with dumb error reports.

### Overview
- Added: Buildtime to SD Maids info.
- Fixed: Crashed caused by running Overview simultaneously with other tools.

### CorpseFinder
- Improved: Canceling behavior. Canceling happens quicker now.
- Improved: Progress feedback. Filter progress should now show which filter is active and in what state.
- Improved: UX of deleting items from the details view.
- Improved: Performance of the sdcard scan, should be much faster now and we still get to keep the accuracy improvements, \o/.
- Changed: Filter choice settings have ben reset.
- Changed: The app data filter has been split into 3 individual filter (/Android/data/,/data/data/ and the sdcard root excluding the Android/data folder).

### AppControl
- Fixed: Crash when quickly opening and closing app details.
- Fixed: Rotation crash in receiver manager (#263).
- Improved: Improved receiver manager layouting (#266).

### SystemCleaner
- Improved: Improved UX of deleting items from the details view.
- Changed: Restricted MacOS files filter to (root of) SDCARD.
- Fixed: Fixed filter on/off settings not working.

### AppCleaner
- Improved: Improved UX of deleting items from the details view.
- Fixed: Deletion being possible without having the pro version.

### Duplicates
- Improved: Improved UX of deleting items from the details view.
- Fixed: Deletion being possible without having the pro version.

### Exclusions
- Improved: Replaced extra searchbar with built in searchview.
- Fixed: Fixed exclusions being cut off.

## [4.0.1] - 2015-12-19 (BETA)
### Core
- Fixed: Timeout during root check not working leading to endless waiting.
- Fixed: Crash due missing update data.
- Fixed: Crash when determining the ownership of a system app related file and the system has an app installed without source folder.
- Fixed: Crash due to rotation when running a setup task.
- Fixed: Crash due CrashTracking crashing :') due to a race condition on app initialisation.
- Fixed: Crash on orientation change related to race conditions between UI callbacks.
- Fixed: Possible crash when resuming SD Maid on a tool that is working state.
- Fixed: Crash due to race condition when entering/leaving SD Maids UI while a new thread is being launched.
- Fixed: Crash due to quickly resuming, pausing, resuming SD Maids main app, a callback would trigger while the UI was no longer visible.
- Fixed: Crash when doing an update check and the server didn't know the version.
- Fixed: Crash during storage detection because the system returned a NULL path.
- Fixed: Crash during storage detection because the sdcard was not mounted or available.
- Fixed: Crashes caused by file forensics failing to match items on /data/app if SD Maid was moved to the sdcard (TY +Ray Hollingsworth, his log provided the solution).
- Changed: If no activity for OPEN_DOCUMENT_TREE is found when playing in the advanced settings, we show a warning instead of crashing.
- Improved: Changes to crash tracking and logouput to help me identify specific issues.
- Improved: Disabled crashtracking if SD Maids assets have been modified and the app crashes because it can no longer support that device (good job /s).
- Improved: Updated translations.

### Explorer
- Fixed: Crash due to trying to create a bookmark for a not mounted sdcard.

### SystemCleaner
- Fixed: Dataloss due to DefaultFilter instantiation with incomplete filter criteria. If this is detected a debug report will be send and the filter will be skipped (TY +Salman Khan SK, his log provided the solution).

### Duplicates
- Fixed: Crash when entering settings.

### Databases
- Fixed: Crash when entering settings.

### LastModified
- Fixed: Crash when entering settings.

## [4.0.0] - 2015-12-18 (BETA)
### Core
- Added: Support for API23 permission system.
- Added: Advanced option to work around Kingo Root's faulty su binary behavior.
- Added: Previews now support videos.
- Added: Exclusions now support regular expressions. There is currently no UI for it, prepend "regex:" during creation.
- Added: Exclusions can now be imported &amp; exported.
- Added: Ownership detection for /system/app, /system/priv-app and /sdcard/Android/media.
- Improved: Design!
- Improved: UI performance by fixing duplicate/overlapping update calls.
- Improved: Switching activities no longer requires reloading of preview picture.
- Improved: Settings now have a nicer picker window to choose paths.
- Improved: Settings now have a tablet mode.
- Improved: Updated BusyBox, now build from 1.23.2 with buildroot 2015.08.1 (default config)
- Improved: Update check now also includes the unlocker.
- Improved: Robustness of uri based external storage access via StorageAccessFramework.
- Fixed: Threading issue when canceling workers through the ActionProgressBar.
- Fixed: Previews sometimes not loading when scrolling like a maniac.
- Changed: Settings structure has been rearranged and are now accessible from the bottom of the navigation drawer.
- Changed: Bugreporting now uses bugsnag.com instead of ACRA (I needed a better backend to organise crash reports).
- Changed: Bugreporting email has been reset.
- Changed: Bugreporting preference has been reset.
- Removed: Removed &lt; API16 binaries.
- Removed: Support for Android &lt; 4.0 (minSdkVersion 16).

### QuickAccess
- Added: Button to see a small explanation.
- Added: A widget that can run QuickAccess actions in one pass.
- Changed: Entries now show full progress feedback.
- Changed: Tapping the title now takes you to the full view.
- Changed: The FAB button will return to it's initial SCAN state even if items are left.

### Overview
- Changed: Consolidated SD Maids version and state details into a single entry.
- Removed: Full display of all mounts (just wasn't that useful and very badly supported).
- Removed: References that could be construed SD Maid only works with ROOT. It just has the bonus that if you have root it can utilize it. Only very early versions of SD Maid needed root.

### Explorer
- Added: Bookmarks for storage locations (right-side drawer).
- Added: Added user bookmarks.
- Added: Copy support on 5.0+ external storage.
- Added: Move support on 5.0+ external storage.
- Added: "Pathdump" it writes the contents of a folder recursively into a textfile.
- Improved: Copied/cut items are now visibly represented by a Snackbar at the bottom, offering details and allowing to clear SD Maids clipboard.
- Removed: Individual setting for preview loading, this is now a general setting.
- Changed: Creating a SystemCleaner filter from the context menu is now an option that has to be enabled.
- Changed: Changing permissions is now an option that has to be enabled.
- Changed: Doing a forced media scan is now an option that has to be enabled.

### Searcher
- Improved: Simplified search options.
- Added: Added SHOW button to entry details.
- Changed: Clicking a search result now open it in the Explorer if there is no app to open it.
- Removed: Individual setting for preview loading, this is now a general setting.

### AppControl
- Added: Support for managing receivers of type: HEADSET_PLUG.
- Added: Support for managing receivers of type: ACTION_POWER_CONNECTED.
- Added: Support for managing receivers of type: ACTION_POWER_DISCONNECTED.
- Added: Color coded action by their overall impact risk.
- Improved: Size accuracy and displayed details.
- Improved: Scan performance, especially on subsequent refreshs.
- Fixed: Dalvik-cache file size not being determined on Lollipop.
- Changed: Removed tag "No APK" from list display. Rare occurrence and not really useful at that stage.
- Changed: The expandable actions and the app details have been moved into a new activity.
- Changed: Autostart related entries have been renamed to BOOT or ON_BOOT to combat misconceptions.
- Changed: 'Toggle autostart' Dialog has been replaced by the 'Receiver Manager' Activity.

### CorpseFinder
- Added: Swipeable fullscreen view for comfortable one-handed viewing of corpse details while drinking coffee.
- Added: Possibility to delete and exclude items from within the details view.
- Improved: All filters now support extension through the clutter database.
- Changed: The asec filter now no longer only looks at .asec files.
- Changed: The "Remove keepers" setting has been reversed and renamed to fit the equivalent within AppControl.
- Changed: The Uninstall watcher now only executes the AppData filter.
- Changed: Corpse checks on the sdcard now support item names with variables through regex matching. Note: This mean the previous reverse lookup method can no longer be used which increases scan time.
- Fixed: Issue in several filters that could lead to false negatives if packagenames overlapped.

### SystemCleaner
- Added: Swipeable fullscreen view to look at the details of each filter.
- Added: Support for importing and exporting user made filters. Importing filters is free, creation and export paid.
- Added: Possibility to delete and exclude items from within the details view.
- Added: JSON syntax for creating user filters.
- Added: User filters now support regex, min size, max size and storage location criteria (currently not usable from the UI, only from JSON).
- Added: Logic to automatically convert old v3 custom filters to the new "user filters".
- Improved: Filter manager view, it's now split into two panes, with the right side pane allowing management of custom made filters.
- Improved: Filter creation UI, simplified possible settings, reduced chance to make mistakes.
- Improved: Default filter accuracy and flexibility by replacing basic string matching with REGEX expressions.
- Removed: Setting to enable creation of user filters. It's now on by default.
- Removed: NetStats and ProcStats filter, their usefulness was always in doubt. If you really want this, create a user filter.

### AppCleaner
- Added: Swipeable fullscreen view to look at the details of each app.
- Added: Possibility to delete and exclude items from within the details view.
- Added: Info and shortcut to system storage for people on 6.0 without root.
- Added: Support for extending cache definitions via regex.

### Duplicates
- Improved: Scan performance through better internal data structures.
- Added: Possibility to delete and exclude items from within the details view.
- Added: Safeguard that routes all single item deletions through an extra check to ensure we have one left over.
- Removed: Individual setting for preview loading, this is now a general setting.

### Biggest
- Improved: Switching behavior when viewing an entry in the Explorer, smoother change and scrolling to correct position.

### LastModified
- Improved: Switching behavior when viewing an entry in the Explorer, smoother change and scrolling to correct position.