# Change Log

## v2.2.0 - xxxx-xx-xx

### New Features:

* Thargoid War mission tracking 🍀. BGS-Tally now tracks your Thargoid War passenger 🧍, cargo 📦, and wounded ⚰️ (escape pod) missions. There are options to report just BGS, just Thargoid War or all combined activity, as well as an option to have a separate Discord channel when reporting Thargoid War activity.

### Changes:

* When displaying information about a CMDR, or posting to Discord, use the latest information we know about that CMDR (squadron membership, for example).
* When displaying CMDR ship type, try to use the localised name if present, instead of internal ship name (e.g. `Type-10 Defender` instead of `type9_military`).
* The text report field is unfortunately no longer manually editable.  This wasn't possible with the splitting of the reports into BGS and Thargoid War, and was a bit of an oddity anyway, as any edits were always overwritten by any changes and lost when the window was closed. If you need to edit your post, copy it and edit it at the destination after pasting.
* When listing ground CZs, use a ⚔️ icon against each to easily differentiate them.
* Tweaks to post titles and footers.
* Whitespace is now stripped from Discord URLs to minimise user error (thanks @steaksauce-).

### Bug Fixes:

* If a selected CMDR has a squadron tag, but that squadron isn't available in Inara, still show the tag when displaying or posting the CMDR info to Discord.
* Moved the overlay text - both tick time and tick alerts - a little to the left to allow for differences in text placement between machines.


## v2.1.0 - 2022-12-05

### New Features:

* CMDR Spotting. The plugin now keeps track of the players you target and scan, together with when it happened and in which system. It also looks up any public CMDR and Squadron information on Inara. All this information is presented in a new window where you can review the list of all CMDRs you've targeted. There is also a 'Post to Discord' feature so you can post the CMDR information to your Discord server if you wish (manual only).
* New format available for Discord posts. The (I think) neater and clearer look uses Discord message embeds. The old text-only format is still available from the settings if you prefer it.

### Changes:

* After the game mode split in Odyssey Update 14, BGS-Tally only operates in `Live` game mode, not `Legacy`.
* Additional data files created by BGS-Tally (such as the mission log) are now saved in an `otherdata` subfolder to keep the top level folder as tidy as possible.

### Bug Fixes:

* BGS-Tally was intentionally omitting secondary INF when a faction was in conflict, but it turns out some mission types can have -ve INF effects on those factions. So we now report all secondary INF.
* The game was not including expiry dates in some mission types (why?), and BGS-Tally was throwing errors when it encountered these. Now we don't require an expiry date.


## v2.0.2 - 2022-10-27

### Bug Fixes:

* Some state was not being initialised correctly on first install of BGS-Tally.


## v2.0.1 - 2022-10-22

### Bug Fixes:

* The latest activity window was failing to display on a clean install of BGS-Tally.


## v2.0.0 - 2022-10-22

### New Features:

