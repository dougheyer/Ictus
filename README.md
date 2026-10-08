# Ictus

**Time-based music notation.** Coming soon to your favorite website.

### ⬇ [Download ictus-convert](../../releases/latest) — MusicXML, LilyPond and MNX, any of them in, any of them out

> The **Code** button above gives you this page and the licence, not the program.
> The converter is a release download, at the link above or under **Releases** in
> the sidebar.

---

## Available now: the converter

While the rest of Ictus is in development, one part of it is useful on its own: a
converter between **MusicXML**, **LilyPond** and **MNX**, any of the three in and any
of the three out. It creates an image of the result, and tells you what could not
be carried across.

### Download the one for your system

| your system | download |
| --- | --- |
| Windows | `ictus-convert-0.3-windows-x64.zip` |
| Mac with Apple silicon (M1, M2, ...) | `ictus-convert-0.3-macos-arm64.zip` |
| Mac with an Intel processor | `ictus-convert-0.3-macos-x64.zip` |
| Linux | `ictus-convert-0.3-linux-x64.zip` |
| anything else, with Java 8 or newer installed | `ictus-convert-0.3.zip` |

**Nothing to install.** Each download carries its own Java. Unzip it, open a command
window in the folder, and give it a music file:

```
convert  myscore.musicxml
```

(`./convert` on Mac and Linux.) That creates `ictus-myscore.mnx`, the same music as
MNX, and `ictus-myscore-mnx.png`, an image of it. Give it an MNX or LilyPond file
and you get MusicXML back. Everything it creates begins with `ictus-`, so your own
files are never overwritten.

The `README.md` inside the download has step-by-step instructions for each system,
including the one-time step macOS needs before it will run a program that Apple has
not signed.

**MNX for MuseScore? Add `-musescore`.** MuseScore 4.7 reads an older version of
MNX and refuses a file that uses anything newer, hairpins included. This creates MNX
it can open, and if you forget it, the converter reminds you:

```
convert  myscore.musicxml  -musescore
```

**Reading LilyPond files** needs [LilyPond](https://lilypond.org) 2.24 or later,
because a LilyPond file is a program and only LilyPond can run it. On Windows
LilyPond comes as a folder to unzip, and `C:\lilypond` is found automatically; on
macOS, `brew install lilypond`; on Linux, your package manager. The converter has
been run over the whole [Mutopia](https://www.mutopiaproject.org) archive.

### Why the reports matter

Converting between notation formats always loses something, because no two formats
describe music in quite the same way. Most converters lose it silently. This one
prints, every time:

- **what the source said that it did not recognize** — the program's own limits;
- **what your score held that the target format does not support** — the
  *format's* limits.

Converting a song to MNX will usually report that the title, the composer's name
and all page layout were lost, because MNX does not support them. The music comes
through.

The converter is built on the same importing and exporting code the Ictus editor
uses, and works by reading a file into a full music database and writing it out
again in the other format. That is what makes the reports possible — the program
can only tell you what was lost because it holds a model of what was there.

## Comments, problems, requests

Please open an [issue](../../issues). Conversion reports are especially useful:
paste the output, which names the version that produced it.

If you work on MNX itself, the reports are the point — run your own repertoire
through and see what the format cannot yet carry.
