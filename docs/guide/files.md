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

## Standard folders

```lua
local sys = require("crescent.sys")
sys.System.getStandardPath("cache")      -- for files the phone may clear
sys.System.getStandardPath("external")   -- visible over USB
```

## A notes app

The **Notes** sample keeps one text file per note: see [Samples](../samples.md).
