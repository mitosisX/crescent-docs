# NavigationBar

`crescent.ui` · A bar of icon items along the bottom, each showing its own widget above it. Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.NavigationBar()
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

### `addItem`

```lua
NavigationBar:addItem(icon: string, label: string, content: any)
```

Adds an item: an icon by name, a label, and the widget it shows.

### `clear`

```lua
NavigationBar:clear()
```

Removes every item.

### `focus`

```lua
NavigationBar:focus()
```

Moves keyboard focus here.

### `getBadge`

```lua
NavigationBar:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getItemCount`

```lua
NavigationBar:getItemCount() --> integer
```

How many items there are.

### `getItemLabel`

```lua
NavigationBar:getItemLabel(index: integer) --> string?
```

The label of an item (from 1), or nil.

### `getMenu`

```lua
NavigationBar:getMenu() --> string[]
```

The widget's menu items.

### `getSelectedIndex`

```lua
NavigationBar:getSelectedIndex() --> integer
```

The open item (from 1), or 0 if there are none.

### `openMenu`

```lua
NavigationBar:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
NavigationBar:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
NavigationBar:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setGradient`

```lua
NavigationBar:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

### `setHeight`

```lua
NavigationBar:setHeight(height: number)
```

Fixed height in dp.

### `setItemBadge`

```lua
NavigationBar:setItemBadge(index: integer, value: integer|string|nil)
```

Puts a badge over an item's icon (positions from 1): a number (0 removes it), a short piece of text, or nil to remove it.

### `setMargins`

```lua
NavigationBar:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMenu`

```lua
NavigationBar:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

### `setMinHeight`

```lua
NavigationBar:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
NavigationBar:setMinWidth(width: number)
```

Smallest width in dp.

### `setSelectedIndex`

```lua
NavigationBar:setSelectedIndex(index: integer)
```

Opens an item (from 1). Does not fire onSelect.

### `setSize`

```lua
NavigationBar:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
NavigationBar:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClick`

```lua
NavigationBar:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnLongPress`

```lua
NavigationBar:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
NavigationBar:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
NavigationBar:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.

### `setOnSelect`

```lua
NavigationBar:setOnSelect(function(widget, index: integer) end)
```

Fired when the user opens an item.
