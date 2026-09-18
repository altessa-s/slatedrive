# Slate Drive

[![Latest release](https://img.shields.io/github/v/release/altessa-s/slatedrive?include_prereleases&label=release)](https://github.com/altessa-s/slatedrive/releases)
[![macOS 15+](https://img.shields.io/badge/macOS-15%2B-black?logo=apple)](#requirements)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](#source-code-and-license)

Slate Drive shows your reMarkable cloud library in Finder, as a volume under *Locations*. Notebooks open as PDFs rendered on your Mac. The folders match what you see on the tablet. You can send files back without cables or manual exports.

The app is free. There are no ads and no sign-up. The only account involved is your reMarkable one.

**[Download the latest release](https://github.com/altessa-s/slatedrive/releases/latest)** · free · macOS 15+ · notarised DMG

> [!NOTE]
> Slate Drive is MIT-licensed. Right now this repository has builds only. The source code will be published here by the end of 2026. See [Source code and license](#source-code-and-license).

## Contents

- [Getting started](#getting-started)
- [Features](#features)
- [Privacy](#privacy)
- [Updates](#updates)
- [Reporting issues](#reporting-issues)
- [Source code and license](#source-code-and-license)

## Getting started

### Requirements

- macOS 15 or later
- A reMarkable account with a paired tablet and an active Connect subscription

### Install

1. Download the DMG from [Releases](https://github.com/altessa-s/slatedrive/releases).
2. Drag Slate Drive into `Applications` and open it.
3. The first launch starts a short tour. It connects your account using the one-time code from your reMarkable account website. It also offers launch at login and notifications, and explains why you might want each one.

You can reopen the tour later with **Show the tour** in the About window.

> [!IMPORTANT]
> Keep one copy of the app on your Mac. The Finder volume comes from a File Provider extension, and macOS ties it to one specific app bundle. A second copy lying around, say in `Downloads` or on a mounted DMG, can take the volume away from the copy you use.

## Features

### Library in Finder

The library appears as **Slate Drive** under *Locations*, with the same folders and documents as on the tablet.

Notebooks and annotated documents open as PDFs rendered locally. PDF and EPUB files are passed through as they are. Documents download when you open them, and the folder tree syncs in the background. Favorites and the tablet's trash show up in the volume too.

The app lives in the menu bar. It keeps you signed in, shows sync status, and can start at login so the drive is always there.

### Read-only or editing

The volume starts read-only. You can browse and open files, but nothing in the library changes.

Turn on editing and Finder works like a normal disk. You can create folders, upload files, rename, move, and put things in the tablet's trash. Finder only offers operations the app fully supports.

### Send to the tablet

There are four ways to send, and none of them needs the app window:

- **Share menu.** "Save to Slate Drive" appears in every Mac app that has a Share menu: Preview, Mail, Safari, Chrome, your editor.
- **Drag and drop.** Drop files onto the Dock icon or the menu-bar icon. Nothing opens and nothing asks for confirmation.
- **Shelf.** A panel at the edge of the screen where you can collect files during the day and then send them all with one click. Each file shows what will happen to it: *keep as is*, *→ PDF* or *→ Notebook*.
- **⌘P.** Any app that can print can send to the tablet (see [Print to the tablet](#print-to-the-tablet)).

**What happens to a file.** PDF and EPUB go through unchanged. Word, Pages, HTML, Markdown, RTF, plain text and images (JPG, PNG, HEIC) become either a PDF or a notebook. A PDF is laid out for your tablet's screen: reMarkable 2, Paper Pure, Paper Pro or Paper Pro Move. A notebook is the tablet's own `.rm` format, so you can keep editing it on the device. A typed notebook can't hold tables or images; a file with those goes as a PDF, and the panel tells you so.

**Where it lands.** Files go to a destination folder you set once. Until you set one, the app creates an *Inbox* folder at the top of the library. You can also have it ask for a folder on every send. Tags from the Tablet settings are added to everything you send.

#### Web articles, cleaned up on your Mac

Share a page from Safari, Chrome, Arc or Firefox and it arrives as a PDF laid out for your tablet. You don't need a browser extension, because the Share menu is part of macOS.

Before the PDF is made, the app keeps only the article: text, headings and images. Menus, ads, cookie banners, subscription pop-ups and comments are left out. The cleanup is done by [Defuddle](https://github.com/kepano/defuddle) (the default) or [Readability](https://github.com/mozilla/readability). Both are built in and neither goes online.

You have a few other options:
- clean up with an AI model on your own key (off until you turn it on)
- turn cleanup off and keep the whole page
- drop the page's images

Articles can have their own tag list. If you leave it empty, they get the general tags.

#### Handwritten notebooks

Text sent as a notebook can arrive typed, or written out in pen strokes as if by hand. Handwriting uses the same settings a page has on the tablet itself:

| Setting | Options |
|---|---|
| Tool | Ballpoint, fineliner, pencil, mechanical pencil |
| Thickness | Thin, regular, thick (each tool has its own values, as on the tablet) |
| Smoothing | Slight, medium, full |
| Paper | Blank, lines, grid, dots, margin, US College, Legal |
| Line spacing | Wide, regular, tight |

Each tool leaves its own mark. Ballpoint and pencil vary in pressure along a stroke, while the fineliner holds a steady line. *Slight* smoothing keeps the tremor of a real hand; *full* comes out almost ruler-straight. The template travels with the note, so on the device it looks like a page you started there. On ruled paper the writing sits on the rules, so the spacing setting only matters on a blank page.

### Tags

Off by default; turn it on in the Drive settings. Tablet tags then show up as Finder tags. In editing mode, a tag you change in Finder is written back to the tablet. Colours stay on the Mac because the tablet doesn't have them.

### Keep offline

Pin a folder or a document and Slate Drive keeps a copy on the Mac, so it opens without a network. Unpin it when you no longer need the copy.

### Local backup

The optional backup keeps a continuous copy of the library in a folder you choose. It holds readable PDFs of notebooks and annotated documents, with the tablet's own files next to them. After the first full pass, only changed documents are updated. That works well with Time Machine or any tool that watches a folder.

### Search and recognition

Spotlight can index document text, so you can find notes by what's in them, not just by title. Handwriting and printed pages each get their own default engine. Engines you switch off disappear from the menus.

| Engine | Where it runs |
|---|---|
| Apple Vision | On this Mac |
| Tesseract | On this Mac. Uses language data from a folder you choose, and stays off until you choose one |
| Google Cloud Vision | Cloud, with your API key |
| Yandex Vision OCR | Cloud, with a Yandex Cloud API key. Handwriting in Russian and English, print in about four dozen languages |
| AI connection | Apple Intelligence on this Mac, or Anthropic, OpenAI, Gemini, DeepSeek or Yandex AI Studio |

Cloud engines stay off until you switch them on, and switching one on asks first: page images will leave this Mac. The same switch turns it off.

Which engine reads best depends on your language, your hand and the page. I don't quote accuracy numbers, because they'd be measured on somebody else's handwriting. Try two engines on a note you know well and compare.

Each page is only read once:
- The text that was read is stored with the document. Spotlight, AI Studio, integrations and MCP all reuse it.
- A page is read again only if the document changes or you pick a different engine.
- PDFs that already have a text layer use that layer, and blank notebook pages are skipped.
- If a model refuses a document, that document is flagged and the rest of the pass carries on. You can then give it to a fallback model or read it locally.

### AI Studio

AI Studio is the window where pages turn into transcripts, summaries and exports.

**Actions** work on the documents you select. An action can read the pages, run a model with a prompt, and write a file; the first two steps are optional. The app ships with three actions: Transcribe, Summary and Highlights. Export to Word and Export to Markdown are added as your own actions, so you can edit or delete them.

Output formats:
- PDF, searchable PDF, notebook
- Markdown, Word, RTF, plain text
- the original document, or page images
- highlighted passages. These include highlights the tablet copied from a PDF's text, and marker strokes drawn over handwriting.

**Prompts** are yours to write: one for lectures, one for meetings, one for papers. Each prompt has a name, a description, tags, and a list of the AI connections it may use. Two prompts come with the app, and you can duplicate them as a starting point. Actions refer to a prompt instead of carrying their own wording.

**Rules** attach an action to a library folder, with a condition and a monthly budget in US dollars. When a rule hits its budget, it pauses until the first of the next month. Rules are the only thing that runs in the background.

**Journal** logs every run with its tokens and cost. When an engine read the page as an image, the entry also shows how confident it was.

**Processors** (OCR engines, Compose, writers) are configured in the same window. A processor you switch off isn't offered in any action.

You can also run actions, or send to an integration, straight from Finder. Progress stays on screen until you close it.

### Integrations

Results can go to note-taking apps. Export is one-way; nothing syncs back.

| Integration | What it creates |
|---|---|
| Obsidian | Markdown and attachments in a vault on this Mac |
| Logseq | Files in a graph folder, or entries through Logseq's local API for a database graph |
| Bear | New notes, via Bear's URL scheme |
| Apple Notes | Notes in a folder of the default account |
| Zotero | Items and attachments, through Zotero on this Mac |
| DEVONthink | Records in the database and group you choose |
| Readwise | Book highlights, on Readwise's servers |
| Readwise Reader | Saved documents |

- **Setup:** each integration has its own setup form, and secrets are stored in the Keychain.
- **Naming:** when an integration creates its own folder or namespace, it's called "reMarkable (Slate Drive)". You can rename it on the form.
- **Tags:** notes that support tags get `reMarkable` first, then whatever tags you add on the form.
- **Sending again:** depending on the app and your settings, a second send either updates the note or creates a new one.

### MCP server

Slate Drive can run a local Model Context Protocol server. It's off by default, listens on localhost only, and requires a Bearer token kept in the Keychain.

Clients like Claude Desktop or Claude Code can:
- list the library
- read document text
- search recognised content
- get a short-lived link to a file
- move items to the trash, after you confirm

Nothing is exposed to the internet, so cloud-hosted connectors can't reach the server.

### Print to the tablet

The virtual printer is optional and off by default. Add it in *Printers & Scanners*, and any Mac app can print into a folder on the tablet.

- By default only this Mac sees the printer. Share it on the local network and iPhones and iPads in the house can print to the tablet too, as long as the Mac is awake.
- It accepts PDF and Apple Raster.
- Paper sizes include tablet sizes, A4 and Letter.
- A finished print is sent straight away, and you get a notification.

### Notifications

Every kind of banner has its own switch on the **Notifications** page in Settings. They all start on:
- a send that arrived, or one that didn't
- a change Finder couldn't make
- sync problems
- AI Studio runs
- a rule that hit its budget
- a send to a note app

### Languages

The interface is available in American English, German, Spanish, French, Dutch and Russian.

## Privacy

There are no analytics and no telemetry. The app runs in the App Sandbox. Tokens and API keys are stored in the Keychain and never in plain settings files or logs.

Page images leave your Mac in four cases:
- you turned on a cloud OCR engine
- you ran an AI action
- you set up a rule
- you send to Readwise or Readwise Reader

Each of these says so at the place where you switch it on. Shared web articles are cleaned up locally by Defuddle or Readability, and they only go out if you turn on AI cleanup.

- [Privacy Policy](https://slatedrive.app/privacy)
- [Terms of Use](https://slatedrive.app/terms)

## Updates

Updates come from [GitHub Releases](https://github.com/altessa-s/slatedrive/releases). You can check by hand, or let the app check on its own and download updates in the background.

## Reporting issues

[Open an issue](https://github.com/altessa-s/slatedrive/issues/new/choose) and include:

- the version line from the About window (it has the commit the build came from)
- your macOS version
- what you did and what happened

## Source code and license

Slate Drive is released under the [MIT License](LICENSE).

The source isn't here yet. I plan to publish it in this repository by the end of 2026. Until then, the repository hosts releases, the issue tracker and this README.

---

<sub>Defuddle, Readability and Tesseract are third-party open-source components and run on your Mac.</sub>

<sub>Slate Drive is independent. It is not affiliated with, endorsed, or sponsored by reMarkable AS. reMarkable is a trademark of reMarkable AS.</sub>
