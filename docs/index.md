# Shot Notes

Shot Notes keeps notes on the shots you take with manual lenses: the aperture,
focal length, lens, kit and place of each frame, which a lens without
electronic contacts can't tell the camera. Your notes stay on your own
devices. Later, they can be written into the metadata of the matching image
files.

!!! note "Beta"

    Shot Notes is in beta. The programs for your computer, the metadata writer
    and the Lightroom plugin, are on the
    [Releases page](https://github.com/shotnotes/support/releases) as
    pre-releases. The mobile apps are only available to testers for now, and
    are not in the app stores. Testing has started on iPhone, and Android is
    coming soon.
    [Announcements](https://github.com/shotnotes/support/discussions/categories/announcements)
    will say when and how to join.

## The parts

- **[The app](app/shots.md)**, for iOS and Android, where you note each shot as
  you take it.
- **[The metadata writer](writer/overview.md)**, for macOS, Windows and Linux:
  a [command-line tool](writer/command-line.md) and a
  [desktop app](writer/desktop-app.md) that read the notes you export from the
  app and write them into the metadata of your image files.
- **A [Lightroom Classic plugin](writer/lightroom.md)**, which matches the notes
  to the photos you select and writes them through the command-line tool.

## How it fits together

1. In the app, **note each shot** as you take it: the lens, the aperture, the
   focal length, and anything else you want to keep.
2. After you download your images, **export your notes** from the app to your
   computer.
3. With the desktop app, the command-line tool or the Lightroom plugin,
   **match the notes to the images**, check the matches, and write the notes
   into the metadata of the images.

[Get started](start/how-it-fits.md) says how to get each part, and takes you
through your first shots.

## Your notes are yours

The notes stay on your device until you export them. The programs for your
computer, the metadata writer and the Lightroom plugin, run on your computer and
send nothing. Read the
[privacy policy](https://www.shotnotes.app/privacy/) for the details.
