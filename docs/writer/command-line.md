# The command-line tool

`shotnotes` is the metadata writer for the terminal, on macOS, Windows and
Linux. It reads an export file, shows what would change, asks you to agree, and
writes the notes with [exiftool](https://exiftool.org/). Read
[The metadata writer](overview.md) first for how it matches and what it writes.
The [Lightroom plugin](lightroom.md) runs this tool for you.

[Install the metadata writer](../start/writer.md) says how to install it. It
needs exiftool, which you install first.

## A first run

Say the notes are in `shot-notes-2026-10-16.snexport` and the images are in
`~/Pictures/2026-10-16`:

```bash
shotnotes show shot-notes-2026-10-16.snexport
shotnotes write shot-notes-2026-10-16.snexport ~/Pictures/2026-10-16 --recursive
```

`show` lists the shots in the file, after checking that the file is whole.
`write` pairs the notes with the images, shows you every pair, shows what will
change, and writes only after you say yes.

## Commands

| Command | Does |
|---|---|
| `shotnotes show <export>` | Lists the shots in an export file. |
| `shotnotes match <export> <paths>` | Proposes which note goes with which image, and writes nothing to the images. |
| `shotnotes write <export> <paths>` | Matches, shows the changes, asks for consent, then writes. |
| `shotnotes certificate` | Makes the certificate and key that sign new [Content Credentials](content-credentials.md). |
| `shotnotes version` | The tool's version with its build number (`0.1.0 (8)`), and the exiftool, helper and signer it found. |

`<paths>` are folders and image files. The notes and the images must be as many.
If the export has more notes than you gave images, name the images the notes are
for. The images must come from one camera: from several, the tool says so and
stops, because the images are put in order by capture time, which two cameras'
clocks do not share.

## Options you will use

| Option | Does |
|---|---|
| `--recursive`, `-r` | Looks in the subfolders of the folders too. |
| `--note-order created\|recorded` | What puts the notes in order, before the n-th note is paired with the n-th image. `recorded` (the default) is the date and time recorded on the note, which has no seconds: notes of one minute stay in the order they were created. `created` is when each note was created, to the millisecond. |
| `--sidecar` | Writes XMP sidecars beside the images, not into them. |
| `--keep-camera-lens` | Keeps the lens and focal length the camera recorded, filling them in only where the file has none. The aperture is always replaced. |
| `--keep-originals` | Keeps each file it replaces as `NAME.EXT_original`. |
| `--kit-keywords` | Also writes the filters, lighting and accessories as keywords. |
| `--credentials add\|c2pa-file\|sidecar` | What to do with a file that has Content Credentials. The default is `add`. |
| `--exiftool <path>` | The exiftool to use, if not the one on the path. |
| `--jobs <n>`, `-j` | How many files to write at once, 1 to 8. The default is 4, or the number of processors if fewer. Use `--jobs 1` on a slow disk, such as a spinning one or a network drive. |
| `--yes`, `-y` | Writes without asking. |

## What it asks

The notes are paired with the images in order: the n-th note, in the order you
chose, with the n-th image, in the order the images were taken. The times written
on the notes are not used to check a pair, since notes are often written long
after the pictures, so nothing is flagged and you are not asked about the
camera's clock. At a terminal, `write` shows you every pair, with the whole date
of the note and of the image (and the offset from UTC when it is known), and
asks:

- **Enter** says you looked at the pairs.
- `m` moves a note to another place (the images stay in the order they were
  taken, and the notes between take the images of their neighbours), as often as
  you need.
- `x` leaves a note out of this run, and `p` puts it back, with its own image if
  no other note has taken it, else the first image no note has. The images no
  note has are listed under the pairs. The export file is not changed.
- `q` cancels.

Then it shows what will change: the number of files, what happens to files with
Content Credentials, and the fields of the first file as they are now and as they
will be. Press `d` to see every file. Only then does it write.

## Without a terminal

When it is not run at a terminal, or with `--yes`, it never guesses:

- `write` without `--yes` refuses to write.
- A proposal is refused even with `--yes`: a person must look at the pairs
  before anything is written, because writing is not undone. Look at them at a
  terminal, or in the desktop app or the Lightroom plugin, and write the pairs
  file they save.

A **pairs file** records what you confirmed, so that what is written is what you
saw. `--save-pairs <file>` saves the pairs, and `shotnotes write <export>
--pairs <file>` writes exactly those and matches nothing. The file is tied to one
export file by its checksum, and is refused if the export has changed.

## Cancelling

Press Ctrl+C. The tool stops cleanly and says what was written and what was not.
Files it was writing at that moment may be reported as failed, and they are then
as they were: a file is never left half written. If you cancel while it is still
reading the images or planning, nothing has been written.
