# DEX Smart Alerts

Persistent intelligent market monitoring and price alert automation for OKX DEX using OpenClaw cron jobs and notification channels.

---

# Table of Contents

- Overview
- Features
- Supported Monitoring Types
- Architecture
- Prerequisites
- Installation
- Telegram Setup
- OpenClaw Setup
- Quick Start
- Natural Language Examples
- Alert Types
- Notification Workflow
- Reliability & Retry Logic
- Cooldown & Expiration
- Security Model
- Example Notification Payloads
- Recommended Companion Skills
- Troubleshooting
- FAQ
- Design Philosophy

---

# Overview

DEX Smart Alerts allows your AI agent to create and manage intelligent persistent market alerts for OKX DEX assets.

The skill continuously monitors token prices using OpenClaw cron jobs and sends notifications to your configured communication channels such as Telegram or Discord.

The system is designed for:
- active traders
- swing traders
- breakout monitoring
- meme coin tracking
- support/resistance monitoring
- volatility alerts
- hands-free market watching

The goal is to reduce manual chart watching while keeping traders informed of important market movements in real time.

---

# Features

## Core Features

- Persistent recurring market monitoring
- Natural language alert creation
- Smart breakout detection
- Percentage move monitoring
- Volatility alerts
- Telegram notifications
- Discord notifications
- OpenClaw cron integration
- Retry & fallback handling
- Cooldown protection against spam
- Alert expiration & cleanup

---

# Supported Monitoring Types

## Fixed Price Monitoring

Examples:
- Alert when ETH goes above 3000
- Notify when BTC drops below 60000

---

## Percentage Move Monitoring

Examples:
- Alert if SOL pumps 10%
- Notify if PEPE dumps 15%

---

## Breakout Monitoring

Examples:
- Watch BTC breakout above resistance
- Notify if ETH loses support

---

## Volatility Monitoring

Examples:
- Monitor BONK volatility
- Alert on sudden meme coin movement

---

## Persistent Monitoring

Examples:
- Monitor WIF every 5 minutes
- Track DOGE for 24 hours

---

# Architecture

```text
User
→ OpenClaw Agent
→ DEX Smart Alerts Skill
→ OKX DEX Market Data
→ OpenClaw Cron Jobs
→ Notification Channel
→ Telegram / Discord
```

---

# Prerequisites

Before using this skill, ensure the following components are available.

## Required

- OKX Onchain OS Agent
- OpenClaw installed
- OpenClaw cron jobs enabled
- `okx-dex-market` skill installed
- Notification channel configured
- Internet access

---

## Optional

- Telegram Bot
- Discord Webhook
- Additional monitoring skills

---

# Installation

## Step 1 — Clone or Copy Skill

Place the skill inside your plugin-store skills directory.

Example:

```bash
skills/dex-smart-alerts/
```

---

## Step 2 — Verify Required Skills

Ensure the following skill exists:

```text
okx-dex-market
```

---

## Step 3 — Validate Skill

Run local validation:

```bash
plugin-store lint skills/dex-smart-alerts
```

Expected result:

```text
✓ 0 errors
✓ 0 warnings
```

---

# Telegram Setup

## Step 1 — Create Telegram Bot

Open Telegram and search for:

```text
@BotFather
```

Create a bot and copy:
- Bot Token

---

## Step 2 — Create Telegram Group or Channel

Create:
- Group
or
- Channel

Add your bot as admin.

---

## Step 3 — Get Chat ID

Example API format:

```text
https://api.telegram.org/[bot-token]/getUpdates
```

Find:

```json
chat.id
```

---

## Step 4 — Configure OpenClaw Notification Channel

Add:
- Bot Token
- Chat ID

Verify bot can send messages.

---

# OpenClaw Setup

## Enable Cron Jobs

Ensure recurring jobs are enabled inside OpenClaw.

The skill relies on cron scheduling for persistent monitoring.

---

## Configure Notification Channel

Supported:
- Telegram
- Discord
- Other OpenClaw-supported channels

---

# Quick Start

## Example Commands

### Standard Monitoring

```text
Set alert for ETH below 2800
```

---

### Breakout Monitoring

```text
Watch BTC breakout above 70000
```

---

### Volatility Monitoring

```text
Monitor PEPE every 5 minutes
```

---

### Percentage Alerts

```text
Alert me if SOL pumps 10%
```

---

# Natural Language Examples

The skill supports flexible natural language requests.

---

## Beginner-Friendly

```text
Tell me if ETH price drops
```

```text
Can you watch SOL for me?
```

---

## Casual Language

```text
Ping me if BTC dumps
```

```text
Wake me up if PEPE flies
```

---

## Trader Slang

```text
Watch for giga pump
```

```text
Notify me if market nukes
```

---

## Power User

```text
Create recurring breakout monitor every 15m
```

```text
Track ARB volatility for 3 days
```

---

# Alert Types

## Fixed Price

Triggers when asset crosses a specified price.

---

## Percentage Change

Triggers after relative percentage movement.

---

## Range Breakout

Triggers when price exits monitored range.

---

## Volatility Detection

Triggers during sudden market expansion.

---

# Notification Workflow

```text
Market Check
→ Trigger Condition
→ Alert Validation
→ Notification Formatting
→ Telegram / Discord Delivery
```

---

# Example Notification Payloads

## Telegram API Format

```text
https://api.telegram.org/[bot-token]/sendMessage?chat_id=[chat-id]&text=[message]
```

---

## Example Alert Message

```text
🚨 ALERT TRIGGERED

Token: ETH
Current Price: $2788
Condition: Below $2800
Interval: 5m
Time: 2026-05-09 14:00 UTC

Suggested Action:
Review momentum or prepare follow-up trade execution.
```

---

# Reliability & Retry Logic

## Price Fetch Failure

- Retry up to 3 times
- Fallback to index price
- Notify only if all retries fail

---

## Notification Failure

- Automatic retry handling
- Prevent duplicate sends
- Preserve alert state

---

## Cron Failure

- Retry cron creation
- Verify recurring persistence

---

# Cooldown & Expiration

## Cooldown

Prevents duplicate spam notifications during rapid volatility.

---

## Expiration

Default alert expiration:
- 7 days

Expired alerts should auto-clean when supported.

---

# Security Model

## This Skill DOES

- Monitor markets
- Send notifications
- Create recurring checks

---

## This Skill DOES NOT

- Execute trades
- Store private keys
- Manage funds
- Perform arbitrage
- Access wallets

---

# Recommended Companion Skills

- okx-dex-market
- okx-dex-swap
- okx-wallet-portfolio
- okx-market-scanner

---

# Troubleshooting

## Alerts Not Triggering

Check:
- cron jobs enabled
- token symbol valid
- monitoring interval correct
- notification channel configured

---

## Telegram Not Sending

Check:
- bot token valid
- bot added to group
- bot has admin permission
- correct chat ID

---

## Duplicate Alerts

Verify cooldown configuration is active.

---

# FAQ

## Does this execute trades?

No.

This skill only monitors markets and sends notifications.

---

## Does this require wallet access?

No.

The skill is read-only.

---

## Can I use Discord instead of Telegram?

Yes.

Any OpenClaw-supported notification channel may be used.

---

# Design Philosophy

DEX Smart Alerts is designed to behave like a proactive market assistant instead of a simple alert bot.

The workflow prioritizes:
- low friction setup
- natural language flexibility
- persistent monitoring
- reliable notifications
- trader-friendly outputs

The system is optimized for real-world crypto monitoring workflows while remaining lightweight and safe.
