---

name: dex-smart-alerts
version: "2.0.0"

description: >

  Fully autonomous persistent OKX DEX monitoring and smart alert system for OpenClaw.
  Supports recurring cron workflows, live market monitoring, breakout detection,
  support/resistance tracking, volatility analysis, percentage-based alerts,
  and automatic Telegram/Discord notifications using real-time OKX DEX market data.

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
→ Parse Monitoring Intent
→ Create Cron Schedule
→ Fetch OKX DEX Market Data
→ Evaluate Trigger Conditions
→ Format Alert Message
→ Send Notification
→ Repeat Continuously

The skill behaves as an autonomous monitoring agent, NOT a passive reminder system.

---

# Autonomous Monitoring Behavior

When users request:

* monitoring
* recurring tracking
* token watching
* scheduled updates
* breakout alerts
* support/resistance watching
* volatility tracking
* pump/dump notifications

the agent MUST:

1. Create a recurring cron workflow
2. Automatically fetch live OKX DEX market data
3. Evaluate conditions continuously
4. Format trader-friendly alerts
5. Send notifications automatically
6. Continue monitoring until explicitly stopped

The skill MUST NEVER behave as:

* a simple timer
* reminder app
* acknowledgement-only scheduler

The skill MUST actively execute recurring market monitoring loops.

---

# Core Capabilities

## Supported Alert Types

### Fixed Price Alerts

* alert when ETH > 3000
* notify when BTC < 60000

### Percentage Move Alerts

* alert when SOL pumps 10%
* notify if PEPE dumps 15%

### Breakout Monitoring

* watch BTC breakout above resistance
* tell me when ETH breaks support

### Range Monitoring

* monitor if ARB leaves range
* watch WIF volatility

### Persistent Monitoring

* monitor BONK every 5 minutes
* keep watching DOGE for 24h
* track BTC continuously

### Volatility Monitoring

* alert on sudden movement
* detect rapid price expansion
* monitor unusual market activity

### Autonomous Recurring Updates

* send BTC updates every minute
* continuously monitor ETH market
* recurring SOL market reports

---

# Trigger Coverage Matrix

The user may express intent in many different ways.

The skill should recognize ALL of the following as recurring autonomous monitoring requests.

## Standard Trading Phrases

* "Set alert for ETH below 2800"
* "Notify me if BTC goes above 70000"
* "Create alert for SOL at 180"
* "Watch PEPE below support"

## Casual / Conversational

* "Ping me if BTC dumps"
* "Tell me if ETH pumps hard"
* "Watch SOL for me"
* "Keep an eye on DOGE"
* "Wake me up if PEPE flies"

## Trader Slang

* "Alert me on breakout"
* "Watch for giga pump"
* "Notify me if market nukes"
* "Track if BTC loses support"
* "Watch if ETH sends"

## Monitoring Requests

* "Monitor WIF every 5m"
* "Track BONK all day"
* "Watch meme coins tonight"
* "Keep tracking SOL volatility"

## Percentage-Based Requests

* "Notify if BTC moves 5%"
* "Alert if ETH drops 8%"
* "Ping me on 10% candle"

## Resistance / Support Language

* "Watch support at 2800"
* "Tell me if resistance breaks"
* "Monitor range breakout"

## Beginner-Friendly Language

* "I want to know when ETH price drops"
* "Can you alert me if SOL goes up?"
* "Let me know when BTC crashes"

## Power User Requests

* "Persistent breakout monitor for ARB"
* "Create recurring alert every 15m"
* "Track PEPE volatility for 3 days"

## Short / Compact Requests

* "btc alert pls"
* "eth watch"
* "sol notif"
* "track pepe"
* "watch btc asap"

## Emotional / Human Language

* "Warn me before market crashes"
* "Tell me if things go crazy"
* "Watch for panic selling"
* "Notify me if meme coins explode"

---

# Required Runtime Behavior

For every recurring monitor:

1. Parse token/pair
2. Determine timeframe
3. Determine trigger conditions
4. Create recurring cron job
5. On EVERY cron execution:

   * call `okx-dex-market`
   * fetch latest market data
   * evaluate conditions
   * format trader-friendly alert
   * send notification
6. Continue execution until stopped

The cron execution MUST repeatedly fetch real market data.

---

# Market Data Execution Pipeline

Execution flow:

Cron Trigger
→ Call `okx-dex-market`
→ Fetch Live Market Data
→ Evaluate Trigger Conditions
→ Generate Alert Context
→ Format Notification
→ Send Telegram/Discord Message
→ Wait Until Next Cron Execution

---

# Keywords

price alert, market watch, monitor token, breakout alert,
support alert, resistance alert, pump alert, dump alert,
persistent monitoring, cron alert, volatility watcher,
trading notification, market tracking, telegram alerts,
crypto monitoring, smart notifications,
autonomous monitoring, recurring market tracking

---

# Notification Channel Configuration

This skill uses OpenClaw notification Channels for alert delivery.

## Telegram Setup

1. Create a Telegram Bot using BotFather
2. Add the bot to your Telegram Group or Channel
3. Grant message sending permissions
4. Configure:

   * Telegram Bot Token
   * Telegram Chat ID
5. Verify delivery before enabling persistent monitoring

## Supported Notification Channels

* Telegram
* Discord
* Other OpenClaw-supported channels

---

# Notification Format

Triggered alerts should always include:

* token name
* current price
* trigger condition
* timestamp
* monitoring interval
* short market context
* suggested next action

Example:

🚨 ALERT TRIGGERED

Token: ETH
Current Price: $2788
Condition: Below $2800
Interval: 5m
Time: 2026-05-09 14:00 UTC

Suggested Action:
Review momentum or prepare follow-up trade execution.

---

# Pre-flight Checks

Before creating recurring monitors:

1. Verify `okx-dex-market` skill is installed
2. Verify OpenClaw notification channel exists
3. Verify cron jobs are enabled
4. Validate token symbol or address
5. Validate interval and expiration values

If validation fails:

* explain the issue clearly
* provide corrective action
* avoid creating broken cron jobs

---

# Reliability Rules

## Price Fetch Failure

* retry up to 3 times
* fallback to index price
* continue monitoring loop
* notify only if all retries fail

## Cron Failure

* retry cron creation twice
* verify cron persistence

## Notification Failure

* retry notification delivery
* rely on OpenClaw retry system
* log failed delivery attempts

---

# Cooldown Rules

Prevent duplicate spam alerts:

* minimum cooldown between notifications
* suppress repeated triggers inside cooldown window

---

# Expiration Rules

* default expiration: 7 days
* stale monitors should auto-expire
* expired alerts should be cleaned automatically

---

# Edge Cases

* Handle invalid token addresses gracefully
* Handle delisted assets
* Handle temporary RPC outages
* Prevent duplicate cron jobs
* Prevent repeated notifications during high volatility

---

# Security & Safety

* Read-only monitoring skill
* No trade execution
* No wallet access
* No private key storage
* Uses only configured OpenClaw notification channels

---

# Required Tools

* cron
* okx-dex-market
* telegram.sendMessage

---

# Do Not Use This Skill For

This skill is NOT designed for:

* direct swap execution
* arbitrage execution
* portfolio management
* high-frequency trading
* automated leverage trading

This skill focuses specifically on autonomous persistent monitoring and notifications.

---

# Design Philosophy

This skill is designed to reduce manual chart watching and make market monitoring more accessible.

The workflow prioritizes:

* low friction setup
* flexible natural language
* autonomous execution
* persistent monitoring
* reliable notifications
* trader-friendly outputs

The skill should behave like a proactive autonomous market assistant rather than a simple alert bot.
