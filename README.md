# DEX Smart Alerts

Fully autonomous persistent OKX DEX monitoring and smart alert system for OpenClaw using recurring cron workflows, real-time market tracking, breakout detection, volatility monitoring, and Telegram/Discord notifications.

---

# Table of Contents

* Overview
* Core Features
* Autonomous Monitoring Workflow
* Supported Monitoring Types
* Architecture
* Prerequisites
* Installation
* Telegram Setup
* OpenClaw Setup
* Quick Start
* Natural Language Examples
* Monitoring Behavior
* Notification Workflow
* Alert Formats
* Reliability & Retry Logic
* Cooldown & Expiration
* Runtime Behavior
* Security Model
* Example Notification Payloads
* Required Tools
* Recommended Companion Skills
* Troubleshooting
* FAQ
* Design Philosophy

---

# Overview

DEX Smart Alerts allows your AI agent to create, execute, and manage fully autonomous persistent market monitoring workflows for OKX DEX assets.

The skill continuously monitors live token prices using OpenClaw recurring cron jobs and automatically sends notifications through configured OpenClaw communication channels such as Telegram or Discord.

The system is designed for:

* active traders
* swing traders
* breakout monitoring
* meme coin tracking
* support/resistance monitoring
* volatility alerts
* recurring market updates
* hands-free market watching

The goal is to reduce manual chart watching while keeping traders informed of important market movements in real time.

---

# Core Features

## Autonomous Monitoring

* Fully autonomous recurring monitoring workflows
* Continuous OKX DEX market tracking
* Automatic cron execution
* Persistent recurring monitors
* Automatic notification delivery

---

## Smart Alert System

* Fixed price alerts
* Percentage movement alerts
* Breakout detection
* Support/resistance monitoring
* Volatility tracking
* Meme coin monitoring
* Range breakout detection

---

## Notification System

* Telegram notifications
* Discord notifications
* OpenClaw channel integration
* Trader-friendly alert formatting
* Persistent recurring updates

---

## Reliability Features

* Retry & fallback handling
* Cron persistence validation
* Cooldown protection
* Duplicate suppression
* Alert expiration & cleanup

---

# Autonomous Monitoring Workflow

The skill behaves as an autonomous market monitoring agent.

Execution flow:

```text
User Request
→ Parse Monitoring Intent
→ Create Recurring Cron Job
→ Fetch Live OKX DEX Market Data
→ Evaluate Trigger Conditions
→ Format Alert Message
→ Send Telegram / Discord Notification
→ Repeat Continuously
```

The skill MUST NOT behave as:

* a passive reminder app
* acknowledgement-only scheduler
* simple timer

The skill MUST continuously fetch real market data and execute recurring monitoring loops.

---

# Supported Monitoring Types

## Fixed Price Monitoring

Examples:

* Alert when ETH goes above 3000
* Notify when BTC drops below 60000

---

## Percentage Move Monitoring

Examples:

* Alert if SOL pumps 10%
* Notify if PEPE dumps 15%

---

## Breakout Monitoring

Examples:

* Watch BTC breakout above resistance
* Notify if ETH loses support

---

## Volatility Monitoring

Examples:

* Monitor BONK volatility
* Alert on sudden meme coin movement

---

## Persistent Monitoring

Examples:

* Monitor WIF every 5 minutes
* Track DOGE for 24 hours
* Monitor BTC continuously

---

## Recurring Market Updates

Examples:

* Send BTC updates every minute
* Track ETH every 5m
* Watch SOL continuously

---

# Architecture

```text
User
→ OpenClaw Agent
→ DEX Smart Alerts Skill
→ OpenClaw Cron Jobs
→ OKX DEX Market Data
→ Trigger Evaluation
→ Notification Formatting
→ Telegram / Discord
```

---

# Prerequisites

Before using this skill, ensure the following components are available.

## Required

* OKX Onchain OS Agent
* OpenClaw installed
* OpenClaw cron jobs enabled
* `okx-dex-market` skill installed
* Notification channel configured
* Internet access

---

## Optional

* Telegram Bot
* Discord Webhook
* Additional monitoring skills

---

# Installation

## Step 1 — Install Skill

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

* Bot Token

---

## Step 2 — Create Telegram Group or Channel

Create:

* Group
  or
