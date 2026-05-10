# DEX Smart Alerts

## Overview

DEX Smart Alerts lets your AI agent create and manage intelligent persistent price alerts for any token on OKX DEX.

Core operations:

* Set fixed or percentage-based price alerts
* Monitor tokens continuously using OpenClaw cron jobs
* Detect breakout, support, resistance, pump, and dump conditions
* Send notifications to configured OpenClaw Channels (Telegram, Discord, etc.)
* Manage alerts, monitoring intervals, cooldowns, and expiration

The skill supports natural language requests ranging from beginner-friendly phrases to advanced trader monitoring workflows.

Tags: `okx` `dex` `alerts` `cron` `monitoring` `notifications` `telegram` `trading`

---

## Prerequisites

* OKX Onchain OS Agent connected
* `okx-dex-market` skill installed
* OpenClaw cron jobs enabled
* At least one notification Channel configured in OpenClaw
* Telegram Bot token and Channel ID configured if using Telegram
* Internet access for recurring market checks

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
* Verify bot permissions

3. Create alerts using natural language

Examples:

* Set alert for ETH below 2800
* Notify me if BTC breaks above 70000
* Watch SOL every 5 minutes
* Ping me if PEPE pumps 10%
* Monitor meme coins tonight

4. Alerts will be monitored automatically using recurring cron jobs

5. Notifications are sent directly to your configured channel when conditions trigger
