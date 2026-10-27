# TextField

`crescent.ui` · A one-line text field, in a Material box with a floating label.

## Create

```lua
local ui = require("crescent.ui")
ui.TextField(text?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `font` | `string` | The font file the text uses: "assets/name.ttf", an absolute path, or a path in the app's files |
| `hint` | `string` | The label, which floats above the box once there is text |
| `leadingIcon` | `string` | The name of a Material icon shown before the text; "" for none |
| `placeholder` | `string` | Grey text shown inside the empty box |
| `readOnly` | `boolean` | Whether the text can be edited |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `text` | `string` | The text shown |
| `textAlignment` | `"left" or "center" or "right" or "top" or "bottom" or "hcenter" or "vcenter"` | Where the text sits |
| `textRole` | `string` | A Material 3 type role like "titleMedium" or "bodySmall"; sets size, weight and spacing, and keeps the text colour and font; set the role before size/bold |
| `trailingIcon` | `string` | The name of a Material icon shown after the text; "" for none |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `clear`

```lua
TextField:clear()
```

Empties the field.

### `getCornerRadius`

```lua
TextField:getCornerRadius()
```

The top-left corner's radius in dp.

### `setBackgroundColor`

```lua
TextField:setBackgroundColor(color: string|integer)
```

Background colour of the box: "#rrggbb", a name like "red", a theme role like "surfaceContainerHigh", or an ARGB integer.

### `setBold`

```lua
TextField:setBold(bold: boolean)
```

Bold text on or off.

### `setCornerRadius`

```lua
TextField:setCornerRadius(a: number, b?: number, c?: number, d?: number)
```

How rounded the box's corners are, in dp: one value for all, two for top then bottom, or top-left, top-right, bottom-right, bottom-left.

### `setError`

```lua
TextField:setError(message: string)
```

Shows a red message under the box; an empty string clears it.

### `setHeight`

```lua
TextField:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
TextField:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMaxLength`

```lua
TextField:setMaxLength(length: integer)
```

Longest text allowed (0 = no limit).

### `setMinHeight`

```lua
TextField:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
TextField:setMinWidth(width: number)
```

Smallest width in dp.

### `setNumeric`

```lua
TextField:setNumeric(on: boolean)
```

Shows the number keyboard.

### `setOutlined`

```lua
TextField:setOutlined(on: boolean)
```

Draws the box's outline (the default); false leaves only its fill, as for a search bar.

### `setPassword`

```lua
TextField:setPassword(on: boolean)
```

Hides what is typed, for a password.

### `setSize`

```lua
TextField:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setTextColor`

```lua
TextField:setTextColor(color: string|integer)
```

Text colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setTextSize`

```lua
TextField:setTextSize(size: number)
```

Text size in sp.

### `setWidth`

```lua
TextField:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
TextField:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLeadingIconClick`

```lua
TextField:setOnLeadingIconClick(function(widget) end)
```

Fired when the icon before the text is tapped.

### `setOnLongPress`

```lua
TextField:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
TextField:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnSubmit`

```lua
TextField:setOnSubmit(function(widget) end)
```

Fired when the user taps Done on the keyboard.

### `setOnTextChange`

```lua
TextField:setOnTextChange(function(widget, text: string) end)
```

Fired whenever the text changes.

### `setOnTrailingIconClick`

```lua
TextField:setOnTrailingIconClick(function(widget) end)
```

Fired when the icon after the text is tapped.
