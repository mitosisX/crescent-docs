# Divider

`crescent.ui` · A thin line between things. In a Row, setVertical(true) makes it stand up.

## Create

```lua
local ui = require("crescent.ui")
ui.Divider()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `vertical` | `boolean` | Whether the line stands up (for a Row) instead of lying across (for a Column) |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
Divider:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Divider:getBadge()
```

What the badge shows, or "" if there is none.

### `getMenu`

```lua
Divider:getMenu()
```

The widget's menu items.

### `getThickness`

```lua
Divider:getThickness()
```

The line's thickness in dp.

### `openMenu`

```lua
Divider:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Divider:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Divider:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setColor`

```lua
Divider:setColor(color: string|integer)
```

The line's colour: "#rrggbb", a name like "red", a theme role like "outlineVariant", or an ARGB integer.

### `setGradient`

```lua
Divider:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Divider:setHeight(height: number)
```

Fixed height in dp.

### `setInset`

```lua
Divider:setInset(before: number, after?: number)
```

Blank space before and after the line, in dp.

### `setMargins`

```lua
Divider:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Divider:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Divider:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Divider:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Divider:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setThickness`

```lua
Divider:setThickness(dp: number)
```

How thick the line is, in dp.

### `setWidth`

```lua
Divider:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Divider:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Divider:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Divider:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Divider:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
