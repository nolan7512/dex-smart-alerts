---
name: dex-smart-alerts
version: "1.1.0"

description: >
  Create persistent smart price alerts for OKX DEX using OpenClaw cron monitoring.
  Supports natural language triggers, recurring monitoring, breakout alerts,
  percentage moves, support/resistance watching, and intelligent notifications.

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
---

# OKX Smart Alerts

## Overview

OKX Smart Alerts allows users to create intelligent persistent market alerts using OKX DEX price data and OpenClaw cron jobs.

The skill continuously monitors token prices and sends notifications through the user's configured OpenClaw notification channel (Telegram, Discord, etc).

This skill is optimized for:

* active traders
* swing traders
* breakout monitoring
* meme coin monitoring
* support/resistance tracking
* hands-free market watching

The goal is to reduce manual chart watching and simplify recurring market monitoring workflows.

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

### Volatility Monitoring

* alert on sudden movement
* detect rapid price expansion
* monitor unusual market activity

---

# Trigger Coverage Matrix

The user may express intent in many different ways.

The skill should recognize all of the following as monitoring or alert requests.

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

# Keywords

price alert, market watch, monitor token, breakout alert,
support alert, resistance alert, pump alert, dump alert,
persistent monitoring, cron alert, volatility watcher,
trading notification, market tracking, telegram alerts,
crypto monitoring, smart notifications

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

## Telegram Bot API Format

```text
https://api.telegram.org/[bot-token]/sendMessage?chat_id=[chat-id]&text=[message]
```

## Telegram Message Payload Example

```text
  "🚨 ALERT TRIGGERED\n\nToken: ETH\nCurrent Price: $2788\nCondition: Below $2800\nInterval: 5m\nTime: 2026-05-09 14:00 UTC\n\nSuggested Action:\nReview momentum or prepare follow-up trade execution."
```

## Supported Notification Channels

* Telegram
* Discord
* Other OpenClaw-supported channels

## Notification Flow

Market Check
→ Trigger Condition
→ OpenClaw Notification Channel
→ Telegram / Discord Delivery

---

# Pre-flight Checks

Before creating alerts:

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

# Commands

## Create Alert

Examples:

* "Set alert for ETH below 2800"
* "Watch BTC breakout above 70k"
* "Monitor PEPE every 5 minutes"
* "Alert me if SOL pumps 10%"

Supported options:

* fixed price
* percentage moves
* breakout monitoring
* recurring checks
* expiration windows

---

## List Alerts

Examples:

* "Show my alerts"
* "List active monitors"
* "What alerts are running?"

---

## Delete Alert

Examples:

* "Delete BTC alert"
* "Remove monitor #12"

---

## Status Check

Examples:

* "Check alert status"
* "Verify notifications"
* "Is monitoring running?"

---

# Notification Format

When an alert triggers, always include:

* token name
* current price
* target condition
* timestamp
* monitoring interval
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

# Output Contract

All triggered alerts should contain:

1. token name
2. current price
3. trigger condition
4. timestamp
5. monitoring interval
6. short momentum context
7. suggested next action

The skill should prioritize concise and trader-friendly outputs.

---

# Reliability Rules

## Error Handling

### Price Fetch Failure

* retry up to 3 times
* fallback to index price
* notify only if all retries fail

### Cron Failure

* retry cron creation twice
* verify persistence after creation

### Notification Failure

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

# Do Not Use This Skill For

This skill is NOT designed for:

* direct swap execution
* arbitrage execution
* portfolio management
* high-frequency trading
* automated leverage trading

This skill focuses specifically on persistent monitoring and notifications.

---

# Recommended Companion Skills

* okx-dex-swap
* okx-wallet-portfolio
* okx-dex-token
* okx-market-scanner

---

# Design Philosophy

This skill is designed to reduce manual chart watching and make market monitoring more accessible.

The workflow prioritizes:

* low friction setup
* flexible natural language
* persistent monitoring
* reliable notifications
* trader-friendly outputs

The skill should behave like a proactive market assistant rather than a simple alert bot.
