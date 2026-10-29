# Stack

`crescent.ui` · Draws children on top of each other: a background behind content, a badge over a picture.

## Create

```lua
local ui = require("crescent.ui")
ui.Stack()
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

### `addChild`

```lua
Stack:addChild(child: any, align?: string)
```

Adds a widget on top of the others; align places it ("center", "top", "bottom", "left", "right", or a corner as two words: "top right", "top left", "bottom right", "bottom left"), or "fill" covers the whole stack, as a background does.

### `clear`

```lua
Stack:clear()
```

Removes every child.

### `focus`

```lua
Stack:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Stack:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getChildAt`

```lua
Stack:getChildAt(index: integer) --> any
```

The child at a 1-based position, or nil.

### `getChildCount`

```lua
Stack:getChildCount() --> integer
```

How many children the stack has.

### `getMenu`

```lua
Stack:getMenu() --> string[]
```

The widget's menu items.

### `openMenu`

```lua
Stack:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Stack:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Stack:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
Stack:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Stack:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Stack:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Stack:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Stack:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Stack:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Stack:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Stack:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Stack:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Stack:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Stack:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Stack:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
