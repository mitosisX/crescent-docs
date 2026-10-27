# Your first app

A counter: a number and a button that adds one.

```lua
local ui = require("crescent.ui")                                      -- (1)!

local screen = ui.Screen { title = "Counter" }                          -- (2)!
local count = 0
local display = ui.Label("0"):setTextAlignment("center"):setTextSize(40) -- (3)!

local plus = ui.Button("+")
plus:setOnClick(function()                                              -- (4)!
  count = count + 1
  display:setText(count)
end)

screen:setContent(ui.Column():setMargins(20):addChild(display):addChild(plus)) -- (5)!
screen:show()                                                           -- (6)!
```

1. `crescent.ui` holds every widget. `crescent.sys` and `crescent.fs` hold system helpers and files.
2. A `Screen` is one page of your app. With a title it gets a top bar.
3. Widgets are made with their constructor, then set up with `setX` calls. Every setter returns
   the widget, so calls chain.
4. Events are `setOnX`. The function runs when it happens.
5. A `Column` stacks its children top to bottom. `setContent` puts it on the screen.
6. `show()` puts the screen up. Showing another screen later stacks it; Back returns.

## The pattern

Everything in Crescent follows the same few rules:

| You want to | You write |
|---|---|
| make a widget | `ui.Button("Save")` |
| change it | `button:setText("Saved")` |
| read it | `button:getText()` |
| react to the user | `button:setOnClick(function() ... end)` |
| put widgets together | `ui.Column():addChild(a):addChild(b)` |
| show a page | `screen:setContent(layout)` then `screen:show()` |

## Next

- Lay things out: [Layouts](../guide/layouts.md)
- Add more pages: [Screens](../guide/screens.md)
