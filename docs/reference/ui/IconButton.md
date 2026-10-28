# IconButton

`crescent.ui` · A round button that shows only an icon, such as "star_border". Give it a description for screen readers.

## Create

```lua
local ui = require("crescent.ui")
ui.IconButton(icon: string, description?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `checkable` | `boolean` | Whether the button stays pressed when tapped, for a star or a bookmark |
| `checked` | `boolean` | Whether a checkable button is on |
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `icon` | `string` | The icon's name in the Material Icons font |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `tint` | `string or integer or nil` | The icon's colour: a colour or a theme role such as "primary"; nil goes back to the theme's default |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
IconButton:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
IconButton:getBadge()
```

What the badge shows, or "" if there is none.

### `getCheckedIcon`

```lua
IconButton:getCheckedIcon()
```

The icon set with setCheckedIcon.

### `getMenu`

```lua
IconButton:getMenu()
```

The widget's menu items.

### `openMenu`

```lua
IconButton:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
IconButton:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer. Keeps the button's shape.

### `setBadge`

```lua
IconButton:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setCheckedIcon`

```lua
IconButton:setCheckedIcon(name: string)
```

The icon shown while a checkable button is on, such as "star" against "star_border"; "" uses the same icon for both.

### `setGradient`

```lua
IconButton:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
IconButton:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
IconButton:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
IconButton:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
IconButton:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
IconButton:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
IconButton:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
IconButton:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnCheck`

```lua
IconButton:setOnCheck(function(widget, checked: boolean) end)
```

Fired when a checkable button is turned on or off.

### `setOnClick`

```lua
IconButton:setOnClick(function(widget) end)
```

Fired when the button is tapped.

### `setOnLongPress`

```lua
IconButton:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
IconButton:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
IconButton:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
