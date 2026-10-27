# Slider

`crescent.ui` · A draggable bar choosing a whole number in a range (default 0..100).

## Create

```lua
local ui = require("crescent.ui")
ui.Slider()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `value` | `integer` | The chosen number |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
Slider:focus()
```

Moves keyboard focus here.

### `setBackgroundColor`

```lua
Slider:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setHeight`

```lua
Slider:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Slider:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Slider:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Slider:setMinWidth(width: number)
```

Smallest width in dp.

### `setRange`

```lua
Slider:setRange(low: integer, high: integer)
```

The lowest and highest values.

### `setSize`

```lua
Slider:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Slider:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnLongPress`

```lua
Slider:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Slider:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnValueChange`

```lua
Slider:setOnValueChange(function(widget, value: integer) end)
```

Fired while the value changes.
