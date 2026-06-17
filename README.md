<p align="center"><img src="https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Assets/CCG/Classic-Chat-Gamble-Logo.png?raw=true" alt="BsA banner" width="400" height="400"></p>

Most classic chat game built for streamer.bot, supporting twitch, kick, trovo and youtube.


---

# Overview

- Works on Twitch, YouTube, Trovo, and Kick  
- Viewers can bet with numbers, keywords (`all`, `half`, `quarter`, `third`, `random`),  
  percentages (`50%`), or shorthand notation (`10k`, `2.5m`, `1b`)  
- Configurable jackpot chance and multiplier on top of the standard win calculation.
- Enable free play either permanently or dynamically via commands, so viewers can gamble without spending any points  
-  Optionally lock the game exclusively to a Twitch Channel Point redemption,  
  with multiple bet modes (`cost`, `input`, `fixed`, `free`) explained in the GUI  
- Global and per-user cooldown durations with customizable chat messages directly in the GUI  
- Exclude specific Streamer.bot groups or individual users from playing  
- Auto-detects [Currency Core by StreamUP](https://streamup.tips/product/currency-core) and [LOYALTY POINTS by tawmae](https://tawmae.xyz/loyalty-points),  
  with a manual fallback for your own custom points system  
- Every chat message (win, loss, jackpot, cooldown, errors, free game) is editable via the settings GUI  
- Persistent log file with every gamble result, filterable and searchable in the built-in log viewer  
- A built-in WPF settings window with dark/light mode, live game preview, and tab-based navigation  

---

## 🎮 How It Works

Viewers trigger the game by using the configured chat command (e.g. `!gamble`) or by redeeming a Channel Point reward. The game rolls against configurable probability thresholds:

| Outcome | Trigger | Payout |
|---------|---------|--------|
| 🎰 **Jackpot** | Roll ≤ Jackpot % | `bet × random(RndMin–RndMax) × JackpotMultiplier` |
| 🎉 **Win** | Roll ≤ Win % | `bet × random(RndMin–RndMax)` |
| ❌ **Loss** | Remaining % | `-bet` |

---

## 🎫 Channel Points Mode (Twitch only)

When `Only Channel Points` is enabled, the chat command is effectively disabled — only viewers who redeem the configured Channel Point reward can play. Four bet modes are available:

- **Cost** — The reward's point cost is the bet
- **Input** — The viewer types their bet into the reward's text field
- **Fixed** — Every redemption bets a fixed configured amount
- **Free** — All redemptions play for free regardless of cost

---

## Get Started

[Setup Guide](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Setup-Guide.md)

[Frequently Asked Questions](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/FAQ.md)

[Import String for streamer.bot](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Import-String.md)

[Download](https://github.com/aaskjer/Classic-Chat-Gamble/releases)

---

## Credits & Links


[aaskjer on Twitch](https://twitch.tv/aaskjer)

[Better Stream Announcements on SB Discord](https://discord.com/channels/834650675224248362/1446874050310836396/1446874050310836396)

[Streamer.bot](https://streamer.bot) / [nate1280](https://www.patreon.com/c/nate1280/home)

YOU ♡
