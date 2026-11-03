## 2026-09-11

### Added
- **Free Game Loss message** — a loss in Free Game Mode now has its own message ("Loss" under Free Game Messages) instead of reusing the normal loss message with the amount and balance left blank.
- **Fairness slider** on the Game page — one control instead of five numbers, like the sensitivity sliders in TwitchSentry. Its steps (Strict, House Edge, Fair, Generous, Classic) drop a whole set of odds into Jackpot and Win chance, Jackpot Multiplier and the win multiplier range, and next to it the window says what a bet of 100 comes back as on average (Strict 75 … Classic 177). Classic is exactly what ships, so nothing moves on update. Typing your own numbers moves the slider to Custom, which keeps them, so moving off a step and back loses nothing.

### Changed
- **New, compact settings window** — the five tabs, and the three hidden under "Other Modules", are one rail of pages now: Game, Access, Messages, Log and About. A strip at the top shows whether Free Game Mode is on (it follows the chat commands while the window is open) and whether viewers play in chat or with channel points. Switches, segmented choices and name chips replace the old checkboxes, drop-downs and comma lists, and the whole window follows the dark or light theme, drop-downs included.
  - **Game**: the Fairness slider comes first, with a bar for the chance of a jackpot, a win and a loss. Default, Minimum and Maximum Bet share one row, and Subscriber boost, VIP boost and the Addicted cut share one card.
  - **Try a bet** replaces the Live Preview table: choose a bet and who plays (viewer, subscriber, VIP or addicted) to see what a win, a jackpot and a loss pay, and press Roll to play one round with your odds and see the exact chat message it sends. Nothing is saved and nobody's points are touched.
  - **Access**: platforms, `!gamble` in chat or channel points (with the Reward ID, what is bet and refunds), both cooldowns, and the blocked and addicted viewers and groups as name chips — type a name and press Enter, or click the × on a chip.
  - **Messages**: the 25 message boxes are one editor. Pick a message from the grouped list, click a placeholder to insert it, and a chat preview shows the message the way chat will read it, sender and /me included. "Use Bot Account" and "Send As Action" for game messages and for cooldown messages live here now, and the Number Separator is picked from examples such as 12.345 or 12,345.
  - **Log**: the Action-Log with search, Result and Date filters and colored results; "Write Log" is a switch right below it.
  - Ctrl+S saves and Ctrl+1 to Ctrl+5 open the pages; the bottom bar says when there are unsaved changes.
- **Channel Points Input mode bets the viewer's own points**, like `!gamble`: the typed amount is checked against their balance — not enough, and the redemption is refunded — and a loss takes it off their balance. Cost and Fixed mode are unchanged; there the channel points are the stake.
- **Channel Points Free mode** uses the Free Game messages, including the one-time Free Mode notice, instead of "You got 0 Points".
- **No gambling on an empty balance** — with 0 points, `!gamble` (for example `!gamble all`) is refused as not enough points instead of playing for 0. Free Game Mode still lets everyone play.
- No more "update available" dialog when the settings window opens: a new version shows as a red Update pill in the window's top strip (click it for the releases page), and the window title says so too.

### Fixed
- **Channel Points redemptions now start a gamble.** The Reward Redemption trigger carries no command ID, so every redemption stopped at "Missing commandId" — nothing was gambled, refunded or fulfilled.
- **Free Game triggers** — "CCG: Free Game Start" and "CCG: Free Game End" now each fire only for their own event; before, starting or ending Free Game Mode fired both.
- Ending Free Game Mode restores a Default Bet of 0 as 0, instead of replacing it with 1234.
- Oversized bets such as `!gamble 99999999999B` or `!gamble 1E300K`, and `!gamble random` with a balance above 2,147,483,647, are refused as too much instead of silently crashing the gamble. A shorthand bet above 2,147,483,647 (such as `!gamble 3B`) is refused even with the points for it, instead of being played as 2,147,483,647.
- Fractional Jackpot/Win chances are exact now — 0.57% used to behave like 0.56%.
- Cooldown messages that contain `{user}` are sent with the name filled in, instead of failing silently.
- `!addicted @` shows the usage instead of adding a blank name.
- **Cooldown refunds** — Channel Points redemptions now keep Cooldown Global/User: one redeemed while the cooldown runs gets the cooldown message and is refunded. "Cooldown active" was listed as a refund reason before, but could never happen for a redemption.
- Refunds are only written to the action log while "Write Log" is on.
- **Minimum/Maximum Bet no longer apply to Channel Points Cost mode**, as the setting's note always said — a reward priced above Maximum Bet (or below Minimum Bet) was refused and refunded on every single redemption. Input and Fixed mode are still limited.
- **Damaged settings files** — settings are now saved by writing a new file and swapping it in, so a crash or power cut mid-save can no longer leave an empty `configs.json` behind, which stopped every gamble. If a file is damaged anyway, the settings window still opens: it shows the defaults, says so, and keeps the damaged file as a `.broken` copy.
- The game's built-in "Added" and "Usage" texts for the addicted list match the settings window; the old "Added" text promised a fixed 50% cut.
- **Settings window**
  - Saving no longer switches off a Free Game that was started while the window was open, and the theme button no longer undoes changes chat commands made in the meantime.
  - An `!addicted` change made while the window is open survives Save: names added or removed in the window are merged with the list on disk.
  - Cooldowns apply as soon as you press Save, not only once the window is closed.
  - Jackpot Multiplier only accepts whole numbers — "43.5" used to be saved as 0.
  - A space works as the Number Separator; it used to be trimmed away on save.
  - Numbers are checked before saving: "30%" is read as 30, and a field that holds no number at all is named in a message and nothing is saved — both used to become 0 silently, and a Win (Percent) of 0 means nobody wins. A number too big for a whole-number field is saved as the largest possible value instead of 0.
  - Very large numbers typed into the window no longer crash it.
  - The Log page can no longer stop the window from opening while a log file is being written.
- **Log page** — the Date filter and content-sized columns from 2026-08-02 were missing from the window and are in place now; the Result filter also offers Refund.

## 2026-08-06

### Added
- **Channel Points refund logic** — redemptions that don't result in a gamble now automatically get refunded instead of silently taking the viewer's points.
  - Refunds trigger on: platform disabled, blocked user/group, cooldown active, or an invalid bet amount.
  - New "Refund Failed Redemptions" toggle on the Channel Points tab (on by default).
  - New "Redemption Refunded" chat message, sent to the viewer when a refund goes through.
  - Successful redemptions are now also marked fulfilled, so they don't pile up in the reward request queue.

### Changed
- **New Cooldown tab** — all cooldown-related settings and messages now live in their own dedicated tab instead of being split across General and Messages.
  - Moved: Use Bot Account, Send As Action, Cooldown Global (Seconds), Cooldown User (Seconds) — out of General.
  - Moved: Global Message, Per User Message — out of Messages.

## 2026-08-02

### Added
- **Daily log rotation** — the action log now writes to a new dated file each day (`Logs/CCG-log-yyyy-MM-dd.txt`) instead of one file that grows forever.
- **Date filter** — the Action-Log tab has a new "Date" dropdown so you can view a single day's entries at a glance, alongside the existing Result/Platform filters and search box.

### Changed
- The Action-Log tab now loads and merges **all** daily log files (plus any legacy `CCG-log.txt`), sorted newest first, so nothing is hidden behind the rotation.
- Action-Log table columns now auto-size to fit their content instead of being split evenly across the grid.
- Updated the "Write Log" setting's tooltip to reflect the new dated log file naming.
