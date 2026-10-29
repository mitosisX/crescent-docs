# Working in the background

Two different things go by that name, and Crescent keeps them apart:

- **A [`Task`](../reference/sys/Task.md)** does slow work while your app is open, off the screen's
  thread.
- **A [`Service`](../reference/sys/Service.md)** keeps working when nobody is looking at your app,
  behind a notification.

Both run one of your project's files, not a function. A Lua function belongs to the screen it was
written on and cannot be moved somewhere else, so the thing you hand over is a file name.

## A task

Put the work in its own file in `src/`:

```lua
-- src/counter.lua
local folder = ...                      -- what start() passed
local fs = require("crescent.fs").FileSystem
local total = 0
for _, name in ipairs(fs.listFolder(folder)) do
  total = total + fs.getFileSize(folder .. "/" .. name)
  task:send(name)                       -- tell the screen how it is going
end
return total                            -- the answer
```

and run it:

```lua
local sys = require("crescent.sys")

local counting = sys.Task("counter")
counting:setOnMessage(function(_, name) label:setText("reading " .. name) end)
counting:setOnDone(function(_, total) label:setText(total .. " bytes") end)
counting:start("photos")
```

The file gets its own Lua world. It can `require` your project's other files, read and write the
same folders, and fetch from the web; it cannot touch the screen, because it has none. Only text,
numbers, true/false and nil travel between the two sides, as arguments, as `task:send(value)`, and
as what the file returns.

`counting:stop()` asks it to wind up. A file that loops should say when it is willing to:

```lua
while not task:isStopping() do
  ...
end
```

Nothing can interrupt a file that never asks, so check it in any long loop.

## A service

A service runs `src/background.lua` with no screen at all, and keeps running when your app is not
on top. Android allows this only while a notification is showing, so one is:

```lua
-- src/background.lua
local net = require("crescent.net")
while not service:isStopping() do
  local answer = net.Http.get("https://example.com/price")
  service:notify("Watching the price", answer:getText())
  require("crescent.sys").System.sleep(60000)
end
```

```lua
sys.Service.start("Watching the price", "checking every minute")
...
sys.Service.stop()
```

`sys.Service.isRunning()` says whether it is up. Starting it again while it runs only changes the
words on the notification.

On Android 13 and later the user has to allow notifications. `start` asks the first time, and does
not wait for the answer: the work goes ahead either way, and the notice appears once it is allowed.

Keep a service for work that genuinely has to continue — a download, a watch on something, a long
upload. Android is strict with apps that work unseen, and will stop one that goes on for hours.

## Just a notification

To say one thing without a service, use [`Notify`](../reference/sys/Notify.md):

```lua
local id = sys.Notify.show("Done", "all 40 photos uploaded")
sys.Notify.hide(id)
```

## Which one do I want?

| You want to | Use |
|---|---|
| keep the screen smooth while something slow happens | `sys.Task` |
| do something every second while your app is open | [`sys.Timer`](../reference/sys/Timer.md) |
| wait for a moment, in order, inside a handler | `sys.System.sleep` |
| carry on when the user leaves your app | `sys.Service` |
| tell the user something when they are elsewhere | `sys.Notify` |
