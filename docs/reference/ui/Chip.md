# Chip

`crescent.ui` · A small rounded tappable label: a tag, a filter or something the user chose. Put several in a ChipGroup.

## Create

```lua
local ui = require("crescent.ui")
ui.Chip(text?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `checkable` | `boolean` | Whether tapping the chip turns it on and leaves it on, the way a filter does |
| `checked` | `boolean` | Whether a checkable chip is on |
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `font` | `string` | The font file the text uses: "assets/name.ttf", an absolute path, or a path in the app's files |
| `icon` | `string` | The name of a Material icon shown before the text; "" for none |
| `removable` | `boolean` | Whether the chip shows an x on its right that takes it away |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `text` | `string` | The text shown |
| `textAlignment` | `"left" or "center" or "right" or "top" or "bottom" or "hcenter" or "vcenter"` | Where the text sits |
| `textRole` | `string` | A Material 3 type role like "titleMedium" or "bodySmall"; sets size, weight and spacing, and keeps the text colour and font; set the role before size/bold |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
Chip:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Chip:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getMenu`

```lua
Chip:getMenu() --> string[]
```

The widget's menu items.

### `openMenu`

```lua
Chip:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Chip:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "secondaryContainer", or an ARGB integer. Keeps the chip's shape.

### `setBadge`

```lua
Chip:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setBold`

```lua
Chip:setBold(bold: boolean)
```

Bold text on or off.

### `setGradient`

```lua
Chip:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Chip:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Chip:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Chip:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Chip:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Chip:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Chip:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setTextColor`

```lua
Chip:setTextColor(color: string|integer)
```

Text colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setTextSize`

```lua
Chip:setTextSize(size: number)
```

Text size in sp.

### `setWidth`

```lua
Chip:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnCheck`

```lua
Chip:setOnCheck(function(widget, checked: boolean) end)
```

Fired when a checkable chip is turned on or off.

### `setOnClick`

```lua
Chip:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Chip:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Chip:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnRemove`

```lua
Chip:setOnRemove(function(widget) end)
```

Fired when the user taps the chip's x, to take it away.

### `setOnResize`

```lua
Chip:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
