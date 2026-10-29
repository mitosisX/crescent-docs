# Screens and navigation

A [`Screen`](../reference/ui/Screen.md) is one page of your app.

```lua
local home = ui.Screen { title = "Notes" }
home:setContent(list)
home:show()
```

## Status bar colour

`setStatusBarColor` sets the colour of the bar at the very top of the phone, where the clock is. It
takes any [colour](styling.md#colours); the icons switch between light and dark to stay readable.

```lua
home:setStatusBarColor("#FBF7EF")
```

## Going to another screen

Showing a screen puts it on top of the current one. Back, or `close()`, returns.

```lua
local function openNote(name)
  local editor = ui.Screen { title = name }
  editor:setContent(ui.TextArea())
  editor:setOnClose(function() save(name) end)
  editor:show()
end
```

Every screen but the first gets a back arrow in its top bar. `setOnClose` runs when the screen goes
away, by Back or by `close()`.

A screen opened to find something out can hand the answer back. `close(result)` passes it, and the
screen underneath reads it in `setOnClose`:

```lua
local function pickColour()
  local picker = ui.Screen { title = "Pick a colour" }
  local list = ui.List():setItems({ "Red", "Green", "Blue" })
  list:setOnItemSelect(function(_, text) picker:close(text) end)
  picker:setContent(list)
  picker:setOnClose(function(_, chosen)
    if chosen then label:setText(chosen) end   -- nil when the user pressed Back
  end)
  picker:show()
end
```

Back hands back nothing, so treat `nil` as "the user changed their mind".

## The top bar

A screen with a title has a top bar. It can also show a second line and icons on the right:

```lua
local thread = ui.Screen { title = "Brunch this weekend?" }
thread:setSubtitle("4 messages")
thread:addAction("more_vert", "More options", function()
  ui.Snackbar.show("More options")
end)
```

The description is what TalkBack reads for the icon. Icon names are [Material icons](icons.md).

`setBarSize` gives the title its own room, the way Settings and Photos do: `"small"` is the default,
`"medium"` and `"large"` are taller.

```lua
thread:setBarSize("large")
```

## A side menu

`setDrawer` puts a panel behind the left edge. The top bar's menu icon, or a drag from the edge,
slides it out:

```lua
local menu = ui.Column():setMargins(16)
menu:addChild(ui.Label("Flowers"):setTextRole("titleMedium"))
menu:addChild(ui.Button("All"):setVariant("text"):setOnClick(function() home:closeDrawer() end))
home:setDrawer(menu)
```

A screen with a drawer shows the menu icon in place of the back arrow, so drawers belong on your
first screen. `openDrawer()` and `closeDrawer()` work from code.

## Sheets

A [`Sheet`](../reference/ui/Sheet.md) slides up from the bottom over the screen: a filter, a share
list, the details of the thing the user just tapped. It is the only widget besides a screen with
`show` and `close`, because it is somewhere the user goes:

```lua
local filters = ui.Sheet()
filters:setContent(ui.Column():setSpacing(12)
  :addChild(ui.Label("Sort by"):setTextRole("titleMedium"))
  :addChild(ui.SegmentedButton():addItem("Newest"):addItem("Cheapest")))
filters:setOnClose(function() applyFilters() end)

sortButton:setOnClick(function() filters:show() end)
```

The user drags it down or taps outside to dismiss it; `close()` does the same from code.
`setPeek(240)` sets how much shows before they drag it up, and `setExpanded(true)` opens it all the
way.

## A bottom bar

For apps with a few top-level places, use a [`NavigationBar`](../reference/ui/NavigationBar.md). Each
item has an icon, a label and the widget it shows:

```lua
local nav = ui.NavigationBar()
nav:addItem("inbox", "Inbox", inboxPage)
nav:addItem("article", "Articles", articlesPage)
nav:addItem("group", "Groups", groupsPage)
nav:setOnSelect(function(_, index) print("now on item", index) end)
screen:setContent(nav)
```

It holds up to five items. For tabs along the top, use [`Tabs`](../reference/ui/Tabs.md).

## The floating button

A screen's main action can float over its content, bottom right:

```lua
local compose = ui.Fab("Compose"):setIcon("edit")
compose:setOnClick(function() newMessage() end)
screen:setFab(compose)
```

`compose:collapse()` shrinks it to just the icon; `expand()` brings the text back. A common pattern
is to collapse it while the user scrolls down a list:

```lua
scroller:setOnScroll(function(_, dx, dy)
  if dy > 0 then compose:collapse() elseif dy < 0 then compose:expand() end
end)
```
