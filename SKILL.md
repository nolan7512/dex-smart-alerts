---

name: dex-smart-alerts
version: "1.0.0"

description: >
  Fully autonomous persistent OKX DEX monitoring and smart alert system
  for OpenClaw using recurring cron workflows, live market tracking,
  breakout detection, volatility monitoring, and Telegram/Discord notifications.

author:
  name: "Nolan"

tags:
  - alerts
  - monitoring
  - trading
  - cron
  - okx-dex
  - smart-alerts
  - telegram
  - notifications
  - automation
  - autonomous-agent
  - market-monitoring

---

# DEX Smart Alerts

## Overview

DEX Smart Alerts lets your AI agent create, execute, and manage fully autonomous persistent market monitoring workflows for any token on OKX DEX.

The skill continuously fetches real-time market data using `okx-dex-market`, evaluates trigger conditions, and sends notifications through configured OpenClaw channels such as Telegram or Discord.

Execution workflow:

User Request
→ Parse Monitoring Intent
→ Create Recurring Cron Job
→ Call `okx-dex-market`
→ Fetch Live Market Data
→ Evaluate Conditions
→ Format Alert Message
→ Send Telegram / Discord Notification
→ Repeat Continuously

The skill behaves as an autonomous monitoring agent, NOT a passive reminder system.

---

# Autonomous Runtime Behavior

When users request:

* recurring monitoring
* token watching
* market tracking
* recurring updates
* breakout monitoring
* support/resistance alerts
* volatility tracking
* pump/dump notifications

the agent MUST:

1. Create recurring cron workflows
2. Continuously call `okx-dex-market`
3. Fetch fresh live token market data
4. Evaluate trigger conditions
5. Format trader-friendly alerts
6. Send notifications automatically
7. Continue monitoring until explicitly stopped

The agent MUST NEVER:

* only acknowledge requests
* behave as a reminder app
* send static placeholder notifications
* skip live market fetches

The agent MUST ALWAYS fetch fresh market data before sending notifications.

---

# Required Runtime Execution

For every recurring monitor:

1. Parse:

   * token/pair
   * interval
   * trigger conditions
   * expiration
   * notification target

2. Create recurring cron job

3. On EVERY cron execution:

   * call `okx-dex-market`
   * fetch:

     * live token price
     * 24h change
     * volatility
     * market context
   * evaluate trigger conditions
   * generate alert summary
   * send Telegram / Discord notification

4. Repeat continuously until stopped

---

# Mandatory Tool Usage

Recurring monitoring MUST use:

* `cron`
* `okx-dex-market`
* `telegram.sendMessage`

The workflow MUST be:

Cron Trigger
→ `okx-dex-market`
→ Live Market Fetch
→ Trigger Evaluation
→ Alert Formatting
→ Telegram Notification
→ Repeat

The agent MUST NEVER send Telegram updates without first calling `okx-dex-market`.

---

# Core Capabilities

## Fixed Price Alerts

Examples:

* alert when ETH > 3000
* notify when BTC < 60000

---

## Percentage Move Alerts

Examples:

* alert when SOL pumps 10%
* notify if PEPE dumps 15%

---

## Breakout Monitoring

Examples:

* watch BTC breakout above resistance
* tell me when ETH breaks support

---

## Volatility Monitoring

Examples:

* monitor BONK volatility
* detect unusual movement
* monitor meme coin expansion

---

## Persistent Monitoring

Examples:

* monitor BTC every 1 minute
* track ETH every 5m
* monitor SOL continuously
* keep watching DOGE all day

---

# Trigger Coverage Matrix

The skill should recognize ALL of the following as autonomous recurring monitoring requests.

## Standard Trading Phrases

* "Set alert for ETH below 2800"
* "Notify me if BTC goes above 70000"
* "Create alert for SOL at 180"

---

## Casual Language

* "Ping me if BTC dumps"
* "Tell me if ETH pumps hard"
* "Watch SOL for me"

---

## Trader Slang

* "Watch for giga pump"
* "Notify me if market nukes"
* "Track if BTC loses support"

---

## Monitoring Requests

* "Monitor WIF every 5m"
* "Track BONK all day"
* "Watch meme coins tonight"

---

## Beginner-Friendly Language

* "Tell me if ETH price drops"
* "Can you watch SOL for me?"
* "Let me know when BTC crashes"

---

# Notification Format

Alerts should always include:

* token name
* current price
* trigger condition
* interval
* timestamp
* short market context

---

## Example Standard Monitor

🟢 BTC Monitor

Price: $103,442
24h: +1.28%
Interval: 1m
Time: 2026-05-10 12:45 UTC

---

## Example Breakout Alert

🚀 BTC Breakout Detected

Current Price: $70,520
Resistance: $70,000
Move: +3.4%

---

## Example Dump Alert

🔴 ETH Dump Alert

Current Price: $2,788
Drop: -8.2%

---

# Notification Channels

Supported:

* Telegram
* Discord
* Other OpenClaw-supported channels

---

# Telegram Configuration

1. Create bot using BotFather
2. Add bot to group/channel
3. Grant send message permission
4. Configure:

   * bot token
   * chat ID
5. Verify delivery

---

# Reliability Rules

## Price Fetch Failure

* retry up to 3 times
* fallback to secondary price source if available
* continue monitoring loop
* notify only if retries fail

---

## Cron Failure

* retry cron creation
* verify recurring persistence

---

## Notification Failure

* retry failed sends
* avoid duplicate notifications
* preserve monitor state

---

# Cooldown Rules

Prevent duplicate spam alerts:

* minimum cooldown window
* suppress repeated triggers

---

# Expiration Rules

* default expiration: 7 days
* stale monitors auto-expire
* expired monitors cleaned automatically

---

# Edge Cases

Handle:

* invalid token symbols
* delisted assets
* temporary API outages
* duplicate cron jobs
* repeated volatility triggers

---

# Security Model

This skill:

* monitors markets
* sends notifications
* creates recurring workflows

This skill DOES NOT:

* execute trades
* store private keys
* manage funds
* access wallets

---

# Required Skills

* okx-dex-market

---

# Required Tools

* cron
* okx-dex-market
* telegram.sendMessage

---

# Example User Requests

* Monitor BTC every 1 minute
* Track ETH every 5m and send Telegram updates
* Alert me if SOL pumps 10%
* Watch BTC breakout above 70k
* Monitor meme coins continuously

---

# Runtime Philosophy

This skill is designed to behave like a proactive autonomous market monitoring agent.

The workflow prioritizes:

* persistent monitoring
* real market data fetching
* automatic recurring execution
* trader-friendly notifications
* low-friction setup
* reliable alert delivery

The agent should behave like an always-running crypto market assistant, not a passive alert bot.
