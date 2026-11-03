<img src="icon.png" width="96" alt="" align="left">

# Slothy Inventory Manager

Windows desktop app for tracking a precious-metals inventory: buys and sells, trades in progress, shipping and P/L.

<br clear="left">

© 2026 Neebu LLC. All rights reserved. This repository only hosts the installer; the source code is not public.

**New here?** Read the [user guide](GUIDE.md) for how to use each page of the app.

## Download

Get **`SlothyInventorySetup-<version>.exe`** from the [latest release](../../releases/latest).

## Install

1. Run the installer. The installer isn't code-signed yet, so Windows SmartScreen may say *"Windows protected your
   PC"*. Click **More info → Run anyway**.
2. Choose **Install for me only** (the default, no admin rights needed) or **Install for all users** (asks for admin
   permission, installs to Program Files). Either way you get a Start menu entry and an optional desktop shortcut.
   Each Windows user keeps their own data.

Windows 10/11, 64-bit.

## Updates

The app keeps itself up to date. It checks for a new version at most once a day (or anytime from
**Help → Check for updates…**), shows what's new and asks before doing anything. **Update now** backs up your data,
installs the new version and reopens the app. Every update is signed, and the app installs only updates signed by
the publisher.

Version numbers are the build date and time: `YY.MM.DD.HHMM`.

If you have version 26.11.03.1100 or earlier (including 1.0.0, then called *Slothy Inventory App*), install the latest
release by hand once. It updates itself from then on.

## Your data

The app keeps everything in `Documents\InventoryApp\inventory.db` on your own PC. Nothing is uploaded.

- **Uninstalling:** Windows Settings → Apps → *Slothy Inventory Manager*. Your database in Documents is left alone.
- If the app is open, setup and uninstall ask you to close it first.
