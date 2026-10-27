# Icon

`crescent.ui` · A Material icon picked by name, such as "inbox" or "star_border".

## Create

```lua
local ui = require("crescent.ui")
ui.Icon(name: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `icon` | `string` | The icon's name in the Material Icons font |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `tint` | `string or integer or nil` | The icon's colour: a colour or a theme role such as "primary"; nil goes back to "onSurface" |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
Icon:focus()
```

Moves keyboard focus here.

### `setBackgroundColor`

```lua
Icon:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setHeight`

```lua
Icon:setHeight(height: number)
```

Fixed height in dp.

### `setIconSize`

```lua
Icon:setIconSize(dp: number)
```

Sets the icon's size in dp (24 by default).

### `setMargins`

```lua
Icon:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Icon:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Icon:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Icon:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Icon:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Icon:setOnClick(function(widget) end)
```

Fired when the icon is tapped.

### `setOnLongPress`

```lua
Icon:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Icon:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
