# NumberPicker

`crescent.ui` · A number with - and + buttons (for a list of choices use Dropdown).

## Create

```lua
local ui = require("crescent.ui")
ui.NumberPicker()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `prefix` | `string` | Text before the number |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `suffix` | `string` | Text after the number |
| `value` | `integer` | The number shown |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
NumberPicker:focus()
```

Moves keyboard focus here.

### `setBackgroundColor`

```lua
NumberPicker:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setHeight`

```lua
NumberPicker:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
NumberPicker:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
NumberPicker:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
NumberPicker:setMinWidth(width: number)
```

Smallest width in dp.

### `setRange`

```lua
NumberPicker:setRange(min: integer, max: integer)
```

The lowest and highest values.

### `setSize`

```lua
NumberPicker:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
NumberPicker:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnLongPress`

```lua
NumberPicker:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
NumberPicker:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnValueChange`

```lua
NumberPicker:setOnValueChange(function(widget, value: integer) end)
```

Fired when - or + changes the value.
