# DEX Smart Alerts

## Overview

DEX Smart Alerts lets your AI agent create and manage intelligent persistent price alerts for any token on OKX DEX.

Core operations:
- Set fixed or percentage-based price alerts
- Monitor tokens continuously using OpenClaw cron jobs
- Detect breakout, support, resistance, pump, and dump conditions
- Send notifications to your configured OpenClaw Channel (Telegram, Discord, etc.)
- Manage alerts, monitoring intervals, cooldowns, and expiration

The skill supports natural language requests ranging from beginner-friendly phrases to advanced trader monitoring workflows.

Tags: `okx` `dex` `alerts` `cron` `monitoring` `notifications` `trading` `market-watch`

---

## Prerequisites

- OKX Onchain OS Agent connected
- `okx-dex-market` skill installed
- OpenClaw cron jobs enabled
- At least one OpenClaw notification Channel configured
  - Telegram recommended
  - Discord supported
- Internet access for recurring market checks
- Optional funded wallet for future swap workflows

---

## Quick Start

1. Install this skill
2. Verify OpenClaw notification Channel is configured
3. Create alerts using natural language

Examples:
- Set alert for ETH below 2800
- Notify me if BTC breaks above 70000
- Watch SOL every 5 minutes
- Ping me if PEPE pumps 10%
- Monitor meme coins tonight

You can also:
- Show all active alerts
- Delete existing monitors
- Check monitoring health status
- Verify notification delivery

Alerts are monitored automatically using OpenClaw cron jobs and delivered to your configured notification Channel.