# Grid

`crescent.ui` · Places widgets in rows and columns, counted from 1. Columns share the width equally.

## Create

```lua
local ui = require("crescent.ui")
ui.Grid()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addChild`

```lua
Grid:addChild(child: any, row: integer, column: integer, rowSpan?: integer, columnSpan?: integer)
```

Puts a widget at row, column (from 1), optionally spanning several cells.

### `clear`

```lua
Grid:clear()
```

Removes every child.

### `focus`

```lua
Grid:focus()
```

Moves keyboard focus here.

### `getChildCount`

```lua
Grid:getChildCount()
```

How many children the grid has.

### `getSpacing`

```lua
Grid:getSpacing()
```

Space between cells, in dp.

### `setBackgroundColor`

```lua
Grid:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setHeight`

```lua
Grid:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Grid:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Inner padding in dp: one value, vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Grid:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Grid:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Grid:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setSpacing`

```lua
Grid:setSpacing(size: number)
```

Space between cells, in dp.

### `setWidth`

```lua
Grid:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Grid:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Grid:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Grid:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
