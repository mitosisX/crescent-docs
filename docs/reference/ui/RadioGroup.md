# RadioGroup

`crescent.ui` · Holds RadioButtons so only one is picked at a time. Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.RadioGroup()
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
RadioGroup:addChild(child: any)
```

Adds a choice.

### `clear`

```lua
RadioGroup:clear()
```

Removes every choice.

### `focus`

```lua
RadioGroup:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
RadioGroup:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getChildCount`

```lua
RadioGroup:getChildCount() --> integer
```

How many choices there are.

### `getMenu`

```lua
RadioGroup:getMenu() --> string[]
```

The widget's menu items.

### `getSelectedIndex`

```lua
RadioGroup:getSelectedIndex() --> integer
```

The picked position (from 1), or 0 if none.

### `openMenu`

```lua
RadioGroup:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
RadioGroup:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
RadioGroup:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
RadioGroup:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
RadioGroup:setHeight(height: number)
```

Fixed height in dp.

### `setHorizontal`

```lua
RadioGroup:setHorizontal(on: boolean)
```

Lays the choices out side by side instead of stacked.

### `setMargins`

```lua
RadioGroup:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
RadioGroup:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
RadioGroup:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
RadioGroup:setMinWidth(width: number)
```

Smallest width in dp.

### `setSelectedIndex`

```lua
RadioGroup:setSelectedIndex(index: integer)
```

Picks the choice at a position (from 1); 0 clears them all.

### `setSize`

```lua
RadioGroup:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
RadioGroup:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
RadioGroup:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
RadioGroup:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
RadioGroup:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
RadioGroup:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnSelect`

```lua
RadioGroup:setOnSelect(function(widget, index: integer) end)
```

Fired when the picked choice changes.
