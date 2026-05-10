# DEX Smart Alerts

## Overview

DEX Smart Alerts lets your AI agent create, execute, and manage fully autonomous persistent market monitoring workflows for any token on OKX DEX.

Core operations:

* Create recurring cron-based token monitors
* Continuously fetch live token prices using `okx-dex-market`
* Automatically fallback to `okx-dex-token` if market lookup fails
* Use web search as final fallback if both OKX tools fail
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
→ Generate Autonomous Task Assistant Prompt
→ Create Cron Schedule
→ Cron Trigger
→ Execute `okx-dex-market`
→ Fetch Live Market Data
→ Evaluate Trigger Conditions
→ Format Alert Message
→ Send Notification
→ Repeat Continuously

Fallback workflow:

`okx-dex-market`
→ `okx-dex-token`
→ web search fallback

The skill behaves as an autonomous monitoring agent, not a passive reminder system.

The agent MUST ALWAYS:

* fetch fresh market data before sending notifications
* execute monitoring loops continuously
* use live OKX DEX market data
* continue recurring cron execution until stopped

The agent MUST NEVER:

* only acknowledge monitoring requests
* behave as a passive reminder app
* send placeholder notifications
* skip market data fetching

Tags: `okx` `dex` `alerts` `cron` `monitoring` `notifications` `telegram` `trading` `automation` `autonomous-agent`

---

## Prerequisites

* OKX Onchain OS Agent connected
* `okx-dex-market` skill installed
* `okx-dex-token` skill installed
* OpenClaw cron jobs enabled
* At least one notification Channel configured in OpenClaw
* Telegram Bot token and Channel ID configured if using Telegram
* Internet access for recurring market checks
* OpenClaw tool execution permissions enabled

Required tools:

* `okx-dex-market`
* `okx-dex-token`
* `cron`
* `telegram.sendMessage`
* web search fallback

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

* Creates recurring cron jobs with autonomous Task Assistant Prompts
* Uses `okx-dex-market` to fetch live OKX DEX market data
* Falls back to `okx-dex-token` if market lookup fails
* Uses web search as final fallback if both OKX tools fail
* Evaluates trigger conditions
* Formats trader-friendly alert messages
* Sends notifications automatically to Telegram / Discord
* Continues recurring monitoring until stopped

5. Monitoring continues persistently until explicitly stopped

6. Notifications are delivered directly to your configured OpenClaw channel
