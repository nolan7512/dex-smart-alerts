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

DEX Smart Alerts is a fully autonomous recurring crypto market monitoring skill for OpenClaw.

The skill continuously monitors token prices using OKX DEX market tools, evaluates trigger conditions, and automatically sends notifications through Telegram, Discord, or other OpenClaw-supported channels.

The system is optimized for:

* active traders
* swing traders
* breakout monitoring
* meme coin tracking
* volatility detection
* support/resistance monitoring
* hands-free recurring market watching

Execution workflow:

User Request
→ Create Recurring Cron Job
→ Call `okx-dex-market`
→ Fetch Live Market Data
→ Evaluate Trigger Conditions
→ Format Trader-Friendly Alert
→ Send Telegram / Discord Notification
→ Repeat Continuously

The skill behaves as an autonomous monitoring agent, NOT a passive reminder system.

---

# Autonomous Runtime Rules

When users request:

* recurring monitoring
* token tracking
* market watching
* recurring updates
* volatility monitoring
* breakout alerts
* support/resistance alerts
* pump/dump notifications

the agent MUST:

1. Create recurring cron workflows
2. Continuously fetch fresh market data
3. Evaluate conditions automatically
4. Send trader-friendly notifications
5. Continue monitoring until explicitly stopped

The agent MUST NEVER:

* only acknowledge requests
* behave as a reminder app
* send placeholder notifications
* skip live market fetches

The agent MUST ALWAYS fetch fresh market data before sending notifications.

---

# Mandatory Execution Contract

For EVERY recurring monitor:

1. Parse:

   * token
   * pair
   * interval
   * trigger conditions
   * expiration
   * notification target

2. Create recurring cron job

3. On EVERY cron execution:

   STEP 1:

   * call `okx-dex-market`
   * fetch:

     * live price
     * 24h change
     * volatility
     * market context

   STEP 2:
   If `okx-dex-market` fails:

   * call `okx-dex-token`
   * resolve token metadata
   * resolve token identifiers
   * attempt secondary token market lookup

   STEP 3:
   If BOTH tools fail:

   * use web search as final fallback
   * search live token market price
   * continue monitoring loop

   STEP 4:

   * evaluate trigger conditions
   * generate trader-friendly alert

   STEP 5:

   * send Telegram / Discord notification

4. Repeat continuously until stopped

---

# Mandatory Tool Priority

The agent MUST use tools in THIS EXACT ORDER:

1. `okx-dex-market`
2. `okx-dex-token`
3. web search fallback

The agent MUST NEVER:

* skip tool execution
* send fake prices
* hallucinate market data
* send notifications without fetching live data

---

# Required Cron Prompt Behavior

Every cron execution MUST behave like:

"You are executing the dex-smart-alerts autonomous monitoring skill."

The cron workflow MUST:

* rebind skill identity
* re-enable monitoring behavior
* re-enable tool usage instructions
* continue autonomous execution

The cron execution MUST NEVER revert to generic assistant behavior.

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

The skill should recognize ALL of the following as recurring monitoring requests.

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

Alerts should ALWAYS include:

* token name
* current price
* trigger condition
* interval
* timestamp
* short market context

---

## Standard Monitor Format

🟢 BTC Monitor

Price: $103,442
24h: +1.28%
Interval: 1m
Time: 2026-05-10 12:45 UTC

---

## Breakout Alert

🚀 BTC Breakout Detected

Current Price: $70,520
Resistance: $70,000
Move: +3.4%

---

## Dump Alert

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
* fallback to `okx-dex-token`
* fallback to web search
* continue monitoring loop
* notify only if all retries fail

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
* okx-dex-token

---

# Required Tools

* cron
* okx-dex-market
* okx-dex-token
* telegram.sendMessage
* web search fallback

---

# Example User Requests

* Monitor BTC every 1 minute
* Track ETH every 5m and send Telegram updates
* Alert me if SOL pumps 10%
* Watch BTC breakout above 70k
* Monitor meme coins continuously

---

# Runtime Philosophy

This skill is designed to behave like a proactive autonomous crypto market assistant instead of a passive alert bot.

The workflow prioritizes:

* persistent monitoring
* real market data fetching
* automatic recurring execution
* trader-friendly notifications
* low-friction setup
* reliable alert delivery
* fallback recovery logic

The agent should behave like an always-running market monitoring system with resilient tool fallback behavior.
