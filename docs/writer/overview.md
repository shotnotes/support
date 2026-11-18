# The metadata writer

The app keeps your notes. The metadata writer puts them into your photos: the
aperture, the focal length, the lens, the shutter speed, the place and your
notes, written into the metadata of the image files, where Lightroom and other
programs read them.

There are three ways to run it. They do the same job with the same rules:

- the [desktop app](desktop-app.md), Shot Notes Writer, for macOS, Windows and
  Linux, with windows and pictures;
- the [command-line tool](command-line.md), `shotnotes`;
- the [Lightroom Classic plugin](lightroom.md), which runs inside Lightroom on
  the photos you select.

## What you need

- An export file from the app, with the extension `.snexport` (see
  [Searching and exporting](../app/search-and-export.md)).
- The image files, on your computer.
- [exiftool](https://exiftool.org/), which does the writing. Shot Notes does not
  include it. Install it yourself, from your system's package manager or from
  the exiftool website ([Install the metadata writer](../start/writer.md) has
  the commands).

Files it can write: JPEG, HEIF, TIFF and DNG. Raw files in other formats, such
as CR3, NEF or ARW, are not supported yet.

!!! note "Photos on a WebDAV drive, on Windows"

    Windows opens no file of more than 50 MB from a network drive that uses
    WebDAV, unless you raise its limit. Large photos, such as the DNG files of
    a high-resolution camera, then fail: exiftool says the file is not found,
    and copying the file in File Explorer says it is too big. Explorer still
    lists the file, which makes it look as if the writer were at fault. It is
    Windows' own limit, and it applies to every program.

    To raise it, run this in a PowerShell that you opened as administrator. It
    sets the limit to 4 GB, the largest value the setting takes:

    ```powershell
    reg add HKLM\SYSTEM\CurrentControlSet\Services\WebClient\Parameters /v FileSizeLimitInBytes /t REG_DWORD /d 4294967295 /f
    Restart-Service WebClient
    ```

    Then map the drive again if it still fails. This changes a Windows setting
    for every program, so make a copy of the registry key first if you want to
    be able to undo it. Reading large photos over WebDAV is slow, and a copy on
    a local disk is the dependable way to work.

## The steps

1. **Choose** the export file and the images the notes are for.
2. **Review** which note belongs to which image. Nothing is written yet.
3. **Check** what will change in each file, and choose where the notes go.
4. **Write.**

Nothing is written until you have seen every pair and agreed. You choose the
images the notes are for, and the notes and the images must be as many: the
writer never guesses to fill the gap. A RAW file and the JPEG next to it count
as one image, and both get the note.

## How it matches notes to images

The n-th note is paired with the n-th image: the images in the order they were
taken, the notes in the order you choose. A note's times cannot be trusted
(a note is often written long after the picture), so the writer does not use
them to check a pair, does not flag any, and does not ask about the camera's
clock. You choose how the notes are put in order:

- **Recorded date time** (the default): the date and time recorded on the note,
  which has no seconds. Notes of one minute stay in the order they were created.
- **Creation date time**: when each note was created, to the millisecond. It is
  the order you wrote the notes in.

You then look at every pair. If one is wrong, move the note to the place of its
image, or leave a note out of this run (the export file is not changed). The
images must all come from one camera: the images are put in order by capture
time, which two cameras' clocks do not share, so the writer refuses images from
more than one.

This is why it helps to write your notes in the order you shoot.

## What it writes

| From your shot | Written as |
|---|---|
| Aperture | The f-number. It always replaces the camera's, because a lens without contacts cannot tell the camera its aperture. |
| Focal length and lens | The focal length, the lens name, maker and serial number, and the lens's widest aperture and focal length range. By default they replace the camera's where they differ, and fill in where the file has none. Choose to keep the camera's instead if you prefer. |
| Shutter speed and ISO | Filled in when the file has none. The camera's are never replaced. |
| Coordinates and place | Filled in when the file has none. |
| Your note | The description of the image, when the file has none, or when an earlier write of Shot Notes put the note there. |
| The whole shot | A set of Shot Notes fields, in a namespace of its own, that carries everything, including the filters, lighting and accessories. |

Filters, lighting and accessories can also be written as keywords, a choice
that is off by default.

**It never changes when the photo was taken.** The capture time stays the
camera's.

A value you or the camera put in the file is not overwritten, except the aperture
and, by default, the lens and focal length. If you write a shot again after you
edit its note, the note follows. A caption you changed in Lightroom is left
alone.

## Into the file, or beside it

The notes can go into the image file, or into an XMP sidecar, a small file
named like the image with `.xmp` as its extension. An existing sidecar is
updated, not replaced: the settings of Lightroom in it are kept.

Which to choose depends on Lightroom Classic, which reads some things from a
sidecar but not others, for a DNG:

- **In the file:** Lightroom shows the aperture, the focal length, the lens
  name, the keywords and the description.
- **In a sidecar:** Lightroom shows the lens name, the keywords and the
  description, but takes the aperture and the focal length from the DNG itself.
  These two are what a manual lens note is for, so write into the file if you
  want them shown.

Files the writer cannot write into get a sidecar, and it says so.

By default the original file is replaced, without a backup copy beside it.
You can ask to keep each original as `NAME.EXT_original`. Keep your own backup of
your photos either way.

## Content Credentials

Some cameras, the Leica M11-P among them, sign each photo with Content
Credentials, and any change to the file would break that signature. The writer
can add its own signed record on top of the camera's. See
[Content Credentials](content-credentials.md).

## Photos already in Lightroom

If a photo is already in a Lightroom catalogue, Lightroom shows a metadata
conflict after the write. Choose **Metadata**, **Read Metadata from Files**. The
[plugin](lightroom.md) does that for you.
