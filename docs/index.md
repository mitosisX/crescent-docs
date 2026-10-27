---
hide:
  - navigation
---

# Crescent

**Write Android apps in Lua, on your phone.**

Crescent runs real Lua 5.5 on Android, with a small, friendly API for screens, buttons, lists and
everything in between. You write a script, tap Run, and it is an app. When it is ready, the Player
builds an APK you can install or share.

```lua
local ui = require("crescent.ui")

local screen = ui.Screen { title = "Counter" }
local count = 0
local display = ui.Label("0"):setTextAlignment("center"):setTextSize(40)

local plus = ui.Button("+")
plus:setOnClick(function()
  count = count + 1
  display:setText(count)
end)

screen:setContent(ui.Column():setMargins(20):addChild(display):addChild(plus))
screen:show()
```

That is the whole app.

<div class="grid cards" markdown>

-   :lucide-rocket: **[Get started](get-started/index.md)**

    Make your first project in the Player and run it.

-   :lucide-layout-dashboard: **[Guide](guide/layouts.md)**

    Layouts, screens, events, colours, icons, files and the Java bridge.

-   :lucide-book-open: **[Reference](reference/ui/index.md)**

    Every widget and function, with what each one does.

-   :lucide-smartphone: **[Samples](samples.md)**

    Full apps to read and copy, from a counter to Google's Reply.

</div>

## What makes it different

- **Phone first.** You write, run and build on the phone itself. Every name in the API is chosen for
  someone holding a phone: there is a `setOnLongPress`, not a right-click.
- **Real Lua.** Not a dialect: Lua 5.5, built with the NDK.
- **Waiting is easy.** `ui.Dialogs.confirm(...)` returns the answer. The screen keeps working while
  your script waits; no callbacks needed.
- **All of Android is there.** Anything the API does not cover is one `java.import` away.
