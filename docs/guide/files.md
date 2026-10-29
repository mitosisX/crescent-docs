# Files

[`crescent.fs`](../reference/fs/FileSystem.md) reads and writes files. Relative paths are inside
your app's own storage, which nobody else can see.

```lua
local F = require("crescent.fs").FileSystem

F.writeFile("notes/shopping.txt", "milk\neggs")   -- creates the folder too
local text = F.readFile("notes/shopping.txt")
F.appendFile("notes/shopping.txt", "\nbread")

for _, name in ipairs(F.listFolder("notes")) do
  print(name)
end

if F.exists("notes/old.txt") then F.deleteFile("notes/old.txt") end
```

## Your app's assets

Files you put in the project's `assets/` folder ship inside the app. Read them with an `assets/`
path:

```lua
local data = F.readFile("assets/words.txt")
```

Widgets that load files take the same paths: `ui.Image("assets/logo.png")`,
`label:setFont("assets/fonts/MyFont.ttf")`.

## Copying, moving, deleting

```lua
F.copyFile("notes/shopping.txt", "notes/backup.txt")
F.copyFolder("notes", "notes-backup")     -- and everything in it
F.moveFile("notes/old.txt", "archive/old.txt")
F.deleteFolder("notes-backup")            -- and everything in it
```

## Zips

```lua
F.zipFolder("notes", "backups/notes.zip")   -- one file works too
F.unzipFile("backups/notes.zip", "restored")
```

Paths inside the zip are relative to the folder you packed, so unpacking somewhere else lays it
out the same way.

## What a file is, and whether it changed

`getFileType` reads the first bytes of a file rather than trusting its name, which is how you tell
a real picture from something that was merely called `.png`:

```lua
F.getFileType("downloads/thing")   -- "png", "jpg", "gif", "pdf", "zip", "mp4", "xml", "unknown"...
```

`getFileHash` is a file's fingerprint. Two files with the same hash hold the same bytes, which is
how you check a download arrived whole, or notice that a file changed:

```lua
F.getFileHash("downloads/report.pdf")          -- sha256
F.getFileHash("downloads/report.pdf", "md5")   -- or "sha1"
```

## Standard folders

```lua
local sys = require("crescent.sys")
sys.System.getStandardPath("cache")      -- for files the phone may clear
sys.System.getStandardPath("external")   -- visible over USB
```

## A notes app

The **Notes** sample keeps one text file per note: see [Samples](../samples.md).
