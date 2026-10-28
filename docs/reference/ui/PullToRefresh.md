# PullToRefresh

`crescent.ui` · Holds a list or a Scroller and reloads it when the user drags down from the top. Set refreshing to false when the reload is done.

## Create

```lua
local ui = require("crescent.ui")
ui.PullToRefresh()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `refreshing` | `boolean` | Whether the spinner is turning; set it to false when the reload has finished |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `focus`

```lua
PullToRefresh:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
PullToRefresh:getBadge()
```

What the badge shows, or "" if there is none.

### `getContent`

```lua
PullToRefresh:getContent()
```

What is inside, or nil.

### `getMenu`

```lua
PullToRefresh:getMenu()
```

The widget's menu items.

### `openMenu`

```lua
PullToRefresh:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
PullToRefresh:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
PullToRefresh:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setContent`

```lua
PullToRefresh:setContent(child: any)
```

Sets what the pull reloads, usually a List or a Scroller.

### `setGradient`

```lua
PullToRefresh:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
PullToRefresh:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
PullToRefresh:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
PullToRefresh:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
PullToRefresh:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
PullToRefresh:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
PullToRefresh:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setSpinnerColor`

```lua
PullToRefresh:setSpinnerColor(color: string|integer)
```

The spinner's colour: "#rrggbb", a name like "red", a theme role like "primary", or an ARGB integer.

### `setWidth`

```lua
PullToRefresh:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
PullToRefresh:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
PullToRefresh:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
PullToRefresh:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnRefresh`

```lua
PullToRefresh:setOnRefresh(function(widget) end)
```

Fired when the user drags down from the top. The spinner keeps turning until you set refreshing to false.

### `setOnResize`

```lua
PullToRefresh:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
