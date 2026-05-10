# DEX Smart Alerts

## Overview

DEX Smart Alerts lets your AI agent create, execute, and manage fully autonomous persistent market monitoring workflows for any token on OKX DEX.

Core operations:

* Create recurring cron-based token monitors
* Continuously fetch live token prices using `okx-dex-market`
* Monitor tokens automatically at configurable intervals
* Detect breakout, support, resistance, pump, dump, and volatility conditions
* Send real-time notifications to configured OpenClaw Channels (Telegram, Discord, etc.)
* Manage monitoring intervals, cooldowns, expiration, and recurring alert workflows
* Execute recurring autonomous monitoring loops without manual interaction

The skill supports natural language requests ranging from beginner-friendly monitoring to advanced trader automation workflows.

Example requests:

* Monitor BTC every 1 minute
* Track ETH every 5m and send updates
* Alert me if SOL breaks resistance
* Watch BONK volatility tonight
* Notify me if PEPE pumps 10%
* Monitor meme coins continuously

Execution workflow:

User Request
→ Create Cron Schedule
→ Fetch OKX DEX Market Data
→ Evaluate Trigger Conditions
→ Format Alert Message
→ Send Notification
→ Repeat Continuously

The skill behaves as an autonomous monitoring agent, not a passive reminder system.

Tags: `okx` `dex` `alerts` `cron` `monitoring` `notifications` `telegram` `trading` `automation` `autonomous-agent`

---

## Prerequisites

* OKX Onchain OS Agent connected
* `okx-dex-market` skill installed
* OpenClaw cron jobs enabled
* At least one notification Channel configured in OpenClaw
* Telegram Bot token and Channel ID configured if using Telegram
* Internet access for recurring market checks
* OpenClaw tool execution permissions enabled

Required tools:

* `okx-dex-market`
* `cron`
* `telegram.sendMessage`

Supported notification channels:

* Telegram
* Discord
* Other OpenClaw-supported channels

---

## Quick Start

1. Install this skill

2. Configure your notification channel in OpenClaw

Telegram example:

* Add your bot token
* Add your Telegram Channel or Group chat ID
* Add the bot to the Channel or Group
* Grant bot permission to send messages
* Verify bot permissions

3. Create autonomous monitoring workflows using natural language

Examples:

* Monitor BTC every 1 minute
* Watch ETH every 5 minutes
* Notify me if BTC breaks above 70000
* Alert me if SOL dumps 7%
* Track meme coins tonight
* Monitor PEPE continuously

4. The skill automatically:

* Creates recurring cron jobs
* Fetches live OKX DEX market data
* Evaluates trigger conditions
* Formats alert messages
* Sends notifications automatically

5. Monitoring continues persistently until explicitly stopped

6. Notifications are delivered directly to your configured OpenClaw channel
