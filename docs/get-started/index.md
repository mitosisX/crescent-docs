# Get started

Crescent apps are written in the **Crescent Player**, an Android app that holds your projects,
edits them, runs them and builds them into APKs.

## Your first project

1. Open the Player. A fresh install already has a **Hello World** project on the **Projects** tab.
2. Tap the project to open it in the editor. The script is `src/main.lua`.
3. Tap **Run**. Your script runs as an app; Back returns to the editor.

To start from scratch, tap **New project** on the Projects tab and give it a name.

## What is in a project

```
My app/
├── src/
│   └── main.lua      the script that runs first
├── assets/           pictures, fonts and other files your app ships with
└── icon.png          the app's icon
```

`main.lua` can `require` other files in `src/`: `require("inbox")` loads `src/inbox.lua`.

Files in `assets/` are reached with paths that start with `assets/`:

```lua
ui.Image("assets/images/logo.png")
```

## Samples

The **Samples** tab has finished apps you can open, read and run. They open read only; copy one
into your projects to change it. See [Samples](../samples.md).

## Build an APK

When your app is ready, open the project's menu and choose **Build**. The Player makes a signed APK
(or an AAB for Google Play) on the phone itself. No computer needed.

## Next

Walk through [your first app](first-app.md), line by line.