* In game overlay implemented!  Currently this just displays the current tick time, and if the next predicted tick is in the next hour, will alert that it's upcoming. The overlay requires *either* installing the separate [EDMCOverlay plugin from here](https://github.com/inorton/EDMCOverlay/releases/latest) *or* having another plugin running that has EDMCOverlay built in (for example the EDR plugin). _Many more things are planned for the overlay in future versions of BGS-Tally_.
* In the activity window, there are now markers against every system, showing at a glance whether there is activity (&#129001; / &#11036;) and also whether you are reporting all, some, or none of the activity (&#9745; / &#9632; / &#9633;).
* The system you are currently in is always displayed as the first tab in the activity log, whether or not you've done any activity in it and whether or not you have "Show Inactive Systems" switched on. This allows you to always add activity manually in the system you're in, e.g. Space CZ wins.
* The 'Previous BGS Tally' button has been replaced by a 'Previous BGS Tallies &#x25bc;' selector, where you can look at all your history of previous work.

### Changes:

* Changed the tick date / time format in main EDMC window to make it more compact.
* Changed the date / time format in Discord posts to avoid localised text (days of week and month names).
* Big improvement in detecting new ticks. Previously, it would only check when you jump to a new system. Now, it checks every minute. This means that even if you stay in the same place (e.g. doing multiple CZs in one system), the tick should tock correctly.
* This version includes a complete and fundamental rewrite of the code for ease of maintenance. This includes a change in how activity is stored on disk - the plugin is now no longer limited to just 'Latest' and 'Previous' activity, but activity logs are kept for many previous ticks - all stored in the `activitydata` folder.
* Revamped the plugin settings panel.

### Bug Fixes:

* Murders were being counted against the system faction. Now count them against the faction of the target ship instead.
* Using the mini scroll-left and scroll-right arrows in the tab bar was throwing errors if there weren't enough tabs to scroll.
* A full fix has now been implemented to work around the game bug where the game reports an odd number of factions in conflicts in a system (1, 3, 5 etc.) which is obviously not possible. BGS-Tally now pairs up factions, and ignores any conflicts that only have a single faction.


## v1.10.0 - 2022-08-11

### New Features:

* Now use scrollable tabs and a drop-down tab selector. Tabs for systems are sorted alphabetically by name, prioritising systems that have any BGS activity first.
* Every Discord post now includes a date and time at the bottom of the post, to make it clear exactly when the user posted (suggested by @Tobytoolbag)
* There is now a 'FORCE Tick' button in the settings, which can be used if the tick detector has failed to detect a tick but you know one has happened. This can occur on patch days or if the tick detector is down.

### Changes:

* Now use an automated GitHub action to build the zip file on every new release.
* Tidy up and narrow the BGS-Tally display in the EDMC main window, to reduce the width used (thank you @Athanasius for this change).

### Bug Fixes:

* Workaround for game bug where factions are incorrectly reported at war (if only a single faction is reported at war in a system, ignore the war) now works for elections too.


## v1.9.0 - 2022-04-23

### New Features:

* Now track Scenario wins (Megaship / Space Installation) - unfortunately manual tracking only, because we cannot track these automatically.

### Bug Fixes:

* If a faction state changed post-tick, this was not spotted by the plugin if you have already visited the system since the tick. Most noticeable case was when a war starts if you were already in the system - no CZ tallies or manual controls appeared. This is fixed.
* Better handling of network failures (when plugin version checking and tick checking).
* Now accepts Discord webhooks that reference more domains: `discord.com`, `discordapp.com`, `ptb.discord.com`, `canary.discord.com`. This was stopping the _Post to Discord_ button from appearing for some users (thank you @Sakurax64 for this fix).

### Changes:

* Simplified the `README`, moving more information into the wiki.


## v1.8.0 - 2022-02-23

### New Features:

* Now track Black Market trading separately to normal trading.
* Now track trade purchases at all markets, as buying commodities now affacts the BGS since Odyssey update 10.

### Bug Fixes:

* Never track on-foot CZs when in Horizons, to help reduce false positives.
* Fix error being thrown to the log when closing EDMC settings panel.
* Add workaround for game bug where factions are incorrectly reported at war - if only a single faction is reported at war in a system, ignore the war.

### Changes:

* Faction name abbreviations are slightly better when dealing with numbers, as they are no longer abbreviated. For example `Nobles of LTT 420` is now shortened to `NoL420` instead of `NoL4`.
* Layout tweaks to the columns in the report windows.


## v1.7.1 - 2021-12-21

### Bug Fixes:

* Fix plugin failure if tick happens while in-game, and you try to hand in BGS work before jumping to another system.


## v1.7.0 - 2021-11-01

### New Features:

* Now track (and report) names of on-foot CZs fought at, automatically determine CZ Low / Med / High, and automatically increment counts. Note that we still can't determine whether you've actually _won_ the CZ, so we count it as a win if you've fought there.
* Now track Exobiology data sold.
* New setting to show/hide tabs for systems that have no BGS activity, default to show.

### Changes:

* Bounty vouchers redeemed on Fleet Carriers now count only 50% of the value.
* Added scrollbar to Discord report.
* When plugin is launched for the very first time, default it to 'Enabled' so it's immediately active.
* Reorganisation and tidy up of settings panel, and add link to help pages.
* The Discord text field and fields in the settings panel now have right-click context menus to Copy, Paste etc.


## v1.6.0 - 2021-10-03

### New Features:

* Now count primary and secondary mission INF separately: Primary INF is for the original mission giving faction and secondary INF is for any target faction(s) affected by the mission. An option is included to exclude secondary INF from the Discord report *
* Discord options are now shown on the main tally windows as well as in the settings.

### Bug Fixes:

* Only count `War` or `Civilwar` missions for the originating faction (thanks @RichardCsiszarik for diagnosing and fixing this).

### Changes:

* Added on-foot scavenger missions and on-foot covert assassination missions to those that count when in `War` or `CivilWar` states.
* Tweaks to window layouts and wording.
* No longer allow mouse wheel to change field values, to help avoid accidental changes.
* Since Odyssey update 7, +INF is now reported for missions for factions in `Election`, `War` and `CivilWar` states. We still report this +INF separately from normal +INF, but have changed the wording to `ElectionINF` / `WarINF` instead of `ElectionMissions` and `WarMissions`.

_* Note that the plugin only tracks primary and secondary INF from this version onwards - all INF in older reports will still be categorised as primary INF._


## v1.5.0 - 2021-09-16

### New features:

* Now count and report certain mission types for factions in the `War` or `CivilWar` states, similarly to how some mission types in `Election` state are counted (gathering a full list of mission types that count when the faction is in conflict is still a work in progress).
* If faction is in state `Election`, `War` or `CivilWar`, don't report fake +INF, instead state the number of election / war missions completed, to avoid confusion.

### Changes:

* Tweaks to window layouts and wording.


## v1.4.0 - 2021-09-09

### New features:

* Can integrate directly with Discord to post messages to a channel, using a user-specified Discord webhook.
* Prefix positive INF with '+'.
* Mission INF is now manually editable as well as automatically updated.
* 'Select all' / 'Select none' checkbox at the top of each system to quickly enable / disable all factions for a system.
* Added 'Failed Missions' to Discord text.

### Bug Fixes:

* Apostrophes in Discord text no longer breaks the colouring.


## v1.3.0 - 2021-09-06

### New features:

* Conflict Zone options are now only presented for factions in `CivilWar` or `War` states.
* The option is now provided to omit individual factions from the report.
* There is a new option in the settings panel to switch on shortening of faction names to their abbreviations. This makes the report less readable but more concise.
* As a suggestion from a user (thanks CMDR Strasnylada!), we now use CSS coloured formatting blocks in the Discord text, which makes it look cleaner and clearer.

### Changes:

* The on-screen layout of the tally table has been improved.


## v1.2.0 - 2021-09-03

### New features:

* Ability to manually add High, Medium and Low on-foot and in-space Combat Zone wins to the Discord report by clicking on-screen buttons.

### Changes:

* Now include a lot more non-violent mission types when counting missions for a faction in the `Election` state (gathering a full list of non-violent mission types is still a work in progress).
* Improvements to layout of window.
* Rename buttons and windows to 'Latest BGS Tally' and 'Previous BGS Tally'.
* The last tick date and time presentation has been improved.


## v1.1.1 - 2021-08-31

### Bug Fixes:

* Now honour the 'Trend' for mission Influence rewards: `UpGood` and `DownGood` are now treated as *+INF* while `UpBad` and `DownBad` are treated as *-INF*.

### Changes:

* Report both +INF and -INF in Discord message.
* Various improvements to README:
    * Improved installation instructions.
    * Added instructions for upgrading from previous version.
    * Added personal data and privacy section.


## v1.1.0 - 2021-08-31

### Changes:

* Changed 'Missions' to 'INF' in Discord text.
* Removed 'Failed Missions' from Discord text.
* Made windows a bit wider to accommodate longer faction names.
* Changed plugin name to just 'BGS Tally' in settings.
* Improvements to the usage instructions in README.
* Renamed buttons to 'Latest Tick Data' and 'Earlier Tick Data' to more clearly describe what each does, avoiding the use of day-based terms 'Yesterday' and 'Today'.


## v1.0.0 - 2021-08-27

Initial release, based on original [BGS-Tally-v2.0 project by tezw21](https://github.com/tezw21/BGS-Tally-v2.0)

### New features:

* Now creates a Discord-ready string for copying and pasting into a Discord chat.
* _Copy to Clipboard_ button to streamline copying the Discord text.

### Bug fixes:

* Typo in 'Missions' fixed

### Other changes:

* Now logs to the EDMC log file, as per latest EDMC documentation recommendations.
