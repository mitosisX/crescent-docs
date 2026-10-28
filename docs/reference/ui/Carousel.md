# Carousel

`crescent.ui` · A swipeable row of items that shrink at the edges, for a gallery or a shelf of cards. Give it a height (setHeight). Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.Carousel()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `layout` | `string` | How the items are sized: "browse" (the default, several at once), "hero" (one big one with the next peeking) or "full" (one at a time) |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addChild`

```lua
Carousel:addChild(child: any)
```

Adds an item, usually a Card or an Image.

### `clear`

```lua
Carousel:clear()
```

Removes every item.

### `focus`

```lua
Carousel:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Carousel:getBadge()
```

What the badge shows, or "" if there is none.

### `getChildAt`

```lua
Carousel:getChildAt(index: integer)
```

The item at a position (from 1), or nil.

### `getChildCount`

```lua
Carousel:getChildCount()
```

How many items there are.

### `getCornerRadius`

```lua
Carousel:getCornerRadius()
```

The item corner radius in dp.

### `getItemWidth`

```lua
Carousel:getItemWidth()
```

The item width in dp.

### `getMenu`

```lua
Carousel:getMenu()
```

The widget's menu items.

### `getSelectedIndex`

```lua
Carousel:getSelectedIndex()
```

The item nearest the start of the carousel (from 1), or 0 if there are none.

### `openMenu`

```lua
Carousel:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Carousel:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Carousel:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setCornerRadius`

```lua
Carousel:setCornerRadius(dp: number)
```

How rounded the items' corners are, in dp.

### `setGradient`

```lua
Carousel:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Carousel:setHeight(height: number)
```

Fixed height in dp.

### `setItemWidth`

```lua
Carousel:setItemWidth(dp: number)
```

How wide an item is, in dp. Only "browse" uses it.

### `setMargins`

```lua
Carousel:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Carousel:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Carousel:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Carousel:setMinWidth(width: number)
```

Smallest width in dp.

### `setSelectedIndex`

```lua
Carousel:setSelectedIndex(index: integer)
```

Scrolls to an item (from 1).

### `setSize`

```lua
Carousel:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Carousel:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Carousel:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnItemSelect`

```lua
Carousel:setOnItemSelect(function(widget, index: integer) end)
```

Fired with the position when the user taps an item.

### `setOnLongPress`

```lua
Carousel:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Carousel:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Carousel:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
