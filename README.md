<p align="center"><img src="https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Assets/CCG/Classic-Chat-Gamble-Logo.png?raw=true" alt="Classic Chat Gamble logo" width="400" height="400"></p>

The most classic chat game, built for streamer.bot and played on Twitch, YouTube and Kick.

![Static Badge](https://img.shields.io/badge/https%3A%2F%2Fimg.shields.io%2Fbadge%2Fany_text-Twitch%2C_Kick%2C_YouTube-white?label=supported%20platforms)
![Static Badge](https://img.shields.io/badge/https%3A%2F%2Fimg.shields.io%2Fbadge%2Fany_text-streamer.bot-white?label=tool&color=%230b73ff)
![GitHub License](https://img.shields.io/github/license/aaskjer/Classic-Chat-Gamble)
![GitHub Release](https://img.shields.io/github/v/release/aaskjer/Classic-Chat-Gamble)
![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/aaskjer/Classic-Chat-Gamble/total)

---

# Overview

- Viewers bet with numbers, keywords (`all`, `half`, `quarter`, `third`, `random`),
  percentages (`50%`) or shorthand (`10k`, `2.5m`, `1b`).
- A jackpot with its own chance and multiplier sits on top of the normal win. One Fairness slider sets all the odds, or you fine-tune them by hand.
- Free play, either permanently or switched on and off by command, lets viewers gamble without spending any points.
- On Twitch, the game can run on a Channel Point reward instead of the chat command,
  with four bet modes (`Reward cost`, `Typed amount`, `Fixed`, `Free`) explained in the settings window.
- Global and per-viewer cooldowns, with their chat messages set right in the settings window.
- Keep specific Streamer.bot groups or individual viewers from playing.
- Detects [Currency Core by StreamUP](https://streamup.tips/product/currency-core) and [LOYALTY POINTS by tawmae](https://tawmae.xyz/loyalty-points) on its own,
  and works with your own points system too.
- Every chat message (win, loss, jackpot, cooldown, errors, free game) can be edited in the settings window.
- A log file per day records every gamble; the built-in log viewer searches and filters it.
- A settings window with dark and light mode, five pages and `Try a bet`, which plays a round with your odds and shows the exact chat message.

---

## 🎮 How It Works

Viewers play with the chat command (`!gamble` by default) or by redeeming a Channel Point reward. Each gamble rolls against your odds:

| Outcome | When | Payout |
|---------|------|--------|
| 🎰 **Jackpot** | Roll ≤ Jackpot % | `bet × random(Min×–Max×) × Jackpot×` |
| 🎉 **Win** | Roll ≤ Win %, on top of the jackpot chance | `bet × random(Min×–Max×)` |
| ❌ **Loss** | Everything else | `-bet` |

---

## 🎫 Channel Points Mode (Twitch only)

With `Channel points` picked, the chat command is off on Twitch, and only viewers who redeem the configured reward can play there. YouTube and Kick keep using the chat command. Four bet modes are available:

| Option | Info |
|---------|---------|
| **Reward cost** | The reward's price is the bet |
| **Typed amount** | The viewer types their bet into the reward's text field |
| **Fixed** | Every redemption bets the same configured amount |
| **Free** | Every redemption plays for free, whatever it costs |

---

## Get Started

[Setup Guide](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Setup-Guide.md)

[Frequently Asked Questions](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/FAQ.md)

[Import String for streamer.bot](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Import-String.md)

[Download](https://github.com/aaskjer/Classic-Chat-Gamble/releases)

---

## Credits & Links


[aaskjer on Twitch](https://twitch.tv/aaskjer)

[Classic Chat Gamble on SB Discord](https://discord.com/channels/834650675224248362/1446874050310836396/1446874050310836396)

[Streamer.bot](https://streamer.bot) / [nate1280](https://www.patreon.com/c/nate1280/home)

YOU ♡
