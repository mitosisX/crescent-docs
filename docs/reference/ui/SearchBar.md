# SearchBar

`crescent.ui` · A rounded bar the user types a search into. setOnTextChange filters as they type; setOnSubmit fires when they press the keyboard's search key.

## Create

```lua
local ui = require("crescent.ui")
ui.SearchBar(hint?: string)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `font` | `string` | The font file the text uses: "assets/name.ttf", an absolute path, or a path in the app's files |
| `hint` | `string` | The grey text shown while the bar is empty |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `text` | `string` | What the bar holds |
| `textAlignment` | `"left" or "center" or "right" or "top" or "bottom" or "hcenter" or "vcenter"` | Where the text sits |
| `textRole` | `string` | A Material 3 type role like "titleMedium" or "bodySmall"; sets size, weight and spacing, and keeps the text colour and font; set the role before size/bold |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `clear`

```lua
SearchBar:clear()
```

Empties the bar.

### `focus`

```lua
SearchBar:focus()
```

Opens the keyboard with the bar ready to type in.

### `getBadge`

```lua
SearchBar:getBadge()
```

What the badge shows, or "" if there is none.

### `getMenu`

```lua
SearchBar:getMenu()
```

The widget's menu items.

### `openMenu`

```lua
SearchBar:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
SearchBar:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
SearchBar:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setBold`

```lua
SearchBar:setBold(bold: boolean)
```

Bold text on or off.

### `setGradient`

```lua
SearchBar:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
SearchBar:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
SearchBar:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
SearchBar:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
SearchBar:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
SearchBar:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
SearchBar:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setTextColor`

```lua
SearchBar:setTextColor(color: string|integer)
```

Text colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setTextSize`

```lua
SearchBar:setTextSize(size: number)
```

Text size in sp.

### `setWidth`

```lua
SearchBar:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
SearchBar:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
SearchBar:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
SearchBar:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
SearchBar:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnSubmit`

```lua
SearchBar:setOnSubmit(function(widget, text: string) end)
```

Fired when the user presses the keyboard's search key.

### `setOnTextChange`

```lua
SearchBar:setOnTextChange(function(widget, text: string) end)
```

Fired on every keystroke, with everything the bar holds.
