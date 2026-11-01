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

The writer compares the time of each note, which is the phone's clock, with the
time each image was taken, which is the camera's clock. Cameras' clocks drift,
so it works out how far apart the two are by itself, and says how well the
times fit. If you know the offset of a camera's clock, such as `+12s` or
`-1h30m`, you can give it and the writer trusts it.

A pair is clear when the note is dated shortly after the image: by default, up
to 10 minutes after. Anything it is unsure of is flagged for you to look at:

- a note and an image far apart in time;
- an image with no note, or a note with no image, which you can leave out of
  this run (the export file is not changed);
- a clock that is further out than a time zone or daylight saving explains,
  such as images from another shoot, or a camera whose date was reset.

This is why it helps to log a shot soon after taking it, with the phone's time
set automatically.

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
