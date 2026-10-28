# Events

Events are methods named `setOnX`, where X is what the user did. You give them a function:

```lua
button:setOnClick(function(button)
  button:setText("Thanks!")
end)
```

The function always gets the widget first, then anything the event knows. A switch tells you
whether it is now on; a list tells you which item was tapped:

```lua
wifi:setOnCheck(function(_, on) print("wifi is", on) end)
list:setOnItemSelect(function(_, text, index) print(index, text) end)
```

Setting an event again replaces the old function.

## Common events

| Event | When |
|---|---|
| `setOnClick` | tapped (every widget has it, and shows a ripple) |
| `setOnLongPress` | pressed and held (every widget has it) |
| `setOnTextChange` | text in a field changed |
| `setOnSubmit` | the keyboard's action key in a one-line field |
| `setOnCheck` | a checkbox, switch or radio button changed |
| `setOnSelect` | a tab, bar item or radio choice was picked |
| `setOnItemSelect` / `setOnItemLongPress` | an item in a list or dropdown |
| `setOnItemSwipe` | an item in a list was swiped away |
| `setOnMenuSelect` | something was picked from a widget's menu |
| `setOnRefresh` | a pull-to-refresh was dragged down |
| `setOnValueChange` | a slider or number picker moved |
| `setOnResize` | the widget's size changed |
| `setOnScroll` | a scroller moved |
| `setOnClose` | a screen went away |

Every widget can be tapped, not only buttons: a `Label`, an `Image`, a `Card` or a whole `Row` can take
`setOnClick`. Widgets that handle touch themselves, such as text fields, sliders and lists, keep that
behaviour, and for them `setOnClick` fires only when the tap lands outside the part they handle.

Each widget's page in the [reference](../reference/ui/index.md) lists its events.

## A menu on a long press

`setMenu` gives any widget a menu that opens when the user presses and holds it:

```lua
note:setMenu({ "Rename", "Duplicate", "Delete" })
note:setOnMenuSelect(function(_, item, index)
  if item == "Delete" then removeNote() end
end)
```

The menu takes the long press over, so a widget with a menu does not also report `setOnLongPress`.
`openMenu()` opens it from code, for an overflow icon that should show the same list.

## Swiping an item away

A list item can be swiped off, the way a mail app deletes a message. The item goes first, then the
event tells you what went, so you can offer an undo:

```lua
list:setOnItemSwipe(function(_, text, index)
  ui.Snackbar.show(text .. " deleted", "Undo", function()
    list:insertItemAt(index, text)
  end)
end)
```

## Errors in handlers

If a handler raises an error, the app does not crash: the error is reported (in the Player, on the
run screen) and the app carries on.

## Waiting inside a handler

Handlers can wait. This works, and the screen stays responsive while the dialog is up:

```lua
delete:setOnClick(function()
  if ui.Dialogs.confirm("Delete", "Delete this note?") then
    removeNote()
  end
end)
```

See [Waiting](waiting.md).
