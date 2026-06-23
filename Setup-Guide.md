# Import
<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/2c17f5a0-15f3-4396-a277-a66638017fb3"> </p> 

Click on `Import` in [streamer.bot](https://streamer.bot/) and drag the [ClassicChatGamble.sb](https://github.com/aaskjer/Classic-Chat-Gamble/releases) file into the window or copy paste the [import string](https://github.com/aaskjer/Classic-Chat-Gamble/blob/main/Import-String.md).

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/ade12d9e-f2a7-4f0c-ab56-2cfcfc7d39b7"></p> 

Click on `Import` and `Yes` on both following popup messages.

## Enable Commands

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/7839f6b3-0b32-4b3d-8f11-e03e5589b16c"></p> 

Enable all commands in the `Commands` tab of streamer.bot.

# Configure Game

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/ad03421b-d887-4e36-91bd-d56edefdb9cd"></p> 

Go to `Actions` tab, click on the action `[CCG] - Settings` and right-click on the `Test` trigger and run `Test Trigger` to open the CCG GUI.

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/01361561-1f87-4460-9535-a2ff24e712bd"></p> 

`General` tab inerhit all options for commands, platforms and general appearance in chat.

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/af0eb185-b3b5-43b8-ba55-f691c5099c12"></p> 

`Game` tab gives your a lot of possibilities to modify the game and features a live preview based on your settings, so you can nerf the game for addicts or adjust it for events.

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/e820c300-b598-48fe-bac3-26213a576747"></p> 

`Messages` gives you the chance to modify any message in the game.

`Other Modules` contains `Twitch Channel Points` and the `Action Log`

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/e27a72ec-44bd-49ab-9941-4eac90430336"></p> 

`Twitch Channel Points` is twitch only (off by default). If enabled, the normal `!gamble` chat command is disabled for twitch.
`Bet Mode` let you choose of different ways to use channel points to trigger the game. Check out the description in the GUI for each mode.
Note: while `Twitch Channel Points` is active, other platforms can still play.

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/b1f384b3-227d-41f4-881c-3d8919d41394"></p> 

`Action Log` shows you exactly the outcome of a gamble game per user. You can see easily who won, loss, hit the jackpot. Filter per platform and other details are possible.

## Math Calculation

| Outcome | Trigger | Payout |
|---------|---------|--------|
| 🎰 **Jackpot** | Roll ≤ Jackpot % | `bet × random(RndMin–RndMax) × JackpotMultiplier` |
| 🎉 **Win** | Roll ≤ Win % | `bet × random(RndMin–RndMax)` |
| ❌ **Loss** | Remaining % | `-bet` |

# Other Features

## Arguments
Arguments available outside of the game, handy if you want to trigger further actions on certain situations.
| Argument | Value |
|----------|-------|
| `gambleOutcome` | `WIN`, `LOSS`, or `JACKPOT` |
| `gambleAmount` | Points won or lost |
| `gambleBetAmount` | The original bet |
| `gamblePreviousPoints` | Balance before the gamble |
| `gambleNewPoints` | Balance after the gamble |
| `gambleCurrency` | Currency name |
| `gambleOutcomeMessage` | Pre-formatted result summary |

<p align="center"><img alt="grafik" src="https://github.com/user-attachments/assets/f0d90ae1-4c89-4ef1-a67e-b67142354678"></p> 

## Free Mode
You have various ways to enable the `Free Mode`. You can set `Default Bet` to `0` or use chat commands:

| Command | Info |
|----------|-------|
| `!SetFreeMode` | Enable the free mode and validate the action with a message.<br>Every user now will get a one time only message to inform about the mode being active | 
| `!EndFreeMode` | Restores the normal gamble mode and validates it with a message. |
