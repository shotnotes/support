# Install the metadata writer

The metadata writer runs on **macOS** (Apple silicon), **Windows** (64-bit) and
**Linux** (x86-64 and arm64). It comes as a desktop app, **Shot Notes Writer**,
and a command-line tool, `shotnotes`. Install either, or both. There is also a
[Lightroom Classic plugin](#lightroom-classic-plugin).

!!! note "Beta"

    Shot Notes is in beta. The programs are on the
    [Releases page](https://github.com/shotnotes/support/releases) as
    pre-releases: they work, and they may still change.
    [Announcements](https://github.com/shotnotes/support/discussions/categories/announcements)
    will say what is new.

## What it needs

- **macOS:** an Apple silicon Mac. The desktop app needs macOS 12 or later; the
  command-line tool, and so the Lightroom plugin, need macOS 14 or later.
- **Windows:** 64-bit Windows 10 or later.
- **Linux:** a 64-bit system, x86-64 or arm64. No minimum version is set.

## 1. Install exiftool first

The writer changes your image files with [exiftool](https://exiftool.org/),
which is not part of it. Install it first:

=== "macOS"

    ```bash
    brew install exiftool
    ```

=== "Windows"

    ```powershell
    winget install OliverBetz.ExifTool
    ```

=== "Linux"

    On Debian and Ubuntu, the package is `libimage-exiftool-perl`.

    ```bash
    sudo apt install libimage-exiftool-perl
    ```

The installer on [exiftool.org](https://exiftool.org/install.html) works too.
If the writer cannot find exiftool, the desktop app asks in its settings for
the path, and the command-line tool has `--exiftool <path>`.

## 2. Install the writer

=== "macOS"

    From the [Releases page](https://github.com/shotnotes/support/releases):

    - **The desktop app:** download `shotnotes-writer-<version>-macos-arm64.zip`,
      unzip it, and move **Shot Notes Writer** to your Applications folder. It
      is signed and notarised by Apple, so it opens as any app does.
    - **The command-line tool:** download `shotnotes-<version>-macos-arm64.tar.gz`
      and unpack it. It holds `shotnotes` and the helper beside it,
      `shotnotes-c2pa`, which must stay together. Put them in a folder on your
      path, or run `./shotnotes` from where you unpacked them.

    A Homebrew tap, `shotnotes/tap`, is planned, with the cask
    `shotnotes-writer` and the formula `shotnotes`. Until the announcements say
    it is there, use the downloads.

=== "Windows"

    From the [Releases page](https://github.com/shotnotes/support/releases):

    - **The desktop app:** download `shotnotes-writer-<version>-windows-x64.zip`,
      unzip it, and open `shot_notes_writer.exe` in the folder. Keep the files
      of the folder together.
    - **The command-line tool:** download `shotnotes-<version>-windows-x64.zip`
      and unzip it. It holds `shotnotes.exe` and the helper beside it,
      `shotnotes-c2pa.exe`, which must stay together. Run it from a terminal.

    The programs are not signed yet, so Windows may warn that it protected your
    PC. Check the download as below before you choose **Run anyway**.

=== "Linux"

    The desktop app is an AppImage. From the
    [Releases page](https://github.com/shotnotes/support/releases), download the
    file for your processor (`x64` or `arm64`), make it executable and run it:

    ```bash
    chmod +x shotnotes-writer-*.AppImage
    ./shotnotes-writer-*.AppImage
    ```

    The command-line tool is a download too,
    `shotnotes-<version>-linux-<processor>.tar.gz`, from the Releases page. It
    holds `shotnotes` and the helper beside it, `shotnotes-c2pa`, which must stay
    together. Put them in a folder on your path, or run `./shotnotes` from where
    you unpacked them. A [Linuxbrew](https://docs.brew.sh/Homebrew-on-Linux)
    formula is planned with the Homebrew tap, which will install exiftool with
    it.

## Check a download

Each release lists the checksum of every file in `SHA256SUMS`. Work out the
checksum of your download, and compare it with its line there, so that you know
it is the file that was published:

=== "macOS and Linux"

    ```bash
    shasum -a 256 shotnotes-writer-<version>-macos-arm64.zip
    ```

=== "Windows"

    ```powershell
    Get-FileHash shotnotes-writer-<version>-windows-x64.zip -Algorithm SHA256
    ```

## Try it

```bash
shotnotes version
```

shows the tool's version, and the exiftool, the helper and the signer it found.
For the desktop app, open it: it asks for an export file.

## Lightroom Classic plugin

The plugin is a download from the Releases page,
`shotnotes-lightroom-<version>.zip`, for Lightroom Classic 15 (tried on 15.1.1)
on macOS and Windows. The cloud-based Lightroom has no plugins.

1. Install [exiftool](#1-install-exiftool-first). The plugin does not contain it.
2. Unzip the file. It holds a folder, `ShotNotes.lrplugin`, with the
   command-line tool for each system inside it. Keep it somewhere that stays,
   such as your Documents folder, because Lightroom runs it from there.
3. In Lightroom Classic, choose **File**, **Plug-in Manager**, **Add**, and
   choose the `ShotNotes.lrplugin` folder.

[The Lightroom plugin](../writer/lightroom.md) says how to use it.

## Updating

Download the new files and replace the old ones. (With Homebrew, once the tap
is there, `brew upgrade`.) The writer keeps nothing of yours, apart from its
settings and the certificate it made for you, if any.
