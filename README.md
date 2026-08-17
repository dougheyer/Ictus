# Ictus

**Time-based music notation.**

Coming soon to your favorite website.

---

## Available now: the MusicXML / MNX converter

While the rest of Ictus is in development, one part of it is useful on its own: a
converter between **MusicXML** and **MNX**, in either direction, that tells you
what could not be carried across.

**[Download the latest release](../../releases/latest)** — unzip it, and if you
have Java installed, it runs:

```
convert  myscore.musicxml  myscore.mnx
convert  myscore.mnx       myscore.musicxml
```

No installer. No other software. Full instructions are in the `readme.txt` inside
the download.

### You need Java

Ictus-convert needs a Java virtual machine, version 8 or newer. To find out
whether you already have one, open a terminal or command prompt and type
`java -version` — with just one hyphen. If it prints a version number you are
ready. If not, install the latest OpenJDK:

- **Linux** — a Java VM is often already part of your distribution. If not,
  install OpenJDK from your package manager or app store.
- **macOS** — use the [Homebrew](https://brew.sh) package manager, then follow
  its instructions for installing OpenJDK. Installing a Java package directly is
  fussier than it looks about the combination of chip, macOS version and Java
  version; Homebrew works that out for you.
- **Windows** — download and run Microsoft's installer from
  [learn.microsoft.com/java/openjdk/download](https://learn.microsoft.com/en-us/java/openjdk/download).

### Why the reports matter

Converting between notation formats always loses something, because no two formats
describe music in quite the same way. Most converters lose it silently. This one
prints two lists every time:

- **what the source said that it did not read** — the program's own limits;
- **what your score held that the target format cannot state** — the *format's*
  limits.

Converting a song to MNX will usually report that the title, the composer's name
and all page layout were lost, because MNX 1.0-draft has nowhere to put them. The
music comes through.

The converter is built on the same importing and exporting code the Ictus editor
uses, and works by reading a file into a full music database and writing it out
again in the other format. That is what makes the reports possible — the program
can only tell you what was lost because it holds a model of what was there.

## Comments, problems, requests

Please open an [issue](../../issues). Conversion reports are especially useful:
paste the output, which names the version that produced it.

If you work on MNX itself, the reports are the point — run your own repertoire
through and see what the format cannot yet carry.
