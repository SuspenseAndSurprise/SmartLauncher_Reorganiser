# Smart Launcher reorganiser – AI prompt for tidying your drawer & home screen

A prompt for an AI that can open files and run Python. You give it your Smart Launcher backup (.slbk), answer a few questions, and it gives you a new backup with a tidier app drawer and home screen.

Unofficial. Built with AI assistance and tested on a real phone. Your original backup is never changed, so keep it as a fallback.

## What it does

- Sorts your apps into tabs, with names and icons you agree on
- Hides clutter you approve
- Moves home screen icons and creates home screen folders
- Arranges tabs, home screen icons and (if you want) the dock for your thumb, left or right handed
- Optionally orders the apps inside each drawer tab by how much you use them. This follows your "stack apps from the bottom" setting (on: bottom up, off: top down) and switches the drawer sort from "By used" to "By user" (a custom order). You can switch it back in Smart Launcher's settings
- Asks which language to chat in and which language the tab and folder names should be in

It doesn't touch widgets, custom icons or anything else in the backup. It checks the new file before handing it over.

## How to use it

1. In Smart Launcher's settings, make a backup and copy the .slbk file somewhere you can reach it.
2. Open an AI that can open files and run Python. Give it `SmartLauncher_Reorganiser_agent.md` as the instructions.
3. Attach your .slbk file and answer its questions.
4. Restore the new file in Smart Launcher (settings, backup/restore). If the lock-screen wallpaper resets, set it again.

## Which AI

It has to accept the backup (it's a zip: rename it to .zip if the upload is refused), extract it, run code and hand back a new file.

- Claude and Grok worked in testing.
- ChatGPT, Copilot and others may work, depending on their current limits. Not tested.
- Gemini: its app limits zips to 10 files and a backup has more, so it probably won't work.

## Privacy

The default backup from Smart Launcher has your app list, layout, launch counts, cached news headlines, your wallpaper, a screenshot of your home screen (check it for calendar items) and the launcher's settings. The settings include your phone model and a last known location (probably for the weather). In the backup I checked there were no emails, phone numbers, passwords or contact names.

Worth a look before you upload it to a cloud AI. To remove the location: rename the backup to .zip, delete the whole `last_position` line in `shared_prefs/ginlemon.flowerfree.xml` and rename it back. Restoring a backup edited like this works, but the launcher writes the location again by itself, so repeat it for each new backup. The wallpaper and screenshot stay inside, so check those yourself. Don't post your backup publicly.

## Free or Pro

Smart Launcher's docs list editable tabs as a Pro feature. This was tested on Pro: restoring a backup with new, renamed and reordered tabs (with icons), moved apps, a home screen folder and moved home icons all worked. I don't know what the free version does with custom tabs. If you're on free, check the first result on your phone before going further.

## Tested

Tested on a real backup with 396 apps (about 0 hidden, 6 tabs built-in plus custom ones; 14 loose home screen apps and 3 folders). Restored on a real phone with Smart Launcher 6 Pro (backup data version 64): tabs, icons, folders, moved home icons, and drawer ordering for left and right handed with "stack apps from the bottom" on and off. Other versions may differ.

## If something goes wrong

Your original backup is never changed. Restore it in Smart Launcher (settings, backup/restore) and you're back where you were. Anything you changed on the phone after making that backup is lost, so make a fresh backup first and copy it to a computer.

If Smart Launcher crashes or won't respond after a restore (I haven't seen this happen, but other versions might differ):

1. Open Settings anyway. The notification shade and the Settings app don't need the launcher.
2. Set your phone's own launcher as default: Settings > Apps > Default apps > Home app.
3. Clear Smart Launcher's data or reinstall it (Settings > Apps > Smart Launcher > Storage > Clear data), open it and restore your original backup.
4. If the screen is frozen, start the phone in safe mode (hold the power button, long-press "Power off", confirm). It loads the stock launcher. Then do step 3.

Menus differ per phone brand. Search your phone's brand plus "safe mode" or "change default launcher" if you get stuck. Your backup files stay on the phone's storage when you clear data, but keep a copy on a computer.

## Tab icons

A tab's icon comes from a hidden category ID, not from its name. Most IDs give a blank folder, including `ai`, `money`, `health` and `photo`. Use `education` for AI, `finance` for money, `fitness` for health and `camera` for photos. The prompt has the full list and picks them for you.
