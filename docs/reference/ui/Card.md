# Card

`crescent.ui` · A rounded raised panel holding one widget, usually a Column.

## Create

```lua
local ui = require("crescent.ui")
ui.Card()
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

### `focus`

```lua
Card:focus()
```

Moves keyboard focus here.

### `getCornerRadius`

```lua
Card:getCornerRadius()
```

The top-left corner's radius in dp.

### `setBackgroundColor`

```lua
Card:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setContent`

```lua
Card:setContent(content: any)
```

Sets what the card holds.

### `setCornerRadius`

```lua
Card:setCornerRadius(a: number, b?: number, c?: number, d?: number)
```

How rounded the corners are, in dp: one value for all, two for top then bottom, or top-left, top-right, bottom-right, bottom-left.

### `setElevation`

```lua
Card:setElevation(dp: number)
```

How raised the card looks, in dp.

### `setHeight`

```lua
Card:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Card:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Inner padding in dp: one value, vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Card:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Card:setMinWidth(width: number)
```

Smallest width in dp.

### `setOutlined`

```lua
Card:setOutlined(on: boolean)
```

Draws an outline instead of a shadow.

### `setSize`

```lua
Card:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Card:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Card:setOnClick(function(widget) end)
```

Fired when the card is tapped.

### `setOnLongPress`

```lua
Card:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Card:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