* Channel

Add your bot as admin.

Grant:

* Send Message permission

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

* Bot Token
* Chat ID

Verify the bot can send messages successfully.

---

# OpenClaw Setup

## Enable Cron Jobs

Ensure recurring jobs are enabled inside OpenClaw.

The skill relies on recurring cron execution for autonomous monitoring.

---

## Configure Notification Channels

Supported:

* Telegram
* Discord
* Other OpenClaw-supported channels

---

# Quick Start

## Example Commands

### Standard Monitoring

```text
Monitor BTC every 1 minute
```

---

### Fixed Price Alert

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

# Monitoring Behavior

For every recurring monitor:

1. Parse monitoring intent
2. Detect token/pair
3. Detect timeframe
4. Detect trigger conditions
5. Create recurring cron job
6. Fetch live OKX DEX market data repeatedly
7. Evaluate trigger conditions
8. Format trader-friendly alerts
9. Send notifications automatically
10. Continue monitoring until explicitly stopped

---

# Notification Workflow

```text
Cron Trigger
→ Fetch Market Data
→ Evaluate Conditions
→ Validate Alert State
→ Format Notification
→ Telegram / Discord Delivery
→ Wait For Next Cron Execution
```

---

# Alert Formats

## Standard Monitor

```text
🟢 BTC Monitor

Price: $103,442
24h: +1.28%
Interval: 1m
Time: 2026-05-10 12:45 UTC
```

---

## Breakout Alert

```text
🚀 BTC Breakout Detected

Current Price: $70,520
Resistance: $70,000
Move: +3.4%
```

---

## Dump Alert

```text
🔴 ETH Dump Alert

Current Price: $2,788
Drop: -8.2%
```

---

## Volatility Alert

```text
⚡ BONK Volatility Spike

Range: 14%
Volume Surge: +220%
Interval: 5m
```

---

# Reliability & Retry Logic

## Price Fetch Failure

* Retry up to 3 times
* Fallback to secondary price source
* Continue monitoring loop
* Notify only if all retries fail

---

## Notification Failure

* Automatic retry handling
* Prevent duplicate sends
* Preserve monitoring state

---

## Cron Failure

* Retry cron creation
* Verify recurring persistence
* Restore monitoring automatically

---

# Cooldown & Expiration

## Cooldown

Prevents duplicate spam notifications during rapid volatility.

---

## Expiration

Default monitor expiration:

* 7 days

Expired monitors should auto-clean when supported.

---

# Runtime Behavior

The skill MUST:

* continuously fetch real market data
* create recurring cron jobs
* send automatic notifications
* behave as an autonomous monitoring agent

The skill MUST NEVER:

* only acknowledge requests
* behave as a reminder app
* stop monitoring unless instructed

---

# Security Model

## This Skill DOES

* Monitor markets
* Send notifications
* Create recurring monitoring workflows
* Fetch public market data

---

## This Skill DOES NOT

* Execute trades
* Store private keys
* Manage funds
* Perform arbitrage
* Access wallets

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

# Required Tools

* cron
* okx-dex-market
* telegram.sendMessage

---

# Recommended Companion Skills

* okx-dex-market
* okx-dex-swap
* okx-wallet-portfolio
* okx-market-scanner

---

# Troubleshooting

## Alerts Not Triggering

Check:

* cron jobs enabled
* token symbol valid
* monitoring interval correct
* notification channel configured
* `okx-dex-market` installed

---

## Telegram Not Sending

Check:

* bot token valid
* bot added to group/channel
* bot has admin permission
* correct chat ID

---

## Duplicate Alerts

Verify cooldown configuration is active.

---

## Cron Not Running

Check:

* OpenClaw cron enabled
* recurring jobs active
* OpenClaw gateway running

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

## Does monitoring continue automatically?

Yes.

Recurring monitoring continues until:

* user stops it
* expiration is reached
* monitor is deleted

---

# Design Philosophy

DEX Smart Alerts is designed to behave like a proactive autonomous market assistant instead of a simple alert bot.

The workflow prioritizes:

* low friction setup
* natural language flexibility
* autonomous execution
* persistent monitoring
* reliable notifications
* trader-friendly outputs

The system is optimized for real-world crypto monitoring workflows while remaining lightweight, safe, and automation-focused.
