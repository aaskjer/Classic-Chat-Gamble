# Changelog

Releases are in the [release notes](https://github.com/aaskjer/Classic-Chat-Gamble/releases).

## v25.2.0 - 2026-11-08

### Added

- **Tells you about updates.** Once per Streamer.bot start, about 20 seconds in, one notice names new releases of
  this game, of the other UIFramework games and of UIFramework: in every chat whose broadcaster account is
  connected (Twitch, YouTube, Kick), or as a Windows notification while none is. The links are in Streamer.bot's
  log. *Tell me about updates* on the About page turns it off for this game. The game action is precompiled on
  application start, so the notice starts with Streamer.bot.
- The host block is UIFramework 1.4.0's; the settings window offers the newest UIFramework on its next open.

## v25.1.0

### Added

- **A tour of the settings window.** The first time the window opens, a short tour rings one part after the other
  (the pages, saving, the customise mode) and says what it does; the **?** at the top right shows it again.
- **UIFramework 1.0.0.** Problems the window finds sit behind a red **i** in its header instead of on the About or
  Log page, and *How to play*, *Log* and *About* sit together at the foot of the page list. The settings action
  offers the new framework on its next open.

### Changed
- **The chat messages are in `configs.json`.** Every setting now sits in one file, as in the other games. An old
  `messages.json` moves in on the first run of the game or of the settings window: each message goes into
  `configs.json` under its new name (one set to null becomes an empty message, which still sends nothing), and the
  file stays beside it as `messages.json.migrated`.
- When the window opens on the numbers of another fairness stop, the slider moves there without a *filled in*
  note in the footer; the note is for a stop you pick.
- **Fixed bet only in Fixed mode.** *Fixed bet* under Channel points shows while the bet mode is *Fixed*;
  before, it stood there greyed out in the other modes.
- **The settings action is UIFramework's generic stub.** `[CCG] - Settings` carries no layout and no game code any
  more: the game action declares its window (pages, pills, the log, help and about, the `!gamble` cooldowns)
  beside its settings table and answers the window itself (the fairness stops, the odds, a test roll, the check
  before saving). Needs UIFramework 0.9.2 or newer; the stub fetches it.
- **German.** With the window's language set to `de` (the pencil, then *Sprache*), every setting, section, page
  and message of the window reads in German. The help and about pages stay English.
- **The settings action is UIFramework's stub 0.2.0.** When the game action hangs, the settings window waits 30
  seconds for its answer, then carries on and can be closed; before, it waited for good. A game that has not
  described itself for a minute no longer locks the settings until Streamer.bot restarts: the next run opens the
  window.
- The host block is UIFramework's current one (1.0.0). It names every type in full, so it no longer depends on the
  action's `using` lines, and it can declare a tour of the window. Nothing changes in the window.
- A chance, multiplier or percentage written as NaN or infinity into `configs.json` still falls back the way it did;
  the new host block alone would read it as 0.

## v25.0.0

The settings window moved into [UIFramework for streamer.bot](https://github.com/aaskjer/UIFramework-Streamer.bot),
one window shared by all of these chat games. Gambles play exactly as before; what changed is how the settings are
shown and stored.

### Changed
- **`[CCG] - Settings` is a small stub now.** The first time you open it, it asks whether to download
  `UIFramework.dll` from GitHub (about 200 KB, checked against its published SHA-256) or to show the folder it
  belongs in, `UIFramework\lib\<version>\` next to Streamer.bot. Nothing is fetched without that click. When a
  newer UIFramework is published, opening the window offers it once: *Yes* downloads, *No* asks again next time
  and shows a pill in the header, *Cancel* skips that version.
- **The window is built from the game's own settings table.** The game declares every setting once and answers
  the window's request with it, so the window and the game can never disagree about a key, a default or a range
  again.
- **The Fairness slider is back.** Its stops, Strict, House Edge, Fair, Generous and Classic, fill in the five
  numbers; type your own and it moves to Custom, or to the stop they match. The bar under it shows the chance of a
  jackpot, a win and a loss and what a bet of 100 comes back as, from the numbers as they stand, saved or not. The
  slider's memory of your custom numbers while you tried stops is gone: a stop simply replaces them, and Cancel
  brings them back.
- **Try a bet** plays a round with the settings as they stand on the page and shows the roll and the exact chat
  message, as before.
- **A save that would not do what it looks like asks first**: Minimum above Maximum, a Default bet or Fixed bet
  outside them, Jackpot and Win chance adding up to more than 100, Min × above Max ×, no points variable while Free
  Game Mode is off, channel points without a Reward ID or with a Fixed bet of 0.
- **Customise mode.** The pencil at the bottom left lets you rename, reorder, hide and move pages and fields by
  drag and drop or from the context menu, and pick the accent colour. It lives in `uiframework.layout.json` next
  to `configs.json` and survives every import of the game.
- `configs.json` keys are camelCase now (`freeGame`, `minBet`, `jackpotPercent`, `addictedPayoutCut`). An existing
  file keeps working: the old names are read through aliases, and the first save writes the new ones.
  `messages.json` is unchanged: the window edits the messages in that file, under the names they always had.
- `!SetFreeGamble`, `!EndFreeGamble` and `!gambleaddict` write only what they change into `configs.json`, under
  the new names, and leave everything else in the file as it is.
- The cooldown messages use `{seconds}` and `{user}` instead of `{0}` and `{1}`; a text that still has the
  numbers keeps working.
- Light/dark lives in `uiframework.layout.json` and is shared with every other window built on UIFramework. An
  existing `DarkMode` is taken over on the first open.
- Values typed out of range are pulled back into range when the game reads them, not only when the window saves.
- The footer counts the unsaved changes; Reset page resets only the page in front; closing the window with
  unsaved changes asks first; a recompile or shutdown in Streamer.bot closes it without asking.

### Removed
- The window's own WPF code and update check (about 3,500 lines) left the import; the DLL carries them now. The
  rainbow mode and the Egg are the framework's now.

## v24.1.1

### Changed
- **The bottom bar counts the unsaved changes** — "No unsaved changes", "1 unsaved change", "3 unsaved changes" — instead of only saying that there are some. A value typed back to what it was no longer counts, and Save starts the count over.
- **Nothing is dropped without asking.** Cancel and the title bar's X ask "Discard N unsaved change(s)?" when there is something to lose; before, only the theme button asked, and the X never did. Save & Exit, Reset and the theme button still close straight away.
- **Reset page**, the new button next to Reset all: it puts only the page in front back to its defaults, in the window, and writes nothing until you save. The other pages keep what they hold.
- A save that fails says so in a box, "Could not save: …", on top of "Not saved" in the bottom bar and the log line.
- Save straightens out what the game takes for granted anyway: negative cooldowns and bets become 0, Jackpot % and Win % stay between 0 and 100, a Jackpot multiplier below 1 becomes 1, and Min × and Max × swap places when they are the wrong way round. Before saving, it asks about settings that cannot do what they look like — Minimum above Maximum, Jackpot % and Win % adding up to more than 100, no points variable while Free Game Mode is off.
- Recompiling or unloading the action while the settings window is open closes the window, instead of leaving one that writes `configs.json` from a build nothing else uses.

### Fixed
- **Damaged settings files are rescued instead of reset.** A `configs.json` or `messages.json` that does not parse now falls back to the `.bak` copy beside it before the defaults, and the window says which file it read back from where. Until now a damaged file simply meant the defaults for everything it held, and the next save wrote them over it.
- **Every save leaves a `.bak` behind** — the file as it was before that save, which is what the window reads back when the live one turns out to be damaged. A file that does not parse itself never becomes the backup, so a broken one cannot overwrite the last readable copy.
- Free Game Mode and the bet it returns to afterwards are carried over from a `configs.json` rescued from its `.bak`; only one that cannot be recovered at all is left alone. Before, any damaged `configs.json` dropped them.
- **Only one settings window opens.** A second trigger while it was up opened another one with its own copy of the settings, and whichever was saved last won. It now brings the open window to the front.
- Switching pages refreshes only the page in front, instead of every control in the window.

## v24.1.0

### Changed
- **No more platform switches.** As in Slot Machine Game, Twitch, YouTube and Kick play wherever the `!gamble` command listens. To leave a platform out, untick it on the command in Streamer.bot (for example "Kick Message"). When updating, keep in mind that YouTube and Kick used to be off by default and now play wherever the command listens to them; untick them on the command if you don't want that.
- **Replies go to the chat they came from.** The trigger's event decides where the game answers: the chat the command was typed in, or Twitch for a redemption. `!SetFreeGamble` and `!EndFreeGamble` answer in their own chat, and so do StartFreeGame and EndFreeGame when a channel point redemption runs them (in that redemption's chat, Twitch or Kick). Turned on or off any other way, for example by an Execute C# Method on StartFreeGame or EndFreeGame in an action of your own, Free Game Mode is announced on every platform with an account in Streamer.bot, and on YouTube only while a broadcast is monitored.
- **Channel points turn `!gamble` off on Twitch only.** Redemptions only come from Twitch, so YouTube and Kick viewers keep playing with `!gamble`. Redemptions keep their own cooldown clock: they don't hold up `!gamble` on YouTube or Kick, and `!gamble` doesn't hold them up.
- **Free Game Mode covers channel point redemptions too.** Nothing is won or lost and the Free Game messages are used, whatever is bet. In Typed amount mode, viewers used to lose real points while chat said it was free.
- **Moderators only:** `!SetFreeGamble`, `!EndFreeGamble` and `!gambleaddict` are limited to the `Moderators` group, and the broadcaster can always use them. Before, any viewer could start Free Game Mode or put someone on the addicted list.
- **The import works wherever Streamer.bot is installed.** Every Windows reference is absolute, so `Find Refs` is no longer needed.
- The update check runs in the background, so the settings window opens straight away and the Update pill appears once GitHub answers. Only a release newer than yours counts; an older tag, or one that isn't a version number, is ignored.
- After Save, the window points out settings that keep gambles from starting: channel points without a Reward ID, a Fixed bet of 0 or outside Minimum/Maximum, or a Default bet of 0 or outside them. "Saved" in the bottom bar turns amber with the reason, and a new problem pops up once.
- The theme button asks about unsaved changes first: Yes saves them, No drops them, Cancel stays. Unsaved changes show up in orange in the bottom bar.
- A few built-in chat texts read more naturally, and the usage text of the addicted list names the real command, `!gambleaddict`. Messages you already saved stay as they are.

### Fixed
- **Log page**: the Platform filter is back, next to Result and Date.
- The "CCG: Gamble Win", "Gamble Loss" and "Gamble Jackpot" triggers fire after the points are saved and the `ccg_last…` globals are written, so GetLastGambleResult in a triggered action reads this gamble, not the one before.
- Odd numbers in the settings or in a balance (NaN, infinity, huge values) no longer crash a gamble. A redemption whose gamble fails before any points move is refunded; one that fails afterwards is fulfilled and starts its cooldown instead of staying in the queue.
- A message set to null in `messages.json` sends nothing instead of failing the gamble.
- With channel points on and no Reward ID, the log reports an error instead of skipping every redemption with only a debug line.
- A Twitch `!gamble` that does nothing while channel points are on no longer starts the `!gamble` cooldown for YouTube and Kick.
- A Command Cooldown trigger never starts a gamble. For `!SetFreeGamble`, `!EndFreeGamble` and `!gambleaddict` it only sends the cooldown message instead of running the command.
- Only Twitch's Reward Redemption trigger starts a channel point gamble. A command is never taken for a redemption, even when it carries a reward ID, and a Kick redemption or a Twitch redemption update is no longer played as a Twitch redemption.
- **Damaged settings files**: the settings window names the damaged file. Only that file falls back to its defaults and is kept as a `.broken` copy; the other one is read as usual, and the theme button doesn't write over it.
- **Settings window**
  - A number field that is empty, or a whole number with a space in it like "1 000", is named in a message and nothing is saved. Both used to become 0 silently.
  - Ctrl+S and Save add a name still being typed into a list before saving, and one click on a name chip's × removes it even while another name is being typed. The × can also be reached with Tab and Space.
  - Try a bet: alice has ten times the Default bet (at least 10,000), so a Default bet above 10,000 is no longer always refused as not enough.
  - While Free Game Mode is on, Default bet shows the bet that applies again when it ends, not 0, and a change to it is kept as that bet.
  - The theme button and Reset say "Not switched" or "Not reset" when the settings can't be written, instead of closing the window.

## 2026-09-11

### Added
- **Free Game Loss message**: a loss in Free Game Mode gets its own message ("Loss" under Free Game messages). Before, it borrowed the normal loss message with the amount and balance left blank.
- **Fairness slider** on the Game page: one control instead of five numbers, like the sensitivity sliders in TwitchSentry. Each step (Strict, House Edge, Fair, Generous, Classic) sets Jackpot and Win chance, the Jackpot multiplier and the win multiplier range at once, and the window shows what a bet of 100 returns on average (Strict 75 … Classic 177). Classic matches the shipped odds, so updating changes nothing. Type your own numbers and the slider moves to Custom, which keeps them, so moving to a step and back loses nothing.

### Changed
- **A new, compact settings window.** The five tabs, plus the three hidden under "Other Modules", became one rail of pages: Game, Access, Messages, Log and About. A strip at the top shows whether Free Game Mode is on (it follows the chat commands while the window is open) and whether viewers play in chat or with channel points. Switches, segmented choices and name chips replace the old checkboxes, drop-downs and comma lists, and the whole window follows the dark or light theme, drop-downs included.
  - **Game**: the Fairness slider comes first, with a bar for the chance of a jackpot, a win and a loss. Default, Minimum and Maximum bet share a row; Subscriber boost, VIP boost and the Addicted cut share a card.
  - **Try a bet** replaces the Live Preview table. Pick a bet and who plays (viewer, subscriber, VIP or addicted) to see what a win, a jackpot and a loss pay, then press Roll for one round with your odds and the exact chat message it sends. Nothing is saved, and nobody's points change.
  - **Access**: platforms, `!gamble` in chat or channel points (with the Reward ID, what is bet and refunds), both cooldowns, and the blocked and addicted viewers and groups as name chips. Type a name and press Enter, or click the × on a chip.
  - **Messages**: the 25 message boxes became one editor. Pick a message from the grouped list, click a placeholder to insert it, and the chat preview shows it the way chat will read it, sender and /me included. "Use Bot Account" and "Send As Action" for game and cooldown messages live here now, and the Number Separator is picked from examples like 12.345 or 12,345.
  - **Log**: the Action-Log with search, Result and Date filters and colored results; "Write Log" is a switch right below it.
  - Ctrl+S saves and Ctrl+1 to Ctrl+5 open the pages; the bottom bar says when there are unsaved changes.
- **Typed amount bets the viewer's own points**, as `!gamble` does. The amount is checked against their balance (not enough, and the redemption is refunded), and a loss takes it off. Reward cost and Fixed mode work as before: there, the channel points are the stake.
- **Channel points Free mode** uses the Free Game messages, including the one-time Free Mode notice, instead of "You got 0 Points".
- **No gambling on an empty balance.** With 0 points, `!gamble` (for example `!gamble all`) is refused as not enough points instead of playing for 0. Free Game Mode still lets everyone play.
- The "update available" dialog is gone. A new version shows up as a red Update pill in the top strip (click it for the releases page), and the window title mentions it too.

### Fixed
- **Channel point redemptions now start a gamble.** The Reward Redemption trigger carries no command ID, so every redemption stopped at "Missing commandId": nothing was gambled, refunded or fulfilled.
- **Free Game triggers**: "CCG: Free Game Start" and "CCG: Free Game End" each fire only for their own event. Before, starting or ending Free Game Mode fired both.
- Ending Free Game Mode restores a Default bet of 0 as 0 instead of replacing it with 1234.
- Oversized bets such as `!gamble 99999999999B` or `!gamble 1E300K` are refused as too much instead of silently crashing the gamble. `!gamble random` with a balance above 2,147,483,647 now plays (betting at most 2,147,483,646) instead of crashing. A shorthand bet above 2,147,483,647, such as `!gamble 3B`, is refused even with the points for it, instead of being played as 2,147,483,647.
- Fractional Jackpot/Win chances are exact: 0.57% used to behave like 0.56%.
- Cooldown messages containing `{user}` go out with the name filled in instead of failing silently.
- `!gambleaddict @` shows the usage instead of adding a blank name.
- **Cooldown refunds**: channel point redemptions respect Cooldown Global/User now. A redemption during the cooldown gets the cooldown message and is refunded. "Cooldown active" was listed as a refund reason before, but could never happen for a redemption.
- Refunds only go into the action log while "Write Log" is on.
- **Minimum/Maximum bet no longer apply to Reward cost mode**, as the setting's note always said. A reward priced above the Maximum (or below the Minimum) was refused and refunded on every single redemption. Typed amount and Fixed mode are still limited.
- **Damaged settings files**: settings are saved by writing a new file and swapping it in, so a crash or power cut mid-save can no longer leave an empty `configs.json` behind, which stopped every gamble. If a file is damaged anyway, the settings window still opens: it shows the defaults, says so, and keeps the damaged file as a `.broken` copy.
- The game's built-in "Added" and "Usage" texts for the addicted list match the settings window; the old "Added" text promised a fixed 50% cut.
- **Settings window**
  - Saving no longer switches off a Free Game started while the window was open, and the theme button no longer undoes what the chat commands changed in the meantime.
  - A `!gambleaddict` change made while the window is open survives Save: names added or removed in the window are merged with the list on disk.
  - Cooldowns apply as soon as you press Save, not only once the window closes.
  - Jackpot Multiplier only takes whole numbers; "43.5" used to be saved as 0.
  - A space works as the Number Separator; it used to be trimmed away on save.
  - Numbers are checked before saving. "30%" counts as 30, and a field that holds no number at all is named in a message and nothing is saved. Both used to become 0 silently, and a Win (Percent) of 0 means nobody wins. A number too big for a whole-number field is saved as the largest possible value instead of 0.
  - Very large numbers typed into the window no longer crash it.
  - The Log page can no longer keep the window from opening while a log file is being written.
- **Log page**: the Date filter and content-sized columns from 2026-08-02 were missing from the window and are back; the Result filter also offers Refund.

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
