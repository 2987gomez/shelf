<p align="center">
  <img src="Shelf/Assets.xcassets/AppIcon.appiconset/icon_256x256.png" width="128" height="128" alt="Shelf icon">
</p>

<h1 align="center">Shelf</h1>

<p align="center">
  <strong>Your macOS dock, powered up.</strong>
</p>

<p align="center">
  Multiple floating shelves for apps, links, and snippets — right where you need them.
</p>

<p align="center">
  <a href="#download">Download</a> · <a href="#features">Features</a> · <a href="#how-it-works">How It Works</a> · <a href="#building-from-source">Build</a>
</p>

---

## What is Shelf?

One dock isn't enough. Shelf gives you **multiple floating shelves** you can place anywhere on your screen — each one holding apps, web links, and text snippets. Like your macOS dock, but unlimited.

Built with **SwiftUI and AppKit** — no Electron, no web views. Pure macOS.

## Download

**[Download the latest .dmg from Releases](https://github.com/f/shelf/releases/latest)**

Or install with Homebrew:

```bash
brew install f/shelf/shelf
```

> Requires **macOS 15 Sequoia** or later. Works on Apple Silicon and Intel.

### First launch

Since Shelf is distributed outside the Mac App Store, macOS may block it on first open. Run this once in Terminal:

```bash
xattr -cr /Applications/Shelf.app
```

Then right-click the app → **Open**. After the first launch, macOS remembers your choice.

## Features

### Item Types

| Type | Description |
|---|---|
| **Apps** | Drag apps from Finder onto any shelf. Click to launch instantly. |
| **Links** | Add any URL — favicons are fetched automatically and masked to look like native macOS icons. |
| **Snippets** | Save text snippets. Click one and it instantly pastes into your active app. Code, emails, signatures — anything. |
| **Spacers** | Add empty space between items to organize your shelf. |
| **Separators** | Add visual dividers between groups of items. |

### Smart Drag & Drop

- **Drag apps** from Finder → adds to shelf
- **Drag text** from any website → creates a snippet
- **Drag a URL** → creates a link with auto-fetched favicon
- Shelf figures out what you meant — URLs become links, text becomes snippets

### Layout

- **Horizontal or Vertical** — each shelf can be either orientation
- **Place anywhere** — drag the background to move a shelf. It stays where you put it
- **Reorder items** — drag icons within a shelf to rearrange them, just like the native macOS dock
- **Multiple shelves** — create as many as you need for different workflows

### Native macOS Experience

- **Frosted glass** container with native vibrancy
- **Icon magnification** on hover
- **Tooltips** on hover showing item names
- **Context menus** — right-click for actions (Show in Finder, Copy URL, Remove, etc.)
- **Persistent** — shelves and positions are saved across restarts
- **Runs in menu bar** — no dock icon clutter

## How It Works

1. **Create a shelf** — Click the menu bar icon and choose "New Shelf". A floating shelf appears on your desktop.
2. **Add your stuff** — Drag apps from Finder, links from your browser, or text from anywhere. Right-click to add snippets, spacers, and separators.
3. **Use it** — Click to launch apps, open links, or paste snippets. Hover for magnification. Everything is always one click away.

## Building from Source

### Requirements

- macOS 15+
- Xcode 16+
- Swift 5.0+

### Build

```bash
git clone https://github.com/f/shelf.git
cd shelf
open Shelf.xcodeproj
```

Build and run with ⌘R in Xcode.

### Create a release build

```bash
chmod +x build.sh
./build.sh
```

This builds a universal binary (arm64 + x86_64) and creates `build/release/Shelf.dmg`.

### Project structure

```
Shelf/
├── Shelf.xcodeproj
├── build.sh                              # Universal binary build + DMG creation
├── docs/
│   └── index.html                        # Landing page
└── Shelf/
    ├── ShelfApp.swift                    # App entry point, menu bar setup
    ├── Models/
    │   ├── DockConfig.swift              # Shelf configuration (position, orientation, items)
    │   └── DockItem.swift                # Item model (app, link, snippet, spacer, separator)
    ├── Store/
    │   └── DockStore.swift               # Persistence layer (JSON in Application Support)
    ├── Views/
    │   ├── FloatingDockView.swift        # Main shelf UI with drag-and-drop reordering
    │   ├── DockItemView.swift            # Individual item rendering, magnification, context menus
    │   └── ManagerView.swift             # Shelf management UI
    ├── Windows/
    │   ├── DockWindowController.swift    # NSPanel management, external drop handling
    │   └── TooltipWindow.swift           # Custom tooltip overlay
    ├── Helpers/
    │   ├── DockHostingView.swift         # NSHostingView subclass for drag-and-drop + window dragging
    │   └── FaviconFetcher.swift          # Favicon download and caching
    └── Assets.xcassets/                  # App icon and colors
```

## License

MIT

---

<p align="center">
  Made by <a href="https://fka.dev">Fatih Kadir Akin</a>
</p>
