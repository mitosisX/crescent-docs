# Stack

`crescent.ui` · Draws children on top of each other: a background behind content, a badge over a picture.

## Create

```lua
local ui = require("crescent.ui")
ui.Stack()
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
Stack:addChild(child: any, align?: string)
```

Adds a widget on top of the others; align places it ("center", "top", "bottom", "left", "right"...), or "fill" covers the whole stack, as a background does.

### `clear`

```lua
Stack:clear()
```

Removes every child.

### `focus`

```lua
Stack:focus()
```

Moves keyboard focus here.

### `getChildAt`

```lua
Stack:getChildAt(index: integer)
```

The child at a 1-based position, or nil.

### `getChildCount`

```lua
Stack:getChildCount()
```

How many children the stack has.

### `setBackgroundColor`

```lua
Stack:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setHeight`

```lua
Stack:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Stack:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Stack:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Stack:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Stack:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Stack:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnLongPress`

```lua
Stack:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Stack:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
