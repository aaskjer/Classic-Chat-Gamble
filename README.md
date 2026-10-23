<p align="center">
  <img src="https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Assets/CCG/Classic-Chat-Gamble-Logo.png?raw=true" alt="Classic Chat Gamble logo" width="320" height="320">
</p>

<h1 align="center">Classic Chat Gamble</h1>

<p align="center">
  <b>The most classic chat game, built for streamer.bot and played on Twitch, YouTube and Kick.</b>
</p>

<p align="center">
  <img alt="Supported platforms" src="https://img.shields.io/badge/supported_platforms-Twitch%2C_YouTube%2C_Kick-white">
  <img alt="Tool" src="https://img.shields.io/badge/tool-streamer.bot-0b73ff">
  <img alt="GitHub License" src="https://img.shields.io/github/license/aaskjer/Classic-Chat-Gamble">
  <img alt="GitHub Release" src="https://img.shields.io/github/v/release/aaskjer/Classic-Chat-Gamble">
  <img alt="GitHub Downloads" src="https://img.shields.io/github/downloads/aaskjer/Classic-Chat-Gamble/total">
</p>

<p align="center">
  <a href="https://github.com/aaskjer/Classic-Chat-Gamble/releases"><b>Download</b></a> ·
  <a href="https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Setup-Guide.md"><b>Setup Guide</b></a> ·
  <a href="https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/FAQ.md"><b>FAQ</b></a> ·
  <a href="https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Import-String.md"><b>Import string</b></a>
</p>

---

## ✨ Features

- 🎲 **Bet your way**: numbers, keywords (`all`, `half`, `quarter`, `third`, `random`), percentages (`50%`) or shorthand (`10k`, `2.5m`, `1b`).
- 🎰 **Jackpots** with their own chance and multiplier, on top of the normal win. One Fairness slider sets all the odds, or you fine-tune them by hand.
- 🆓 **Free play**, either permanently or switched on and off by command, so viewers can gamble without spending any points.
- 🎫 **Twitch Channel Points**: run the game on a reward instead of the chat command, with four bet modes. YouTube and Kick keep the chat command.
- ⏱️ **Cooldowns** for everyone and per viewer, each with its own chat message.
- 🚫 **Blocked and addicted viewers**: keep viewers or Streamer.bot groups from playing, or cut the winnings of addicted ones.
- 💰 **Your points system**: [Currency Core by StreamUP](https://streamup.tips/product/currency-core) and [LOYALTY POINTS by tawmae](https://tawmae.xyz/loyalty-points) are detected on their own, and your own system works too.
- 💬 **Every message is yours**: edit or translate any chat message (win, loss, jackpot, cooldown, errors, free game) and see it in a chat preview.
- 📜 **Daily log** of every gamble and refund, searchable and filterable right in the settings window.
- 🖥️ **Settings window** with dark and light mode and `Try a bet`, which plays a round with your odds and shows the exact chat message.

---

## 🎮 How It Works

Viewers play with `!gamble` or by redeeming a Channel Point reward. Each gamble rolls against your odds:

| Outcome | When | Payout |
|---------|------|--------|
| 🎰 **Jackpot** | Roll ≤ Jackpot % | `bet × random(Min×–Max×) × Jackpot×` |
| 🎉 **Win** | Roll ≤ Win %, on top of the jackpot chance | `bet × random(Min×–Max×)` |
| ❌ **Loss** | Everything else | `-bet` |

Wins and jackpots are paid on top of the bet.

---

## 💬 Commands

| Command | Who | What it does |
|---------|-----|--------------|
| `!gamble <amount>` (or `!gambel`) | Everyone | Plays a round. Without an amount, the Default bet is used. |
| `!SetFreeGamble` | Moderators | Turns Free Game Mode on: nobody pays or wins points. |
| `!EndFreeGamble` | Moderators | Turns Free Game Mode off again. |
| `!gambleaddict add <name>` / `remove <name>` | Moderators | Puts a viewer on the addicted list or takes them off. |

---

## 🎫 Channel Points Mode (Twitch only)

With `Channel points` picked, the chat command is off on Twitch, and only viewers who redeem the configured reward can play there. YouTube and Kick keep using the chat command. Four bet modes are available:

| Mode | What is bet |
|------|-------------|
| **Reward cost** | The reward's price |
| **Typed amount** | What the viewer types into the reward, paid from their own points |
| **Fixed** | The same configured amount on every redemption |
| **Free** | Nothing: every redemption plays for free |

A redemption that doesn't end in a gamble is refunded.

---

## 🚀 Get Started

- [Setup Guide](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Setup-Guide.md)
- [Frequently Asked Questions](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/FAQ.md)
- [Import String for streamer.bot](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Import-String.md)
- [Download](https://github.com/aaskjer/Classic-Chat-Gamble/releases)

---

## ❤️ Credits & Links

- [aaskjer on Twitch](https://twitch.tv/aaskjer)
- [aaskjer.github.io](https://aaskjer.github.io/)
- [Classic Chat Gamble on SB Discord](https://discord.com/channels/834650675224248362/1446874050310836396/1446874050310836396)
- [Streamer.bot](https://streamer.bot) / [nate1280](https://www.patreon.com/c/nate1280/home)
- YOU ♡
