# The Lightroom Classic plugin

The plugin matches the notes in an export file to the photos you select in
Adobe Lightroom Classic, and writes them into the photos' metadata. It does the same
job as the [desktop app](desktop-app.md), with the photos chosen inside
Lightroom, and it runs the [command-line tool](command-line.md) for the writing.
Read [The metadata writer](overview.md) first for how it matches and what it
writes.

**Lightroom Classic only.** The cloud-based Lightroom has no plugins. The plugin
is tested on Lightroom Classic 15 (15.1.1).

It needs [exiftool](https://exiftool.org/), which is not in the plugin's zip.
On macOS, install it with [Homebrew](https://brew.sh/): `brew install exiftool`.
On Windows, install it with `winget`: `winget install OliverBetz.ExifTool`. The
installer on the exiftool website works on both.
[Install the metadata writer](../start/writer.md#lightroom-classic-plugin)
says how to add the plugin to Lightroom.

## Using it

Select the photos in the Library, then choose **Library**, **Plug-in Extras**,
**Match Shot Notes to the Selected Photos...**. The best time is straight after
importing, before you delete any photos. If you already deleted some, delete their
shots in the app before you export, or leave those notes out when asked.

1. **Choose the export file.** A window says so first, with **Note ordering**,
   then the file chooser opens. The notes are paired with the photos in order:
   the n-th note with the n-th photo, in the order the photos were taken. Note
   ordering chooses what puts the notes in order: **Recorded date time** (the
   default), the date and time recorded on the note, which has no seconds, so
   notes of one minute stay in the order they were created, or **Creation date
   time**, when each note was created. The photos must all come from one camera: from
   several, the plugin says so and stops.
2. **Which notes?** If the export has more notes than you selected photos, you
   tick the notes that are for these photos. Nothing is suggested: the times of
   the notes cannot be trusted, so you decide. The photos are the ones you
   selected: if some do not belong, cancel, deselect them in Lightroom and match
   again.
3. **Check the pairs.** Each note is shown with its whole date beside the
   thumbnail of its photo. Nothing is flagged: you decide every pair. You can
   change a photo with the menu (it offers the photos that no note has; putting a
   note beside a photo another note has is a move, not a swap), put the notes in
   another order with **Move note up**, **Move note down** or **Move note to
   place** (the photos stay in the order they were taken, and the notes between
   take the photos of their neighbours), or leave a note out. Tick **I have
   looked at the pairs**; **Next** is available when it is ticked. Any change to
   the pairs unticks it, so that you look again.
4. **Confirm the changes.** The window shows how many photos change and, one
   photo at a time, every field that changes. Beside it you see the photo's
   Content Credentials now and after the write. The options are those of the
   command-line tool: kit keywords, keeping the camera's lens and focal length,
   sidecars, and keeping originals. When you change an option, choose **Update
   the changes** to see the new plan before **Write** is allowed, so what you
   see is always what will be written. **Back** returns to the pairs, which keep
   what you changed.
5. **Write.** Lightroom first saves into the files the metadata its catalogue
   holds. The tool then writes exactly the pairs you confirmed, Lightroom reads
   the files back, and the plugin checks that Lightroom shows what was written.
   It tells you which photos it does not show, and then you choose **Metadata**,
   **Read Metadata from Files**.

Cancel at any time in the progress bar. It stops after the files in hand, and a
file is never left half written.

## Where the notes show in Lightroom

Lightroom shows the camera's fields, aperture, focal length and lens, with the
values the notes gave them. The note and the kit are also put in fields of the
plugin's own, shown under the **Shot Notes** set in the Metadata panel and
searchable in the Library filter. Lightroom does not show custom metadata
otherwise.

A virtual copy shares its original's file: the file is matched and written once,
and every copy gets the note.

If you edited a photo's capture time in the catalogue (**Edit Capture Time**),
the plugin tells you, because the matching reads the capture time from the file.

## Content Credentials

If a photo has Content Credentials and you have no certificate yet, the window
asks for your name and makes one for you, or you can give a certificate and
private key of your own (PEM files). The plugin remembers the files. See
[Content Credentials](content-credentials.md).

## If something goes wrong

The plugin keeps a log of what it did, with the tool's command lines and exit
codes, in `ShotNotes.log`, in the `LrClassicLogs` folder of your Documents
folder. Attach it when you [report a problem](../help.md), after reading it for
anything you would rather not make public.
