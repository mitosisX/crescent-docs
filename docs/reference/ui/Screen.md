# Screen

`crescent.ui` · A screen of the app. show() displays it; showing another stacks it and Back returns. A title adds a top bar.

## Create

```lua
local ui = require("crescent.ui")
ui.Screen(options?: table?)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `description` | `string` | What a screen reader says for this widget, and the tip shown on a long press nobody handles |
| `enabled` | `boolean` | Whether the widget reacts to touch |
| `style` | `string` | A CSS subset: font-size, font-weight, color, background-color, padding, border-radius |
| `subtitle` | `string` | A smaller line under the title |
| `title` | `string` | The top bar's title (no title, no bar) |
| `visible` | `boolean` | Whether the widget is shown |

## Methods

### `addAction`

```lua
Screen:addAction(icon: string, description: string, onTap: function)
```

Adds an icon at the right of the top bar. The description is what TalkBack reads, and the label if it folds into the overflow menu.

### `clearActions`

```lua
Screen:clearActions()
```

Removes every top bar action.

### `close`

```lua
Screen:close()
```

Closes the screen and returns to the one under it.

### `focus`

```lua
Screen:focus()
```

Moves keyboard focus here.

### `getActionCount`

```lua
Screen:getActionCount()
```

How many actions the top bar has.

### `setBackgroundColor`

```lua
Screen:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setContent`

```lua
Screen:setContent(content: any)
```

Sets what the screen shows (usually a layout).

### `setFab`

```lua
Screen:setFab(fab: any)
```

Puts a Fab over the content, bottom right.

### `setHeight`

```lua
Screen:setHeight(height: number)
```

Fixed height in dp.

### `setMargins`

```lua
Screen:setMargins(left: number, top?: number, right?: number, bottom?: number)
```

Inner padding in dp: one value, vertical and horizontal, or left, top, right, bottom.

### `setMinHeight`

```lua
Screen:setMinHeight(height: number)
```

Smallest height in dp.

### `setMinWidth`

```lua
Screen:setMinWidth(width: number)
```

Smallest width in dp.

### `setSize`

```lua
Screen:setSize(width: number, height: number)
```

Fixed width and height in dp.

### `setWidth`

```lua
Screen:setWidth(width: number)
```

Fixed width in dp.

### `show`

```lua
Screen:show()
```

Shows the screen, on top of any screen already shown.

## Events

Every handler receives the widget first, then the values listed.

### `setOnClose`

```lua
Screen:setOnClose(function(widget) end)
```

Fired when the screen closes (Back or close()).

### `setOnLongPress`

```lua
Screen:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnResize`

```lua
Screen:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
