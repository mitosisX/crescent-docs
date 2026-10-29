# ChipGroup

`crescent.ui` · Chips in rows that wrap onto the next line. Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.ChipGroup()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `singleChoice` | `boolean` | Whether only one chip can be on at a time |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addChild`

```lua
ChipGroup:addChild(child: any)
```

Adds a Chip.

### `clear`

```lua
ChipGroup:clear()
```

Removes every chip.

### `focus`

```lua
ChipGroup:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
ChipGroup:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getChildAt`

```lua
ChipGroup:getChildAt(index: integer) --> any
```

The chip at a position (from 1), or nil.

### `getChildCount`

```lua
ChipGroup:getChildCount() --> integer
```

How many chips there are.

### `getMenu`

```lua
ChipGroup:getMenu() --> string[]
```

The widget's menu items.

### `getSelectedIndex`

```lua
ChipGroup:getSelectedIndex() --> integer
```

The position of the chip that is on (from 1), or 0 if none is.

### `getSelectedIndexes`

```lua
ChipGroup:getSelectedIndexes() --> integer[]
```

The positions (from 1) of every chip that is on.

### `openMenu`

```lua
ChipGroup:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
ChipGroup:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
ChipGroup:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
ChipGroup:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
ChipGroup:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
ChipGroup:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
ChipGroup:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
ChipGroup:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
ChipGroup:setMinWidth(width: number)
```

Smallest width in dp.

### `setSelectedIndex`

```lua
ChipGroup:setSelectedIndex(index: integer)
```

Turns on the chip at a position (from 1); 0 turns them all off. Does not fire onSelect.

### `setSize`

```lua
ChipGroup:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
ChipGroup:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
ChipGroup:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
ChipGroup:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
ChipGroup:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
ChipGroup:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnSelect`

```lua
ChipGroup:setOnSelect(function(widget, index: integer) end)
```

Fired when the user turns a chip on or off. Single choice reports the chip that is on (0 if none is); otherwise it reports the chip the user just touched.
