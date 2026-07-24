[README.md](https://github.com/user-attachments/files/30288600/README.md)
# InvMgr — Inventory Manager

A top-down inventory manager for keeping track of boxes in a 2D simulation of your space, be it a garage, attic, or a storage-unit-because-you-moved-years-ago-and-still-don't-have-enough-space-for-your-stuff-and-you-have-no-idea-where-anything-is (couldn't be me). Of course, you can organize non-boxes in the same way, as it's mainly a representation of what's where. You can create items to-scale in your to-scale room and stack them based on your real space. You can plan them in the list before deciding where they go, as well. Finally, you can view the space in 3D to check how well it matches up, flying around the space freely.

Single self-contained HTML file. No build step, no server, no account, no
network calls at runtime. Works fully offline, installable as a PWA, and
available as a compiled Android APK. (technically, PWA and APK need internet to get the latest `index.html` from this repo)

<p align="center">
  <img src="https://raw.githubusercontent.com/ModCritic/AsteroidRawFileEmbeds/main/desktopinvmgr.webp" height="364">
  <img src="https://raw.githubusercontent.com/ModCritic/AsteroidRawFileEmbeds/main/mobileinvmgr.gif" height="364">
</p>

## Features

### Room & display
- Enter your room's width, length, and height; the 2D view is a true-to-scale top-down layout of the room.
- Fit-to-screen toggle, and a Units toggle for Imperial/Metric.

### Items
- Add items with an optional name/description, actual width, length, and height, and an
  optional ID (not shown in tooltips or the item list, but included in
  *exported* item list for SKUs, barcodes, asset tags, or just plainly saying it's a box, rather than a bin).
- Drag items to reposition them.
- Items automatically settle onto whatever's beneath their footprint, so dragging an item over another stacks its remembered height above the floor, or you can disable gravity and have active collision with other items in the same vertical space so you can reposition everything more precisely with **Layer  Collision**.
- **Planned items**: stage an item in the list before committing it to a real spot in
  the room. Drag out from the list into the room to commit.
- **Presets**: save named width/length/height combinations for items you add
  often (like standard U-Haul boxes), and apply them to the Add Item dialog in one tap.
- Double-click (or double-tap) any item, in the room or in the list, to edit
  it, including a one-tap 90 degree rotation in case you input it the wrong way around.

### Layer slider
Peel back the room by height to see what's stacked underneath, like viewing a cross-section from above.

### Item list
Full searchable list of everything in the room with partial-match search, by name, or by exact
dimension (type a width/length/height value, e.g: W15, and it filters to items matching
that measurement). Export the entire list as a plain-text file, one line per
item with its name, full dimension readout, and ID.

### Save & recovery
- Save/load your whole room as a portable JSON file.
- Automatic session recovery: if the tab reloads or crashes unexpectedly,
  you'll be offered a one-click restore of your last state, in most cases.

### 3D walkthrough
See a full 3D view of the room from directly overhead, descending into
a first-person view you can fly around with.

- **Desktop:** WASD to move, mouse-look, Shift to move faster, Space/C for
  up/down.
- **Touch:** on-screen joystick to move, swipe to look, two-finger drag to
  pan (physically move camera) horizontally and vertically.
- Hover or tap any item in 3D to see the same tooltip you'd get in the 2D
  view.

### Undo
Unlimited undo for moves, deletes, and height changes.

## Getting started

Open `index.html` directly in any modern browser — no installation required.
For an app-like experience, install it as a PWA from your browser's install
prompt, or grab the compiled Android APK from this repo's
[Releases](https://github.com/ModCritic/InvMgr/releases/tag/v1.1.0) page (V1.1.0 release has the last APK since that doesn't need to change for updates to the HTML file).

## How it's built

Everything — markup, styling, and logic — lives in a single `index.html`.
No frameworks, no bundler, no dependencies fetched at runtime. The 3D view is
built on CSS 3D transforms rather than WebGL or a game engine.

## Status

This HTML/JS build is the finished, feature-complete state of the project's
original architecture. A ground-up native rewrite (Java, targeting desktop
and Android with built-in offline speech-to-text entry for quicker organizing) is in
progress in a separate repository (unless it turns out unfeasible).

I'll still do bug-fixes if people submit issues and I'll work with you to improve it how it is if you want to contribute.

## License

Original code is released under the 0BSD license (see `LICENSE`). The
Android APK — generated via PWABuilder/Bubblewrap — bundles Apache-2.0
licensed components; see `THIRD-PARTY-LICENSES.md` for full attribution.
