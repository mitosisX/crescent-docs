# Flow

`crescent.ui` · Children side by side, carrying on to the next line when the line is full.

## Create

```lua
local ui = require("crescent.ui")
ui.Flow()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `spacing` | `number` | The gap between children in dp, across and down |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addChild`

```lua
Flow:addChild(child: any)
```

Adds a child at the end.

### `clear`

```lua
Flow:clear()
```

Removes every child.

### `focus`

```lua
Flow:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Flow:getBadge()
```

What the badge shows, or "" if there is none.

### `getChildAt`

```lua
Flow:getChildAt(index: integer)
```

The child at a position (from 1), or nil.

### `getChildCount`

```lua
Flow:getChildCount()
```

How many children there are.

### `getMenu`

```lua
Flow:getMenu()
```

The widget's menu items.

### `openMenu`

```lua
Flow:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Flow:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Flow:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
Flow:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Flow:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Flow:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Flow:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Flow:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Flow:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Flow:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Flow:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Flow:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Flow:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Flow:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Flow:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
