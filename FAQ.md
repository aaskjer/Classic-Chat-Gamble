# Setup & Configuration
### How do I install Classic Chat Gamble?
Import the [string](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Import-String.md) or the [Classic-Chat-Gamble.sb](https://github.com/aaskjer/Classic-Chat-Gamble/releases) file in streamer.bot. Checkout the [Setup Guide](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Setup-Guide.md) for more details.
### Which version of Streamer.bot is required?
The latest public version is always recommended.
### Where are the config files located?
Always in your streamer.bot root folder: > `Chat Games\Classic Chat Gamble`
### How do I reset all settings to default?
Delete the `configs.json` or simply press the `Reset` button in the GUI.

# Points & Currency
### Which loyalty point systems are supported?
Any custom points system is supported. [CurrencyCore by StreamUP](https://streamup.tips/product/currency-core) and [LOYALITY POINTS by tawmae](https://tawmae.xyz/loyalty-points) are supported directly and will overrule any settings in configs.json
### How do I connect my existing points system?
Enter the GUI and replace the default `Points` value of `Points Var` in the `Game` tab if necessary.
### Why are users not losing or gaining points?
You may activated accidentally the `Free Mode` via commands, which causes the game to not rely on points to play anymore,
set `Default Bet` to 0 (which also leads to `Free Mode`) or your `Points Var` is invalid or missing.
### Can different platforms use separate point balances?
No, your configuration is globally for all platforms.

# Gameplay
### How do I change the gamble command?
Like any other command in streamer.bot in the commands tab.
### What bet inputs are supported?
Numbers, Percentage, Shorthand, Random, Half, Quarter, All.
### What does "DefaultBet = 0" do?
It enables the `Free Mode` which means that CCG does not use any currency anymore to play.
### Why does a user with 0 points get an error instead of being ignored silently?
This may be caused by an internal issue, please report it.
### Can users bet more than they have?
No. Users are bound by their total currency score and by the specifications set by Min Bet and Max Bet.
### How does the calculation work?

| Outcome | Trigger | Payout |
|---------|---------|--------|
| 🎰 **Jackpot** | Roll ≤ Jackpot % | `bet × random(RndMin–RndMax) × JackpotMultiplier` |
| 🎉 **Win** | Roll ≤ Win % | `bet × random(RndMin–RndMax)` |
| ❌ **Loss** | Remaining % | `-bet` |

# Channel Points
### Can other platforms still play when Channel Points mode is enabled?
Yes, Channel Points won't block other platforms from running anymore starting with `v22.0.0`
### What are the different CP Bet Modes and when should I use them?
`Cost`: Bet = Channel point reward cost. No user input needed — what the reward costs is what gets wagered.  
`Input`: Users type their bet into the reward text field (rawInput). Must be a positive integer — empty or negative input is rejected.  
`Fixed`: Every redemption bets the exact fixed bet you enter in the GUI. Must be > 0. Reward cost and viewer input are ignored.  
`Free Mode`: Bet is forced to 0. Users play for free — no points spent. Useful for events with a lot of new viewers.  
### How do I find my Reward ID?
Check out [Find Reward ID](https://ayrtonalexis.com/reward_checker/reward_check.html) to find your custom reward ID.

# Free Game Mode
### How do I start and stop Free Game Mode?
`!SetFreeGamble` to enable Free Mode and `!EndFreeGamble` to disable the Free Mode.
### Do users still earn points during Free Game Mode?
No Points will be deducted or awarded during Free Mode.
### Why aren't users being notified about Free Game Mode?
The notification is once per user on their first run.

# Cooldowns
### What is the difference between global and user cooldown?
Global cooldown blocks all users from playing, user cooldown is individual per user.
### Why is the cooldown message not appearing?
Message is empty, `messages.json` is corrupt/missing or currently there is no cooldown running.

# Multi-Platform
### Which platforms are supported?
Twitch, YouTube, Kick, Trovo
### Can I run the game on multiple platforms simultaneously?
Yes.
### Do cooldowns apply across platforms?
No, each platform runs their own cooldown handled by streamer.bot

# Custom Triggers & Integration
### What arguments are available after each gamble?
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
Add a new action and set a custom trigger of CCG

# Logs & Debugging
### Where is the action log saved?
Always in your streamer.bot root folder > `\Chat Games\Logs\CCG-log.txt`
### Why is nothing being logged?
Check if your ticked `Write Log` in the GUI. If the log is still missing, please report it.
### How do I report a bug?
Feel free to open up an issue [here](https://github.com/aaskjer/Classic-Chat-Gamble/issues).

# Messages
### How do I customize the win/loss/jackpot messages?
Directly in the GUI or in the `messages.json`
### What placeholders are available in messages?
Check the tooltips of the message in question.
### Can I use emojis in messages?
Yes.
