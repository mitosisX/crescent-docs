# Button

`crescent.ui` · A tappable button.

## Create

```lua
local ui = require("crescent.ui")
ui.Button(text?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `checkable` | `boolean` | Whether the button toggles on and off |
| `checked` | `boolean` | Whether a checkable button is on |
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `font` | `string` | The font file the text uses: "assets/name.ttf", an absolute path, or a path in the app's files |
| `icon` | `string` | The name of a Material icon shown before the text; "" for none |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `text` | `string` | The text shown |
| `textAlignment` | `"left" or "center" or "right" or "top" or "bottom" or "hcenter" or "vcenter"` | Where the text sits |
| `textRole` | `string` | A Material 3 type role like "titleMedium" or "bodySmall"; sets size, weight and spacing, and keeps the text colour and font; set the role before size/bold |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `click`

```lua
Button:click()
```

Taps the button from code.

### `focus`

```lua
Button:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Button:getBadge()
```

What the badge shows, or "" if there is none.

### `getCornerRadius`

```lua
Button:getCornerRadius()
```

The corner radius set with setCornerRadius, in dp.

### `getMenu`

```lua
Button:getMenu()
```

The widget's menu items.

### `getVariant`

```lua
Button:getVariant()
```

The look set with setVariant.

### `openMenu`

```lua
Button:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Button:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer. Keeps the button's shape, and replaces a gradient.

### `setBadge`

```lua
Button:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setBold`

```lua
Button:setBold(bold: boolean)
```

Bold text on or off.

### `setCornerRadius`

```lua
Button:setCornerRadius(dp: number)
```

How rounded the corners are, in dp: one value for all four. A large value makes a pill.

### `setGradient`

```lua
Button:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the button with a gradient from one colour to another, keeping its corners. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Button:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Button:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Button:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Button:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Button:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Button:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setTextColor`

```lua
Button:setTextColor(color: string|integer)
```

Text colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setTextSize`

```lua
Button:setTextSize(size: number)
```

Text size in sp.

### `setVariant`

```lua
Button:setVariant(name: string)
```

How the button looks: "filled" (the default), "tonal", "elevated", "outlined" or "text".

### `setWidth`

```lua
Button:setWidth(width: number)
```

Fixed width in dp.

### `toggle`

```lua
Button:toggle()
```

Flips a checkable button.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Button:setOnClick(function(widget, checked: boolean) end)
```

Fired when the button is tapped.

### `setOnLongPress`

```lua
Button:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Button:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Button:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
