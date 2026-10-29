# SegmentedButton

`crescent.ui` · A row of joined buttons where one is chosen, for two to five short choices. Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.SegmentedButton()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `multiple` | `boolean` | Whether several items can be on at once instead of just one |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addItem`

```lua
SegmentedButton:addItem(label: string, icon?: string)
```

Adds an item: a label, and an optional Material icon name shown before it.

### `clear`

```lua
SegmentedButton:clear()
```

Removes every item.

### `focus`

```lua
SegmentedButton:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
SegmentedButton:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getItemCount`

```lua
SegmentedButton:getItemCount() --> integer
```

How many items there are.

### `getItemLabel`

```lua
SegmentedButton:getItemLabel(index: integer) --> string?
```

The label of an item (from 1), or nil.

### `getMenu`

```lua
SegmentedButton:getMenu() --> string[]
```

The widget's menu items.

### `getSelectedIndex`

```lua
SegmentedButton:getSelectedIndex() --> integer
```

The chosen position (from 1), or 0 if none is. With several on, the first of them.

### `getSelectedIndexes`

```lua
SegmentedButton:getSelectedIndexes() --> integer[]
```

The positions (from 1) of every item that is on.

### `openMenu`

```lua
SegmentedButton:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
SegmentedButton:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
SegmentedButton:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
SegmentedButton:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
SegmentedButton:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
SegmentedButton:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
SegmentedButton:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
SegmentedButton:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
SegmentedButton:setMinWidth(width: number)
```

Smallest width in dp.

### `setSelectedIndex`

```lua
SegmentedButton:setSelectedIndex(index: integer)
```

Chooses an item (from 1); 0 clears the choice. Does not fire onSelect.

### `setSize`

```lua
SegmentedButton:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
SegmentedButton:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
SegmentedButton:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
SegmentedButton:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
SegmentedButton:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
SegmentedButton:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnSelect`

```lua
SegmentedButton:setOnSelect(function(widget, index: integer) end)
```

Fired when the user chooses an item.
