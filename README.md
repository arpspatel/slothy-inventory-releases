# Slothy Inventory App — downloads

Windows desktop app for tracking a precious-metals inventory: buys and sells, trades in progress, shipping and P/L.

© 2026 Neebu LLC. All rights reserved. This repository only hosts the installer; the source code is not public.

## Download

Get **`SlothyInventorySetup-<version>.exe`** from the [latest release](../../releases/latest).

## Install

1. Run the installer. No admin rights are needed: it installs for your Windows user only, to
   `%LOCALAPPDATA%\Programs\Slothy Inventory App`, with a Start menu entry and an optional desktop shortcut.
2. The installer isn't code-signed yet, so Windows SmartScreen may say *"Windows protected your PC"*. Click
   **More info → Run anyway**.

Windows 10/11, 64-bit.

## Your data

The app keeps everything in `Documents\InventoryApp\inventory.db` on your own PC. Nothing is uploaded.

- **Updating:** run a newer installer over the old one. It upgrades in place and keeps your data.
- **Uninstalling:** Windows Settings → Apps → *Slothy Inventory App*. Your database in Documents is left alone.
- If the app is open, setup and uninstall ask you to close it first.
