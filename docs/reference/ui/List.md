# List

`crescent.ui` · A scrolling list of text items. Positions count from 1.

## Create

```lua
local ui = require("crescent.ui")
ui.List()
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
List:addItem(text: string)
```

Adds one item at the end.

### `addItems`

```lua
List:addItems(list: string[])
```

Adds several items at the end.

### `clear`

```lua
List:clear()
```

Removes every item.

### `focus`

```lua
List:focus()
```

Moves keyboard focus here.

### `getItemAt`

```lua
List:getItemAt(index: integer)
```

The text at a position (from 1), or nil.

### `getItemCount`

```lua
List:getItemCount()
```

How many items there are.

### `getSelectedIndex`

```lua
List:getSelectedIndex()
```

The selected position (from 1), or 0 if none.

### `insertItemAt`

```lua
List:insertItemAt(index: integer, text: string)
```

Inserts an item at a position (from 1).

### `removeItemAt`

```lua
List:removeItemAt(index: integer)
```

Removes the item at a position (from 1).

### `setBackgroundColor`

```lua
List:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setHeight`

```lua
List:setHeight(height: number)
```

Fixed height in dp.

### `setItems`

```lua
List:setItems(list: string[])
```

Replaces every item.

### `setMargins`

```lua
List:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Space around the widget in dp: one value for all sides, two for vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
List:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
List:setMinWidth(width: number)
```

Smallest width in dp.

### `setSelectedIndex`

```lua
List:setSelectedIndex(index: integer)
```

Selects a position (from 1); 0 clears the selection.

### `setSize`

```lua
List:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
List:setWidth(width: number)
```

Fixed width in dp.

## Events

Every handler receives the widget first, then the values listed.

### `setOnItemLongPress`

```lua
List:setOnItemLongPress(function(widget, text: string, index: integer) end)
```

Fired when the user presses and holds an item.

### `setOnItemSelect`

```lua
List:setOnItemSelect(function(widget, text: string, index: integer) end)
```

Fired when the user taps an item.

### `setOnLongPress`

```lua
List:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
List:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
