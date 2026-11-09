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

Match straight after you import, before you delete any photos. If you already
deleted some, delete their shots in the app before you export, or leave those
notes out when it asks.

`show` lists the shots in the file, after checking that the file is whole.
`write` matches the notes to the images, asks about anything it is unsure of,
shows what will change, and writes only after you say yes.

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
for.

## Options you will use

| Option | Does |
|---|---|
| `--recursive`, `-r` | Looks in the subfolders of the folders too. |
| `--clock-offset <offset>` | How far the camera's clock is ahead of the phone's, such as `+12s` or `-1h30m`, instead of working it out. For one body: `"Canon EOS R5=+12s"`. Repeat the option for each camera. |
| `--tolerance <time>` | How long after its image a note may be dated before the pair is flagged. The default is `10m`. |
| `--sidecar` | Writes XMP sidecars beside the images, not into them. |
| `--keep-camera-lens` | Keeps the lens and focal length the camera recorded, filling them in only where the file has none. The aperture is always replaced. |
| `--keep-originals` | Keeps each file it replaces as `NAME.EXT_original`. |
| `--kit-keywords` | Also writes the filters, lighting and accessories as keywords. |
| `--credentials add\|c2pa-file\|sidecar` | What to do with a file that has Content Credentials. The default is `add`. |
| `--exiftool <path>` | The exiftool to use, if not the one on the path. |
| `--jobs <n>`, `-j` | How many files to write at once, 1 to 8. The default is 4, or the number of processors if fewer. Use `--jobs 1` on a slow disk, such as a spinning one or a network drive. |
| `--yes`, `-y` | Writes without asking. |

## What it asks

At a terminal, `write` asks about what the matching was unsure of, in this
order:

1. The clock, if it is further out than a time zone or daylight saving
   explains: keep it, or give the offset.
2. The notes and images with no partner, which are left out of this run. The
   export file is not changed.
3. Each flagged pair, with the other images it could be: keep it, use another,
   or leave the note out.

Then it shows what will change: the number of files, what happens to files with
Content Credentials, and the fields of the first file as they are now and as they
will be. Press `d` to see every file. Only then does it write.

## Without a terminal

When it is not run at a terminal, or with `--yes`, it never guesses:

- `write` without `--yes` refuses to write.
- A proposal with anything for a person to decide is refused even with `--yes`.
  Decide it at a terminal, or save the decisions in a pairs file.

A **pairs file** records what you confirmed, so that what is written is what you
saw. `--save-pairs <file>` saves the pairs, and `shotnotes write <export>
--pairs <file>` writes exactly those and matches nothing. The file is tied to one
export file by its checksum, and is refused if the export has changed.

## Cancelling

Press Ctrl+C. The tool stops cleanly and says what was written and what was not.
Files it was writing at that moment may be reported as failed, and they are then
as they were: a file is never left half written. If you cancel while it is still
reading the images or planning, nothing has been written.
