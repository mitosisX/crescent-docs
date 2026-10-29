# Sheet

`crescent.ui` · A panel that slides up from the bottom over the screen. show() opens it; dragging it down, tapping outside or close() dismisses it.

## Create

```lua
local ui = require("crescent.ui")
ui.Sheet()
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

### `close`

```lua
Sheet:close()
```

Closes the sheet.

### `focus`

```lua
Sheet:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Sheet:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getContent`

```lua
Sheet:getContent() --> any
```

What the sheet holds, or nil.

### `getMenu`

```lua
Sheet:getMenu() --> string[]
```

The widget's menu items.

### `getPeek`

```lua
Sheet:getPeek() --> number
```

The peek height in dp.

### `isExpanded`

```lua
Sheet:isExpanded() --> boolean
```

Whether the sheet opens all the way up.

### `isOpen`

```lua
Sheet:isOpen() --> boolean
```

Whether the sheet is open.

### `openMenu`

```lua
Sheet:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Sheet:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Sheet:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setContent`

```lua
Sheet:setContent(child: any)
```

Sets what the sheet holds, usually a Column.

### `setExpanded`

```lua
Sheet:setExpanded(on: boolean)
```

Whether the sheet opens all the way up instead of part way.

### `setGradient`

```lua
Sheet:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Sheet:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Sheet:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Sheet:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Sheet:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Sheet:setMinWidth(width: number)
```

Smallest width in dp.

### `setPeek`

```lua
Sheet:setPeek(dp: number)
```

How much of the sheet shows before the user drags it up, in dp. 0 (the default) fits the content.

### `setSize`

```lua
Sheet:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Sheet:setWidth(width: number)
```

Fixed width in dp.

### `show`

```lua
Sheet:show()
```

Opens the sheet over the screen.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Sheet:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnClose`

```lua
Sheet:setOnClose(function(widget) end)
```

Fired when the sheet closes, however it was closed.

### `setOnLongPress`

```lua
Sheet:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Sheet:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Sheet:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
