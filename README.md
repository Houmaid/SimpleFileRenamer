# Simple File Renamer 1.0.0

<img width="1933" height="1477" alt="Screenshoot" src="https://github.com/user-attachments/assets/5ee780ab-80c2-4e89-9517-e2df7838fc29" />

Simple File Renamer renames many files at once – with a live preview, presets and undo.
The app is **portable**: there is no setup, it runs straight from its folder and needs **no administrator rights**.

**Contents:** [Requirements](#1-requirements) · [Installation](#2-installation) · [Update](#3-update) ·
[Uninstall](#4-uninstall) · [Data](#5-where-the-app-stores-its-data) · [Troubleshooting](#6-troubleshooting) ·
[Help & Instructions](#7-help--instructions)

---

## 1. Requirements

- Windows 10 (version 1809 or later) or Windows 11, 64-bit.
- **No .NET installation is required:** the .NET 10 runtime is included in the subfolder `net`.
  Always keep the `net` folder next to `SimpleFileRenamer.exe`.

## 2. Installation

1. **Before extracting** the ZIP file: right-click it → **Properties** → tick **Unblock** at the bottom → **OK**.
   Otherwise Windows asks every time you start the app.
2. Extract the ZIP file into a permanent folder, e.g. `C:\Users\<Name>\Programs` (preferably not your Downloads
   folder). This creates the folder `SimpleFileRenamer`.
3. Double-click **SimpleFileRenamer.exe**.
4. Optional: right-click `SimpleFileRenamer.exe` → **Send to** → **Desktop (create shortcut)**.

*"Windows protected your PC"*: the app is not digitally signed. Click **More info** → **Run anyway**.

## 3. Update

At every start the app checks GitHub for a new version and offers to open the download page.

1. Close the app (also in the system tray next to the clock: right-click → **Exit**).
2. Unblock and extract the new ZIP file as described above.
3. Replace the old `SimpleFileRenamer` folder with the new one.

Settings, your own presets and the undo history are kept.

## 4. Uninstall

1. First turn off in the app: ⚙️ → **Explorer context menu and "Send to"** (untick), and ⚡ → **autostart with Windows**.
2. Close the app and delete the `SimpleFileRenamer` folder.
3. Optionally delete the saved data as well (press `Win + R` and enter the folder name):
   - `%APPDATA%\SimpleFileRenamer` – presets, undo history, log
   - `%LOCALAPPDATA%\SimpleFileRenamer` – settings (language, color scheme, window size)

## 5. Where the app stores its data

| Folder | Content |
|---|---|
| `%APPDATA%\SimpleFileRenamer` | `presets.json` (your presets), `undo.json` (undo history and the rename currently running), `history.csv` (log of all renames), `error.log` (error log) |
| `%LOCALAPPDATA%\SimpleFileRenamer` | `user.config` (settings) |

⚙️ → **Open log folder** opens the first folder. A file that cannot be read is set aside as
`….corrupt-<date-time>` instead of being overwritten.

The app only connects to the internet for the update check (`api.github.com`). No file names or other data are sent.

## 6. Troubleshooting

| Problem | Solution |
|---|---|
| The app does not start or reports missing files | Make sure the `net` folder is complete and lies next to `SimpleFileRenamer.exe`. If in doubt, extract the ZIP file again. |
| The app does not open a second time | Only one instance runs at a time – look in the system tray next to the clock. |
| Context menu entry is missing or does nothing | ⚙️ → turn the context menu off and on again (e.g. after moving the app folder). |
| The app crashed while renaming | Restart it. It detects the changes already made and shows a notice; **Undo** reverts them. |
| A file is suddenly named `….sfr-` plus 8 characters | A temporary name used when swapping two names. It is only left behind if the app crashed at exactly that moment; simply rename the file back. |
| Presets or undo history are empty | Look for `presets.json.corrupt-…` or `undo.json.corrupt-…` in the log folder. |
| Other errors | ⚙️ → **Open log folder** → attach `error.log` when reporting a problem. |

---

## 7. Help & Instructions

The same instructions are in the app under ❓ (or **F1**).

### 7.1 Getting started

1. Drag files or folders onto the area at the top. Alternatively, click the area or use “Choose folder…”.
2. Click a quick preset or enter your own rules.
3. Check the preview: changed parts are highlighted, problems are marked in red. Nothing happens to your files until you click “Apply Filenames”.
4. Click “Apply Filenames” (Ctrl+Enter).
5. Something wrong? “Undo” (Ctrl+Z) reverts the last step, even after restarting the app.

### 7.2 Loading files

- Drag: drag files and folders from Explorer onto the area at the top. New files are added to the list; duplicates are ignored.
- Select: clicking the area (Ctrl+O) opens the file picker, “Choose folder…” (Ctrl+Shift+O) the folder picker.
- From Explorer: right-click → “Rename with Simple File Renamer” or “Send to”. Both are switched on in the gear menu. If the app is already running, the files go to the open window.
- “Include subfolders”: include files from all subfolders.
- “Skip hidden and system files”: applies to folder contents. Files you select individually are always included.
- “Rename folders themselves (not their content)”: dropped folders themselves are added to the list, not their files.
- “Only extensions”: e.g. jpg;png – separated by semicolon, comma or space. Empty means all files.
- The list is sorted like in Explorer (“File 2” before “File 10”), so {Nr} counts in the expected order.
- Loading large folders can be cancelled with Esc. “Clear” removes all entries from the list; the files themselves stay unchanged.

### 7.3 Quick presets and your own presets

- 🔍 Automatic Suggestion (Smart): detects TV episodes (e.g. “show.s01e02.1080p”) and suggests “Show - S01E02”. Otherwise the files are numbered.
- ✨ Clean Up Automatically: dots and underscores become spaces, double spaces are removed.
- 📺 Clean TV Show Episodes: “Show.Name.S01E02.German.1080p” becomes “Show Name - S01E02”.
- 🔢 Number Sequentially: new name from the template “File_{Nr}_{YYYY}”.
- My presets: “💾 Save” stores all current rules under a name. Picking a preset from the list loads it again, “Delete” removes it.
- A preset replaces the current rules. You can adjust everything afterwards.

### 7.4 Simple Mode

- “Search / Pattern” holds the terms, “New Name / Replace” the replacements. They are matched in order and separated by spaces. Example: german web → German empty
- Put terms containing spaces in quotes: "web dl".
- “empty” or "" as replacement deletes the term. If a replacement is missing, the term is deleted as well.
- All terms are replaced at once. Longer terms take priority, so “web-dl” before “web”.
- Upper and lower case are ignored unless “Match case” is checked.
- Without a search term, the replacement field is the template for the whole name: Vacation_{Nr} gives Vacation_01, Vacation_02 …
- The extension is always kept. You can change it under “More rules”.

### 7.5 Expert Mode (Regex)

- The search pattern is a regular expression (.NET) and applies to the name without extension.
- In the new name, `$1`, `$2` … insert the groups, `${name}` named groups and `$0` the whole match.
- Example: pattern `^(.*?)_S(\d+)E(\d+)`, new name `$1 - S$2E$3`
- Groups and variables can be combined: `$1_{Nr}`
- Errors in the pattern are shown below the input fields, and the files then show “Pattern error”. Patterns that take too long are stopped after a short time.

### 7.6 Variables

| Variable | Meaning |
|---|---|
| `{Nr}` | running number (settings under “Counter {Nr}”) |
| `{YYYY}` | current year |
| `{Date}` | today's date (YYYY-MM-DD) |
| `{Modified}` | date the file was last modified |
| `{Taken}` | date taken from the EXIF data of photos (JPG, PNG, TIFF, HEIC, RAW …), otherwise the modified date |
| `{Folder}` | name of the folder containing the file |
| `{Name}` | original name without extension |

- The buttons under “Insert Variables” insert the variable at the cursor position in the last field you used.
- Variables work in the new name, in replacements and in prefix and suffix. Case does not matter: {nr} = {Nr}.
- If “{Date}” or similar already appears in the original file name, it is left as it is.

### 7.7 More rules

- Prefix / Suffix: text before or after the name (before the extension).
- Remove characters from position / Count: position 1 and count 4, for example, remove the first four characters.
- New extension: e.g. jpg without a dot. Empty means keep the extension. Folders have no extension.
- Case: Unchanged, lowercase, UPPERCASE or Title Case. Applies to the name only, not the extension.
- Clean up: dots and underscores become spaces. Double spaces and spaces at the edges are removed.
- Counter {Nr}: Start, Step and Digits (0 = auto). With 0 the number has at least two digits, more if there are many files (001 … 150). Only included files are counted, in list order.
- Order: search/replace → remove characters → clean → prefix/suffix → variables → case → extension.

### 7.8 Preview and status

- Each row shows the old and the new name; the changed part is highlighted. The preview updates as you type.
- Untick the box at the front to skip a file. If several rows are selected, the click applies to all of them.
- Double-click the new name to edit it by hand (Enter confirms, Esc discards). Clearing the field makes the rules apply again.
- Right-click: Include · Exclude · Reset manual name · Show in Explorer · Remove from list (Del)
- Status:
  - Ready – will be renamed
  - Unchanged / Excluded – will be skipped
  - Invalid characters – `\ / : * ? " < > |` or a dot or space at the end
  - Reserved name – CON, PRN, AUX, NUL, COM1 …, LPT1 …
  - Path too long (MAX_PATH) – more than 260 characters
  - Internal collision – several files would get the same name
  - Target exists – another file already has this name
- Only rows with “Ready” are renamed.

### 7.9 Renaming

- “Apply Filenames” (Ctrl+Enter) renames all rows with “Ready”. From 10 files on, you are asked to confirm first.
- Progress and remaining time are shown at the bottom. “Cancel” or Esc stops after the current file; whatever was done until then can be undone.
- Chains and swaps work: a→b and b→c run in a safe order, a↔b via a short temporary name.
- Read-only files are renamed too. Files that are currently open in another program stay unchanged and get an error status.
- Afterwards each row shows its result, e.g. “Renamed” or the reason for the error.

### 7.10 Target folder

- Tick “Save to target folder” and choose a folder. All files in the list then end up in this one folder with their new names, even if they come from different folders.
- “Move” takes the files out of their folders, “Copy” leaves the originals in place.
- Identical names from different folders count as a collision. {Nr} or {Folder} in the new name make them unique.
- Folders themselves cannot be put into a target folder.
- “Delete source folders afterwards” (only when moving): after a confirmation, the source folders and their remaining contents go to the Recycle Bin. Drives, Windows and user folders (Desktop, Downloads, Documents …), folders containing the target folder and folders with files that were not moved are never touched.
- “Undo” moves the files back and restores deleted source folders from the Recycle Bin. Copies are only deleted if they have not been changed since.

### 7.11 Undo, redo and log

- “Undo” (Ctrl+Z) reverts the last step, “Redo” (Ctrl+Y) repeats it. Up to 50 steps are kept, even across restarts.
- If a file cannot be renamed back, it stays in the history and can be retried later.
- If the app stops in the middle of renaming (crash, power failure), the next start detects the changes already made. They can then be undone.
- “Clear” only empties the list, not the history.
- “📄 Export log” saves all renames so far as a CSV file, e.g. for Excel. Gear → “Open log folder” shows the log, the error log and your presets.

### 7.12 Settings and Windows

- ⚙️ Gear: Explorer context menu and "Send to" · “Minimize to system tray” · “Open log folder”
- ⚡ Lightning bolt: start with Windows. The app then starts hidden in the notification area next to the clock.
- 🌐 Globe: language (15 languages). 🎨 Palette: color scheme; “System (automatic)” follows the light or dark mode of Windows.
- Notification area: double-click opens the window, right-click → Open / Exit.
- Updates: at every start the app checks GitHub for a new version. If there is one, it asks whether to open the download page in your browser. Without an internet connection nothing happens.
- Only one instance runs at a time. Starting it again, e.g. from Explorer, hands the files over to the open window.
- Language, color scheme, window size and loading options are saved.
- If you move the app folder, switch the context menu and autostart off and on again once.

### 7.13 Keyboard shortcuts

| Shortcut | Action |
|---|---|
| **Ctrl+O** | add files |
| **Ctrl+Shift+O** | add folder |
| **Ctrl+Enter** | “Apply Filenames” |
| **Ctrl+Z / Ctrl+Y** | Undo / Redo |
| **Esc** | cancel loading or renaming |
| **Del** | remove selected rows from the list |
| **Double-click** | edit the new name by hand |
| **F1** | this help |
