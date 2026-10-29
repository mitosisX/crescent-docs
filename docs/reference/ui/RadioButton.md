# RadioButton

`crescent.ui` · One choice in a RadioGroup; picking it clears the others.

## Create

```lua
local ui = require("crescent.ui")
ui.RadioButton(text?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `checked` | `boolean` | Whether this choice is picked |
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `font` | `string` | The font file the text uses: "assets/name.ttf", an absolute path, or a path in the app's files |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `text` | `string` | The text shown |
| `textAlignment` | `"left" or "center" or "right" or "top" or "bottom" or "hcenter" or "vcenter"` | Where the text sits |
| `textRole` | `string` | A Material 3 type role like "titleMedium" or "bodySmall"; sets size, weight and spacing, and keeps the text colour and font; set the role before size/bold |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
RadioButton:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
RadioButton:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getMenu`

```lua
RadioButton:getMenu() --> string[]
```

The widget's menu items.

### `openMenu`

```lua
RadioButton:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
RadioButton:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
RadioButton:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setBold`

```lua
RadioButton:setBold(bold: boolean)
```

Bold text on or off.

### `setGradient`

```lua
RadioButton:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
RadioButton:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
RadioButton:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
RadioButton:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
RadioButton:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
RadioButton:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
RadioButton:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setTextColor`

```lua
RadioButton:setTextColor(color: string|integer)
```

Text colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setTextSize`

```lua
RadioButton:setTextSize(size: number)
```

Text size in sp.

### `setWidth`

```lua
RadioButton:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnCheck`

```lua
RadioButton:setOnCheck(function(widget, checked: boolean) end)
```

Fired when this choice is picked or cleared.

### `setOnClick`

```lua
RadioButton:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
RadioButton:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
RadioButton:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
RadioButton:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
