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

![The Choose step: the export file and the images, both counted](../screenshots/writer-choose-light.svg#only-light){ loading=lazy }
![The Choose step: the export file and the images, both counted](../screenshots/writer-choose-dark.svg#only-dark){ loading=lazy }

A check says whether the shots and the images are as many. **Match** stays off
until they are. When they are not, choose the notes and the images you want to
leave out, from all of them: **Choose notes...** and **Choose images...**. They
are left out of this run only: the export file and the images are not changed.
What you left out stays listed, with **Put back**. You can also **Add images**.

The images must all come from one camera. They are put in the order of their
capture times, which two cameras' clocks do not share, so if the images come
from more than one body the app says so and **Match** stays off until you choose
the images of one camera only (or leave the others out).

The notes and the images are paired in order: the n-th note with the n-th
image, in the order the images were taken. Under **Note ordering** you choose
what puts the notes in order:

- **Recorded date time**, the default: the date and time recorded on each note,
  which you can change by hand in the app. It has no seconds, so notes of one
  minute can tie; those stay in the order they were created.
- **Creation date time**: when each note was created, to the millisecond, which
  the app records in the note's own id. It is the order you wrote the notes in.

The times written on the notes are not used for anything else, because notes
are often written long after the pictures: the app does not guess from them
which pairs are doubtful, and does not ask about the camera's clock. Changing
the ordering matches again, so what you changed by hand on Review is not kept.

## 2. Review

The top says how many pairs there are. Below, one row for each place in the
list. The images stay in the order they were taken, and each note is paired with
the image in its row. Nothing is flagged: you decide every pair. A row has:

- the place, from 1, and the image, with its picture and its capture time;
- the note, with a handle at its left;
- **Exclude**, a tick that leaves the note out of this run. Untick it to put the
  note back, with the image it had if no other note has taken it;
- three buttons to move the note: up, down, or to a place you type.

To pair a note with another image of the shoot, move the note: drag it by its
handle, or use the buttons, which do the same without a drag. The notes between
take the images of their neighbours, and the images stay where they are. A note
that is left out has **Choose an image...** when some image has no note: it lists
those images, and using one pairs it with the note.

![The Review step: one row for each note, with its image](../screenshots/writer-review-light.svg#only-light){ loading=lazy }
![The Review step: one row for each note, with its image](../screenshots/writer-review-dark.svg#only-dark){ loading=lazy }
![The images no note has, to choose from for a note](../screenshots/writer-review-pair-light.svg#only-light){ loading=lazy }
![The images no note has, to choose from for a note](../screenshots/writer-review-pair-dark.svg#only-dark){ loading=lazy }

The notes are put in the order you chose on Choose: by default the order they
were created. Write your notes in the order you shoot, and the n-th note is
paired with the n-th image. Look at the first pair, the last
and a few between: if one is wrong, the notes are in another order than the
images, and you put them right by moving the notes in the list.

One tick, **I have looked at the pairs**, says you did. **Write** is available
when it is ticked. Any change to the pairs unticks it, so that you look again.
What you changed by hand is kept if you match again.

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
Resources. On Linux they are in `/usr/share/doc/shotnotes-writer` when you
installed the `.deb` or `.rpm`, and inside the AppImage, which unpacks itself
when run with `--appimage-extract`. The terms are also at
https://github.com/shotnotes/support/blob/main/TERMS.md.

The settings are kept on this computer only. Your choices on the Write step are
remembered.
