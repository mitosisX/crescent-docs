# Screens and navigation

A [`Screen`](../reference/ui/Screen.md) is one page of your app.

```lua
local home = ui.Screen { title = "Notes" }
home:setContent(list)
home:show()
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
