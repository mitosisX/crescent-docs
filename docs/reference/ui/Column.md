# Column

`crescent.ui` · Stacks widgets top to bottom.

## Create

```lua
local ui = require("crescent.ui")
ui.Column()
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
Column:addChild(child: any, stretch?: integer)
```

Adds a widget or layout; stretch > 0 makes it take spare space.

### `addSpace`

```lua
Column:addSpace(size: number)
```

Adds fixed empty space, in dp.

### `addStretch`

```lua
Column:addStretch(stretch?: number)
```

Adds empty space that grows to fill the gap.

### `clear`

```lua
Column:clear()
```

Removes every child.

### `focus`

```lua
Column:focus()
```

Moves keyboard focus here.

### `getChildAt`

```lua
Column:getChildAt(index: integer)
```

The child at a 1-based position, or nil.

### `getChildCount`

```lua
Column:getChildCount()
```

How many children the layout has.

### `getSpacing`

```lua
Column:getSpacing()
```

Space between children, in dp.

### `setAlign`

```lua
Column:setAlign(alignment: string)
```

Where children sit when there is room: "top", "center", "left", ...

### `setBackgroundColor`

```lua
Column:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setHeight`

```lua
Column:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Column:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Inner padding in dp: one value, vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Column:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Column:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Column:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setSpacing`

```lua
Column:setSpacing(size: number)
```

Space between children, in dp.

### `setWidth`

```lua
Column:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Column:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Column:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Column:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
