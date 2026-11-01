# Settings and your data

## Where your shots are

Your shots, kit and notes are kept on your phone, in the app's own database.
There is no account and nothing is sent to a server of Shot Notes. The
[privacy policy](https://shotnotes.app/privacy/) has the whole picture.

Two things leave the phone, and only when you ask:

- **A place name.** When you tap the location button, the app can send the
  coordinates to Apple (on iOS) or Google (on Android) to find the name of the
  place. **Look up place names**, in Settings, turns this off; the location
  button then records coordinates only and sends nothing.
- **A map.** The map button of a shot hands its location to your phone's map
  app.

## What is in Settings

- **Carry over:** what a new shot copies from the last one (see
  [Logging a shot](shots.md)).
- **Look up place names:** on by default.
- **Data:** how many kit items and manufacturers you have.
- **Export shots:** a day, a date range or all shots, for the metadata
  writer (see [Searching and exporting](search-and-export.md)), and how many
  exports you have left this month.
- **Recently deleted:** shots and kit you deleted in the last 30 days, each
  with **Restore**. After that a deleted shot is erased for good.
- **About Shot Notes:** the version, the privacy policy and the licences of
  what the app is built from.
- **Report a problem:** see below.

![The Settings tab](../screenshots/app-settings-light.svg#only-light){ .phone loading=lazy }
![The Settings tab](../screenshots/app-settings-dark.svg#only-dark){ .phone loading=lazy }

## Backup

The app has no backup of its own yet: **Back up everything** and **Restore
from backup** are marked as coming in Beta 2. Until then, your phone's own
backup (iCloud Backup or a backup to your computer on an iPhone, Android's
backup on an Android phone) includes your shots. The monthly export count is
left out of backups on purpose.

To keep a copy now, export your shots and keep the files (see
[Searching and exporting](search-and-export.md)).

## Reporting a problem

**Report a problem** opens a new issue in the public Shot Notes support
repository on GitHub, with the form already filled in with the version of the
app, the operating system and the device. Everyone can read the issue, and you
need a GitHub account to file it. Nothing is sent until you tap **Open
GitHub**, and you can change everything on that page first.

You can add the app's **error log**. It keeps the errors the app did not
expect, with the time, the version and where in the code they happened, and it
is made not to hold your shots, notes, places or coordinates. **Show the log**
shows exactly what would be added, and **Clear the log** deletes it.

See [Getting help](../help.md) for the other ways to ask or report.
