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
| `align` | `string` | Where the content sits inside the card: "top", "center", "bottom right", ...; "fill" (the default) stretches it across the width |
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `outlined` | `boolean` | Whether the card has a thin outline; cards have none by default |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
Card:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Card:getBadge()
```

What the badge shows, or "" if there is none.

### `getCornerRadius`

```lua
Card:getCornerRadius()
```

The top-left corner's radius in dp.

### `getMenu`

```lua
Card:getMenu()
```

The widget's menu items.

### `openMenu`

```lua
Card:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Card:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Card:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

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

### `setGradient`

```lua
Card:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the card with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

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

### `setMenu`

```lua
Card:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

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

### `setOnMenuSelect`

```lua
Card:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Card:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
