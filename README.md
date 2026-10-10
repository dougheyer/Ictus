# Ictus

**Time-based music notation.** Coming soon...

### ⬇ [Download ictus-convert](../../releases/latest) — MusicXML, LilyPond and MNX, any of them in, any of them out

> Note: the **Code** button above gives you this page and the license, not the program.
> The converter is a release download: use the link above, or **Releases** in the sidebar.

---

## Available now: the converter

While the rest of Ictus is in development, one part of it is useful on its own: a
converter between **MusicXML**, **LilyPond** and **MNX**, any of the three in and any
of the three out. It creates an image of the result, and lists what could not be
carried across.

### Download the one for your system

| your system | download |
| --- | --- |
| Windows | `ictus-convert-0.4-windows-x64.zip` |
| Mac with Apple silicon (M1, M2, ...) | `ictus-convert-0.4-macos-arm64.zip` |
| Mac with an Intel processor | `ictus-convert-0.4-macos-x64.zip` |
| Linux | `ictus-convert-0.4-linux-x64.zip` |
| anything else, with Java 8 or newer installed | `ictus-convert-0.4.zip` |

## Installation

### ictus-convert

Unzip the download into a folder of your choice. The Windows, Mac and Linux downloads
each have their own built-in Java, so Java does not have to be installed on your
computer.

**On a Mac**, one more step, the first time only. Open Terminal (in Applications >
Utilities), type `cd` and a space, drag the `ictus-convert-0.4` folder into the
Terminal window, and press Enter. Then type:

```
sudo xattr -dr com.apple.quarantine .
```

It asks for your Mac's login password; nothing appears as you type it. (Mind the dot
at the end. macOS marks every downloaded file as unchecked, and this program is not
signed by Apple, so without this step macOS refuses to run it. The command clears the
mark for this folder only. Without `sudo` it answers with a stream of "permission
denied" messages.)

The `README.md` inside the download has step-by-step instructions for each system.

### LilyPond (optional)

Only needed to **read** LilyPond files: a LilyPond file is a program, and only
[LilyPond](https://lilypond.org) 2.24 or later can run it. Creating LilyPond files
needs nothing installed.

- **Windows:** LilyPond comes as a zip file. Unzip it to `C:\`, which gives a folder
  such as `C:\lilypond-2.24.4`, or name the folder `C:\lilypond`. The converter finds
  any folder on `C:\` whose name begins with "lilypond", as long as its `bin` folder
  is directly inside it - make sure the unzipping did not put a second lilypond folder
  inside the first. If it is not found, add the `bin` folder (for example
  `C:\lilypond\bin`) to your PATH.
- **macOS:** install it with Homebrew: `brew install lilypond`
- **Linux:** install it with your package manager.

## How to use ictus-convert

Open a command window in the folder where you unzipped it, and give it a music file
to convert:

```
convert  myscore.musicxml
```

(`./convert` on Mac or Linux.) This creates `ictus-myscore.mnx` and an image of it,
`ictus-myscore-mnx.png`. Give it an MNX or LilyPond file, and it creates MusicXML.

All the files it creates begin with `ictus-`, so your own files are never
overwritten.

### Options

**Choose what to create: `-xml`, `-mnx`, `-ly`.** Each asks for one format; give as
many as you like.

```
convert  myscore.musicxml  -ly
convert  myscore.ly  -xml  -mnx
```

**Creating MNX for MuseScore? Add `-musescore`.** MuseScore 4.7 reads an older
version of MNX and rejects a file that uses anything newer. This option creates an
MNX file that MuseScore 4.7 can open. If you forget it, the converter reminds you.

```
convert  myscore.musicxml  -musescore
```

**A cover page or pages of text? Add `-musiconly`.** MusicXML supports pages that have
no music, but MuseScore 4.7 and Dorico 6 do not support them. This option creates
MusicXML of the music pages only, and lists what was left out.

```
convert  myscore.ly  -musiconly
```

## Conversion reports

Converting between notation formats always loses something, because no two formats
describe music in quite the same way. For every conversion ictus-convert lists:

- **what the source said that it did not recognize** — the conversion program's own limits;
- **what your score held that the target format does not support** — the
  target *format's* limits.

Converting a song to MNX will usually report that the title, the composer's name
and all page layout were lost, because MNX does not support them. The music comes
through.

ictus-convert is built on the same importing and exporting code the Ictus editor
uses. It works by reading a file into a full music database and writing it out
again in the target format.

## Comments, problems, requests

Please open an [issue](../../issues). Conversion reports are especially useful:
paste the report, which names the version that produced it.
