# Shot Notes Writer, the desktop app

Shot Notes Writer is the metadata writer with windows. It runs on macOS,
Windows and Linux. It lists the shots in your export file, proposes which image
each one belongs to, shows you what would change, and writes only after you
agree. Read [The metadata writer](overview.md) first for how it matches and what
it writes.

It needs [exiftool](https://exiftool.org/), which you install first, or give its
path in the settings.

The window has a fixed size, so every step fits in it, and the pages scroll
when they are long. It follows the system's light or dark setting.

## 1. Choose

Choose the export file, then the images: a folder with its subfolders, or
files. Each choice has a card that says what was found: the shots and the span
of their dates, the images, the folders and the camera bodies.

![The Choose step: the export file and the images, both counted, with the camera clock to work out](../screenshots/writer-choose-light.svg#only-light){ loading=lazy }
![The Choose step: the export file and the images, both counted, with the camera clock to work out](../screenshots/writer-choose-dark.svg#only-dark){ loading=lazy }

Match straight after you import, before you delete any photos. If you already
deleted some, delete their shots in the app before you export, or leave those
notes out here.

A check says whether the shots and the images are as many. **Match** stays off
until they are. When they are not, it tells you where the times disagree: a note
with no image near it (with the two nearest images), or an image with no note.
For each, you can **Leave this out of this run**, which does not change the
export file, or **Add images**.

The camera's clock is worked out for you. If you know it, give it for each
camera, such as `+12s` or `-1h30m`, and it is trusted.

## 2. Review

The top says how the clock was settled, how well the times fit, how many pairs
are clear and how many need a look. Below, one row for each pair in time order:

- the note;
- a mark, **ok**, **?** or **!**, in words as well as colour;
- the image, with its picture;
- how long after the image the note is dated.

The arrow at the end of a row opens any pair. There you can choose another
image for the note (choosing an image that another note holds swaps the two),
shift this pair and every pair after it up or down by one image, leave the note
out, or say **I checked this pair**. A timeline of the whole run shows where
the lines slant, which is where a run has slipped by one.

![The Review step: one row for each note, with its image and how long after the image the note is dated](../screenshots/writer-review-light.svg#only-light){ loading=lazy }
![The Review step: one row for each note, with its image and how long after the image the note is dated](../screenshots/writer-review-dark.svg#only-dark){ loading=lazy }
![One pair open, with the other images it could be and the choices for it](../screenshots/writer-review-pair-light.svg#only-light){ loading=lazy }
![One pair open, with the other images it could be and the choices for it](../screenshots/writer-review-pair-dark.svg#only-dark){ loading=lazy }

If the clock is further out than a time zone explains, the app asks first
whether the times fit, in which case it uses the offset, or do not, in which case
you choose other images.

The clear pairs are confirmed together with one tick. **Write** is available
only when nothing is left to decide. What you changed by hand is kept if you
match again.

## 3. Write

Choose:

- where the notes go: into the files, or into XMP sidecars;
- what to do with the camera's lens and focal length: replace them with the
  notes' where they differ, or keep the camera's. The aperture is always
  replaced;
- what to do with [Content Credentials](content-credentials.md), when a file
  has them.

You see the changes to one file at a time, before and after, with **Previous**
and **Next**. If you changed pairs by hand or left things out, a line sums it
up, with the list one click away. Writing shows its progress, and you can cancel
it: it stops after the files in hand, and no file is left half written.

![The Write step: where the notes go, and the fields that change in one file, before and after](../screenshots/writer-write-light.svg#only-light){ loading=lazy }
![The Write step: where the notes go, and the fields that change in one file, before and after](../screenshots/writer-write-dark.svg#only-dark){ loading=lazy }

## 4. Done

What was written, and what failed, with the reason for each file that failed.

![The Done step: 7 written, 0 failed](../screenshots/writer-done-light.svg#only-light){ loading=lazy }
![The Done step: 7 written, 0 failed](../screenshots/writer-done-dark.svg#only-dark){ loading=lazy }

## Settings

The gear, or Cmd+, on macOS and Ctrl+, elsewhere, holds:

- the path of exiftool, by default the one on the system's path;
- the path of the Content Credentials helper, the program that reads and signs
  them (it comes with the app);
- the certificate and key that sign Content Credentials;
- whether to keep the originals;
- whether to also write the kit as keywords.

**Licences...** lists the licences of the software in the app. The terms of use,
and the licences of the program's other parts, are in the files `TERMS.md`,
`NOTICES.md` and `LICENCES.txt`. On Windows they are in the app's folder. On
macOS they are inside the app: choose Show Package Contents, then Contents and
Resources. On Linux they are inside the AppImage, which unpacks itself when run
with `--appimage-extract`. The terms are also at
https://github.com/shotnotes/support/blob/main/TERMS.md.

The settings are kept on this computer only. Your choices on the Write step are
remembered.
