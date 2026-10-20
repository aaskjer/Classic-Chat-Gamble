# Setup & Configuration
### How do I install Classic Chat Gamble?
Import the [import string](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Import-String.md) or the [ClassicChatGamble.sb](https://github.com/aaskjer/Classic-Chat-Gamble/releases) file in Streamer.bot. The [Setup Guide](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Setup-Guide.md) walks you through it.
### Which version of Streamer.bot is required?
The latest public version is always recommended.
### Where are the config files?
In your Streamer.bot folder under `Chat Games\Classic Chat Gamble`: `configs.json` holds the settings, `messages.json` the chat messages.
### How do I reset all settings to default?
Click the reset button at the bottom left of the settings window and confirm, or delete `configs.json`.
### What if a settings file is damaged?
The settings window still opens and tells you which file it couldn't read. That file shows its defaults and is kept next to it as a `.broken` copy, and saving writes a fresh one.

# Points & Currency
### Which loyalty point systems are supported?
Any custom points system works. [Currency Core by StreamUP](https://streamup.tips/product/currency-core) and [LOYALTY POINTS by tawmae](https://tawmae.xyz/loyalty-points) are detected on their own, and their settings take priority over the ones in `configs.json`.
### How do I connect my existing points system?
On the Game page of the settings window, enter its variable under `Points variable`. The default is `points`.
### Why aren't viewers losing or gaining points?
Check these first:
- Free Game Mode is on. The strip at the top of the settings window then says `Free game on`, and `!EndFreeGamble` turns it off.
- Channel points are set to `Free`, or to `Reward cost` or `Fixed`, where a loss takes no points by design.
- The `Points variable` is wrong or missing.
### Do different platforms have separate point balances?
Yes. Each platform keeps its own balance per viewer, while the settings apply to every platform.

# Gameplay
### How do I change the gamble command?
Like any other command, in the `Commands` tab of Streamer.bot.
### What bet inputs are supported?
Numbers (`500`), percentages (`50%`), shorthand (`10k`, `2.5m`, `1b`) and the keywords `all`, `half`, `third`, `quarter` and `random`.
### What does a Default bet of 0 do?
Viewers then always have to name an amount, and a plain `!gamble` is refused. To let everyone play for free, use Free Game Mode instead.
### Why does a viewer with 0 points get an error?
That's on purpose: with an empty balance there's nothing to bet, so `!gamble` is refused as not enough points. Free Game Mode still lets everyone play.
### Can viewers bet more than they have?
No. A bet is limited by the viewer's balance and by the Minimum and Maximum bet.
### What does `!gambleaddict` do?
It puts a viewer on the addicted list (`!gambleaddict add <name>`) or takes them off (`!gambleaddict remove <name>`). Addicted viewers win less, by the Addicted cut on the Game page, and get messages of their own.
### How does the calculation work?

| Outcome | When | Payout |
|---------|------|--------|
| 🎰 **Jackpot** | Roll ≤ Jackpot % | `bet × random(Min×–Max×) × Jackpot×` |
| 🎉 **Win** | Roll ≤ Win %, on top of the jackpot chance | `bet × random(Min×–Max×)` |
| ❌ **Loss** | Everything else | `-bet` |

Wins and jackpots are paid on top of the bet.

# Channel Points
### Can other platforms still play while channel points are on?
Yes. Since `v22.0.0`, channel points only turn `!gamble` off on Twitch, and YouTube and Kick keep playing with it.
### What are the bet modes, and when should I use which?
`Reward cost`: the reward's price is the bet, so viewers don't type anything. A loss doesn't touch their points, and a win is paid in points.  
`Typed amount`: viewers type their bet into the reward's text field. Like `!gamble`, it's paid from their own points: checked against their balance and taken off on a loss. It has to be a whole number above 0.  
`Fixed`: every redemption bets the amount you set, which must be above 0. The reward's price and anything typed are ignored.  
`Free`: nothing is won or lost. Useful for events with a lot of new viewers.  
Minimum and Maximum bet apply to `Typed amount` and `Fixed`.
### Why was a redemption refunded?
It didn't end in a gamble: the viewer is blocked, a cooldown is running, or the bet didn't work, for example too few points for a typed amount. Refunds only work while the redemption waits in the queue, so the reward must not skip the reward requests queue. You can switch refunds off on the Access page.
### How do I find my Reward ID?
[Find Reward ID](https://ayrtonalexis.com/reward_checker/reward_check.html) lists your rewards with their IDs. The settings window links there too.

# Free Game Mode
### How do I start and stop Free Game Mode?
`!SetFreeGamble` starts it, `!EndFreeGamble` stops it.
### Do viewers still earn points during Free Game Mode?
No. Nobody wins or loses points while it's on, channel point redemptions included.
### Why aren't viewers being told about Free Game Mode?
The notice goes to each viewer only once, with their first gamble.

# Cooldowns
### What's the difference between the global and the user cooldown?
The global cooldown (`Everyone`) pauses the game for all viewers, the user cooldown (`Per viewer`) only for the viewer who just played.
### Why isn't the cooldown message showing up?
The message is empty, `messages.json` is damaged, or no cooldown is running.
### Do cooldowns apply across platforms?
No, Streamer.bot runs the command cooldown for each platform on its own. Channel point redemptions keep a separate clock with the same durations.

# Multi-Platform
### Which platforms are supported?
Twitch, YouTube and Kick.
### Can I run the game on several platforms at once?
Yes. Every platform the `!gamble` command listens to can play, and the game always answers in the chat the command came from. To leave a platform out, untick its source on the command, for example `Kick Message`.

# Custom Triggers & Integration
### What arguments are available after each gamble?
Run `GetLastGambleResult` with an `Execute C# Method` sub-action to get them:

| Argument | Value |
|----------|-------|
| `gambleOutcome` | `WIN`, `LOSS`, or `JACKPOT` |
| `gambleAmount` | Points won or lost |
| `gambleBetAmount` | The original bet |
| `gamblePreviousPoints` | Balance before the gamble |
| `gambleNewPoints` | Balance after the gamble |
| `gambleCurrency` | Currency name |
| `gambleOutcomeMessage` | Pre-formatted result summary |
### How do I use the custom triggers in other actions?
Add a new action and give it one of the CCG custom triggers: `CCG: Gamble Win`, `CCG: Gamble Loss`, `CCG: Gamble Jackpot`, `CCG: Free Game Start` or `CCG: Free Game End`.

# Logs & Debugging
### Where is the action log saved?
In your Streamer.bot folder under `Chat Games\Logs`, one file per day: `CCG-log-yyyy-MM-dd.txt`. The Log page of the settings window shows them all together.
### Why is nothing being logged?
Check that `Write a log file per day` is switched on, below the table on the Log page. If the log stays empty, please report it.
### How do I report a bug?
Open an issue [here](https://github.com/aaskjer/Classic-Chat-Gamble/issues).

# Messages
### How do I customize the win, loss and jackpot messages?
On the Messages page of the settings window, or directly in `messages.json`.
### Which placeholders can I use?
The Messages page lists them under each message; hover over one to see what it stands for, click it to insert it.
### Can I use emojis in messages?
Yes.
