# ubuntu

Your Solid pod as an **Ubuntu (GNOME / Yaru) desktop** — the aubergine wallpaper,
the dark top bar, the left dock, rounded Adwaita windows, Ubuntu orange.

It's the **same desktop engine** as [`chrome`](https://github.com/solid-apps/chrome)
and [`win98`](https://github.com/solid-apps/win98) — a real window manager, apps
as **panes** (ES modules), an app launcher, real-time via WebSocket Notifications,
and prefs/installed-apps synced to your pod. `ubuntu` is a third **skin** over those
shared primitives, so panes are interchangeable across all three.

## What's Ubuntu about it

- **GNOME top bar** — Activities (opens the app grid), the clock, quick settings,
  and the sign-in pill.
- **Left dock** — running and pinned apps as icons, with the Yaru orange running
  indicator; the *Show Applications* grid sits at the bottom.
- **Aubergine desktop** — the signature Ubuntu purple gradient.
- **Adwaita windows** — rounded corners, a light header bar, circular window
  controls (close turns red), snap-to-edge tiling, workspaces.
- **Real Ubuntu typography** — the Ubuntu font family (UFL-licensed), self-hosted.

## How the reskin works

`ubuntu` reuses chrome's `src/` engine **verbatim** — only three things change:

1. `style.css` — the Yaru theme. It redefines `:root` and **aliases** the engine's
   variables (`--accent` → Ubuntu orange, etc.), so every module, the launcher, and
   quick-settings inherit the look; then it restyles the shell as a top bar + dock.
2. `index.html` — the GNOME shell markup, keeping the same element ids the engine
   binds to (`#tray-launcher`, `#shelf-running`, `#tray-clock`, …).
3. `src/windows.js` — two constants + the workspace rect, so windows tile below the
   top bar and beside the dock.

Everything else (`app.js`, `panes.js`, `registry.js`, `launcher.js`, `pod.js`,
auth, notifications, builtins) is byte-identical to chrome.

## Run

Open `index.html`, or install via the **store** to `/public/apps/ubuntu/`. Sign in
with the pill (Solid OIDC or Nostr) to launch your pod apps.

AGPL-3.0-only.
