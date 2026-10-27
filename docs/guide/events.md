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
| `setOnClick` | tapped |
| `setOnLongPress` | pressed and held (every widget has it) |
| `setOnTextChange` | text in a field changed |
| `setOnSubmit` | the keyboard's action key in a one-line field |
| `setOnCheck` | a checkbox, switch or radio button changed |
| `setOnSelect` | a tab, bar item or radio choice was picked |
| `setOnItemSelect` / `setOnItemLongPress` | an item in a list or dropdown |
| `setOnValueChange` | a slider or number picker moved |
| `setOnResize` | the widget's size changed |
| `setOnScroll` | a scroller moved |
| `setOnClose` | a screen went away |

Each widget's page in the [reference](../reference/ui/index.md) lists its events.

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
