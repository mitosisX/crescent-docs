# Dropdown

`crescent.ui` · A drop-down list. Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.Dropdown()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `hint` | `string` | The label above the box |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addItem`

```lua
Dropdown:addItem(text: string)
```

Adds one item.

### `addItems`

```lua
Dropdown:addItems(list: string[])
```

Adds several items.

### `clear`

```lua
Dropdown:clear()
```

Removes every item.

### `focus`

```lua
Dropdown:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Dropdown:getBadge()
```

What the badge shows, or "" if there is none.

### `getItemAt`

```lua
Dropdown:getItemAt(index: integer)
```

The text at a position (from 1), or nil.

### `getMenu`

```lua
Dropdown:getMenu()
```

The widget's menu items.

### `getSelectedIndex`

```lua
Dropdown:getSelectedIndex()
```

The chosen position (from 1), or 0 if empty.

### `getSelectedItem`

```lua
Dropdown:getSelectedItem()
```

The chosen item's text.

### `openMenu`

```lua
Dropdown:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Dropdown:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Dropdown:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
Dropdown:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Dropdown:setHeight(height: number)
```

Fixed height in dp.

### `setItems`

```lua
Dropdown:setItems(list: string[])
```

Replaces every item.

### `setMargins`

```lua
Dropdown:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Dropdown:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Dropdown:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Dropdown:setMinWidth(width: number)
```

Smallest width in dp.

### `setSelectedIndex`

```lua
Dropdown:setSelectedIndex(index: integer)
```

Chooses the item at a position (from 1).

### `setSize`

```lua
Dropdown:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Dropdown:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Dropdown:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnItemSelect`

```lua
Dropdown:setOnItemSelect(function(widget, index: integer) end)
```

Fired when the user picks an item.

### `setOnLongPress`

```lua
Dropdown:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Dropdown:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Dropdown:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
