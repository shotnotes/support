# Install the metadata writer

The metadata writer runs on **macOS** (Apple Silicon), **Windows** (64-bit) and
**Linux** (x86-64 and arm64). It comes as a desktop app, **Shot Notes Writer**,
and a command-line tool, `shotnotes`. Install either, or both. There is also a
[Lightroom Classic plugin](#lightroom-classic-plugin).

!!! note "Beta"

    Shot Notes is in beta. The programs are on the
    [Releases page](https://github.com/shotnotes/support/releases) as
    pre-releases: they work, and they may still change.
    [Announcements](https://github.com/shotnotes/support/discussions/categories/announcements)
    will say what is new.

The programs are free to use, under the
[terms of use](https://github.com/shotnotes/support/blob/main/TERMS.md). By
installing them you agree to the terms.

## What it needs

- **macOS:** an Apple Silicon Mac. The desktop app needs macOS 12 or later; the
  command-line tool, and so the Lightroom plugin, need macOS 14 or later.
- **Windows:** 64-bit Windows 10 or later.
- **Linux:** a 64-bit system, x86-64 or arm64, with glibc 2.39 or newer (Ubuntu
  24.04, Debian 13 or Fedora 40, or later). The desktop app needs the desktop's
  GTK 3.

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

    The `.deb` and `.rpm` packages below install it themselves. On Debian and
    Ubuntu, the package is `libimage-exiftool-perl`.

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

    Or use [Homebrew](https://brew.sh/), which installs exiftool with them. The
    desktop app needs macOS 12 or later, and the command-line tool macOS 14 or
    later:

    ```bash
    brew tap shotnotes/tap
    brew trust shotnotes/tap
    brew install --cask shotnotes-writer
    ```

    ```bash
    brew install shotnotes
    ```

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

    On Debian, Ubuntu and their derivatives, and on Fedora and its derivatives,
    install a package from the
    [Releases page](https://github.com/shotnotes/support/releases). It installs
    exiftool with it. Download the files for your processor (`amd64` or `arm64`
    for a `.deb`, `x86_64` or `aarch64` for an `.rpm`). `shotnotes` is the
    command-line tool and the helper, and `shotnotes-writer` is the desktop app:

    ```bash
    sudo apt install ./shotnotes_<version>_amd64.deb ./shotnotes-writer_<version>_amd64.deb
    ```

    ```bash
    sudo dnf install ./shotnotes-<version>-1.x86_64.rpm ./shotnotes-writer-<version>-1.x86_64.rpm
    ```

    Each command installs both; give it one file to install just that one. A
    system with an older glibc than the one required is refused, with a message
    about `libc6` or `glibc`. The packages are not signed yet, and do not update
    by themselves: install the newer files over them.

    For another Linux, the desktop app is also an AppImage. Download the file
    for your processor (`x64` or `arm64`), make it executable and run it:

    ```bash
    chmod +x shotnotes-writer-*.AppImage
    ./shotnotes-writer-*.AppImage
    ```

    The command-line tool is a download too,
    `shotnotes-<version>-linux-<processor>.tar.gz`, from the Releases page. It
    holds `shotnotes` and the helper beside it, `shotnotes-c2pa`, which must stay
    together. Put them in a folder on your path, or run `./shotnotes` from where
    you unpacked them. It is also on
    [Linuxbrew](https://docs.brew.sh/Homebrew-on-Linux), which installs exiftool
    with it:

    ```bash
    brew tap shotnotes/tap
    brew trust shotnotes/tap
    brew install shotnotes
    ```

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

Download the new files and replace the old ones. (With Homebrew, `brew upgrade`.) The writer keeps nothing of yours, apart from its
settings and the certificate it made for you, if any.
