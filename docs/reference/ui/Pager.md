# Pager

`crescent.ui` · Pages you swipe through, one child per page, with optional dots. Give it a height (setHeight): pages fill the Pager. Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.Pager()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `dots` | `boolean` | Whether small dots under the pages show which one is open; false by default |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `vertical` | `boolean` | Whether pages are swiped up and down instead of sideways |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addChild`

```lua
Pager:addChild(child: any)
```

Adds a page. The page fills the Pager: its own size and margins are not used.

### `clear`

```lua
Pager:clear()
```

Removes every page.

### `focus`

```lua
Pager:focus()
```

Moves keyboard focus here.

### `getAutoAdvance`

```lua
Pager:getAutoAdvance()
```

The auto-advance time in seconds, or 0.

### `getBadge`

```lua
Pager:getBadge()
```

What the badge shows, or "" if there is none.

### `getChildCount`

```lua
Pager:getChildCount()
```

How many pages there are.

### `getMenu`

```lua
Pager:getMenu()
```

The widget's menu items.

### `getPeek`

```lua
Pager:getPeek()
```

The peek width in dp.

### `getSelectedIndex`

```lua
Pager:getSelectedIndex()
```

The page showing (from 1), or 0 if there are none.

### `openMenu`

```lua
Pager:openMenu()
```

Opens the widget's menu, as a long press would.

### `setAutoAdvance`

```lua
Pager:setAutoAdvance(seconds: number)
```

Moves to the next page by itself every so many seconds, wrapping round at the end. 0 (the default) stops it.

### `setBackgroundColor`

```lua
Pager:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Pager:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
Pager:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
Pager:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Pager:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
Pager:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
Pager:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Pager:setMinWidth(width: number)
```

Smallest width in dp.

### `setPeek`

```lua
Pager:setPeek(dp: number)
```

How much of the next page peeks in at the side, in dp. 0 (the default) shows one page at a time.

### `setSelectedIndex`

```lua
Pager:setSelectedIndex(index: integer)
```

Scrolls to a page (from 1). Does not fire onSelect.

### `setSize`

```lua
Pager:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Pager:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
Pager:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
Pager:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Pager:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Pager:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnSelect`

```lua
Pager:setOnSelect(function(widget, index: integer) end)
```

Fired when the user swipes to a page.
