# BGS-Tally (modified by Aussi)

[![CodeQL](https://github.com/aussig/BGS-Tally/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/aussig/BGS-Tally/actions/workflows/codeql-analysis.yml)
[![GitHub Latest Version](https://img.shields.io/github/v/release/aussig/BGS-Tally)](https://github.com/aussig/BGS-Tally/releases/latest)
[![Github All Releases](https://img.shields.io/github/downloads/aussig/BGS-Tally/total.svg)](https://github.com/aussig/BGS-Tally/releases/latest)

A tool to track and report your Background Simulation (BGS) activity in Elite Dangerous, implemented as an [EDMC](https://github.com/EDCD/EDMarketConnector) plugin. BGS Tally counts all the BGS work you do for any faction, in any system.

Based on BGS-Tally v2.0 by tezw21: [Original tezw21 BGS-Tally-v2.0 Project](https://github.com/tezw21/BGS-Tally-v2.0)

This modified version includes automatic on-foot Conflict Zone tracking (with settlement names), manual in-space Conflict Zone tracking, Discord-ready information, quick Copy to Clipboard function for the Discord text and posting directly to Discord.


# Initial Installation and Use

Full instructions for **installation and use are [here in the wiki &rarr;](https://github.com/aussig/BGS-Tally/wiki)**.


# Updating from a Previous Version

Full instructions for **upgrading from a previous version are [here in the wiki &rarr;](https://github.com/aussig/BGS-Tally/wiki/Upgrade)**.


# Discord Integration

The plugin generates Discord-ready text for copying-and-pasting manually into Discord and also supports direct posting into a Discord server of your choice using a webhook. You will need to create this webhook on your Discord server first - **instructions for setting up the webhook within Discord are [here in the wiki &rarr;](https://github.com/aussig/BGS-Tally/wiki/Discord-Server-Setup)**.


# What is Tracked

The plugin includes both automatic and manual tracking of BGS activity data.

* For a basic summary of what is tracked, see the **[Home Page of the wiki &rarr;](https://github.com/aussig/BGS-Tally/wiki#it-tracks-bgs-activity)**.
* For more detail, see the **[Activity Window section in the wiki &rarr;](https://github.com/aussig/BGS-Tally/wiki/Use#activity-window)**.


# Your Personal Activity and Privacy

If you're concerned about the privacy of your BGS activity, note that this plugin **does not send your data anywhere, unless you specifically choose to by configuring the Discord Integration** (see above for instructions).

It writes the following three files, all in the BGS-Tally folder:

1. `Today.txt` - This contains your activity since the last tick.
2. `Yesterday.txt` - This contains your activity in your previous session before the last tick.
3. `MissionLog.txt` - This contains your currently active list of missions.

All three of these files use the JSON format, so can be easily viewed in a text editor or JSON viewer.

The plugin makes the following network connections:

1. To [EliteBGS](https://elitebgs.app/api/ebgs/v5/ticks) to grab the date and time of the lastest tick.
2. To [GitHub](https://api.github.com/repos/aussig/BGS-Tally/releases/latest) to check the version of the plugin to see whether there is a newer version available.
3. **Only if configured by you** to a specific Discord webhook on a Discord server of your choice, and only when you explicitly click the _Post to Discord_ button.
