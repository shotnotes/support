# Your first shots

From the first shot to a photo with its notes. It takes about ten minutes, and
three or four shots are enough. You need the [app](app.md) on your
phone, the [writer](writer.md) on your computer, and a camera with a manual
lens.

## 1. On the phone, as you shoot

1. Add the lens to **Kit**, if you have not.
2. After each shot, tap **+**, check the lens, the aperture and the focal
   length, and tap **Save**. Do it soon after taking the shot. The notes
   are matched to the photos by time.

![A new shot, with the aperture chosen](../screenshots/app-new-shot-light.svg#only-light){ .phone loading=lazy }
![A new shot, with the aperture chosen](../screenshots/app-new-shot-dark.svg#only-dark){ .phone loading=lazy }

## 2. Export the notes

1. In the **Shots** tab, tap **Select**, choose the shots, and tap **Export**.
2. Send the file, which ends in `.snexport`, to your computer: AirDrop, a cloud
   drive, email or a cable.

[Searching and exporting](../app/search-and-export.md) has the other ways to
export, and says how many shots you can export a month.

## 3. Put the photos on the computer

Copy the photos off the camera in your usual way, in a folder of their own
if you can.

## 4. Write the notes into them

=== "Desktop app"

    1. Open **Shot Notes Writer**. Choose the export file, then the folder with
       the photos. **Match** is available when the notes and the images are as
       many.
    2. Look at the pairs. The clear ones are confirmed with one tick, and the
       ones the writer is unsure of are marked.
    3. Choose where the notes go (into the files, or into XMP sidecars), and
       look at the changes. **Write** when you agree.

    [The desktop app](../writer/desktop-app.md) goes through each step.

=== "Command line"

    ```bash
    shotnotes write shot-notes-2026-10-16.snexport ~/Pictures/2026-10-16
    ```

    It shows what it will change, and writes only after you say yes.
    [The command-line tool](../writer/command-line.md) has the options.

=== "Lightroom Classic"

    Import the photos, select them, and choose **Library**, **Plug-in Extras**,
    **Match Shot Notes to the Selected Photos...**.
    [The Lightroom plugin](../writer/lightroom.md) says what each window asks.

## 5. See the result

Open a photo in any program that shows metadata, or in Lightroom's Metadata
panel. The aperture, the focal length and the lens are those of your notes, and
the note itself is in the description, unless the file had one.

If the camera signs its files (the Leica M11-P does), read
[Content Credentials](../writer/content-credentials.md) first: writing into a
signed file needs a choice.

## If it does not go as planned

The writer does not guess. When the notes and the photos are not as many, or a
time does not fit, it says so and asks. [How matching works](../writer/overview.md)
explains why, and [Getting help](../help.md) says where to ask.
