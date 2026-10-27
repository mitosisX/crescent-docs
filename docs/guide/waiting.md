# Waiting

In Crescent, your script can simply wait, for the user, for time to pass, or for a dialog, and the
screen keeps working while it does. There are no callbacks to chain.

## Dialogs

```lua
ui.Dialogs.alert("Saved", "Your note is safe.")              -- waits for OK

if ui.Dialogs.confirm("Delete", "Delete this note?") then    -- true for Yes
  deleteNote()
end

local name = ui.Dialogs.prompt("Rename", "New name", old)    -- nil if cancelled
if name then rename(old, name) end

ui.Dialogs.toast("Copied")                                   -- does not wait
```

`pickDate` shows a calendar and waits. It returns the day as `"YYYY-MM-DD"`, or `nil` if the user
cancelled. Both arguments are optional: a title, and the date to start on (today by default).

```lua
local day = ui.Dialogs.pickDate("Delivery day", "2026-12-24")
if day then order:setDate(day) end
```

For a message with an action that does not block, use a snackbar:

```lua
ui.Snackbar.show("Deleted", "Undo", function() restore() end)
```

## Time

```lua
local sys = require("crescent.sys")

sys.System.sleep(500)                       -- wait half a second

sys.Timer.singleShot(2000, function()       -- run something once, later
  ui.Snackbar.show("Two seconds passed")
end)

local clock = sys.Timer(1000)               -- run something every second
clock:setOnTick(function() tick() end)
clock:start()
```

## Where waiting works

Waiting works in your script's main body and inside event handlers. Each event that arrives
while nothing else is running starts fresh, so one handler waiting does not block another.
