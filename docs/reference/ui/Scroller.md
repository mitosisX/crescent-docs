# Scroller

`crescent.ui` · Scrolls one child (usually a layout) when it is bigger than the screen: down the page, or sideways for a row of cards.

## Create

```lua
local ui = require("crescent.ui")
ui.Scroller()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `horizontal` | `boolean` | Whether it scrolls sideways instead of down |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
Scroller:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
Scroller:getBadge()
```

What the badge shows, or "" if there is none.

### `getContent`

```lua
Scroller:getContent()
```

What is scrolling, or nil.

### `getMenu`

```lua
Scroller:getMenu()
```

The widget's menu items.

### `openMenu`

```lua
Scroller:openMenu()
```

Opens the widget's menu, as a long press would.

### `scrollToEnd`

```lua
Scroller:scrollToEnd()
```

Scrolls to the end: the bottom, or the right when it scrolls sideways.

### `setBackgroundColor`

```lua
Scroller:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Scroller:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setContent`

```lua
Scroller:setContent(child: any)
```

Sets what scrolls.

### `setGradient`

```lua
Scroller:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Scroller:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Scroller:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Scroller:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Scroller:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Scroller:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Scroller:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Scroller:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Scroller:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Scroller:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Scroller:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Scroller:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnScroll`

```lua
Scroller:setOnScroll(function(widget, dx: integer, dy: integer) end)
```

Fired with (dx, dy) in dp as the content scrolls. dy > 0 means the content moved up (the user scrolled down); a sideways scroller reports dx.
