# Switch

`crescent.ui` · An on/off switch, for settings.

## Create

```lua
local ui = require("crescent.ui")
ui.Switch(text?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `checked` | `boolean` | Whether it is on |
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
Switch:focus()
```

Moves keyboard focus here.

### `setBackgroundColor`

```lua
Switch:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBold`

```lua
Switch:setBold(bold: boolean)
```

Bold text on or off.

### `setHeight`

```lua
Switch:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Switch:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Switch:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Switch:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Switch:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setTextColor`

```lua
Switch:setTextColor(color: string|integer)
```

Text colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setTextSize`

```lua
Switch:setTextSize(size: number)
```

Text size in sp.

### `setWidth`

```lua
Switch:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnCheck`

```lua
Switch:setOnCheck(function(widget, checked: boolean) end)
```

Fired when the switch is turned on or off.

### `setOnClick`

```lua
Switch:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Switch:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Switch:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
