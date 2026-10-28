# Image

`crescent.ui` · Shows a picture from the app's files or assets.

## Create

```lua
local ui = require("crescent.ui")
ui.Image(path?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `scale` | `"fit" or "crop" or "stretch"` | How the picture fills the widget: whole and centred, cropped to fill, or stretched |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `tint` | `string or integer or nil` | A colour painted over the picture's shape, for one-colour icons; nil removes it |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
Image:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Image:getBadge()
```

What the badge shows, or "" if there is none.

### `getCornerRadius`

```lua
Image:getCornerRadius()
```

The top-left corner's radius in dp.

### `getMenu`

```lua
Image:getMenu()
```

The widget's menu items.

### `getSource`

```lua
Image:getSource()
```

The path last given to setSource.

### `openMenu`

```lua
Image:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Image:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Image:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setCornerRadius`

```lua
Image:setCornerRadius(a: number, b?: number, c?: number, d?: number)
```

Rounds the picture's corners, in dp: one value for all, two for top then bottom, or top-left, top-right, bottom-right, bottom-left. Half the size makes a circle.

### `setGradient`

```lua
Image:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Image:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Image:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Image:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Image:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Image:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Image:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setSource`

```lua
Image:setSource(path: string)
```

Loads a picture: "assets/name.png" (shipped with the app), an absolute path, or a path in the app's files.

### `setWidth`

```lua
Image:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Image:setOnClick(function(widget) end)
```

Fired when the image is tapped.

### `setOnLongPress`

```lua
Image:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Image:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Image:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
