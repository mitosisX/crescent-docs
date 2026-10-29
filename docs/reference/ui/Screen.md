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
| `statusBarColor` | `string` | The colour behind the status bar while this screen is on top, a "#rrggbb" or a theme role ("" = the theme's own); the icons turn light or dark to read on it |
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
Screen:close(result?: any)
```

Closes the screen and returns to the one under it, handing it a result: whatever a screen was opened to find out (the row the user picked, the text they typed). Closing with Back hands back nothing.

### `closeDrawer`

```lua
Screen:closeDrawer()
```

Slides the drawer away.

### `focus`

```lua
Screen:focus()
```

Moves keyboard focus here.

### `getActionCount`

```lua
Screen:getActionCount() --> integer
```

How many actions the top bar has.

### `getBadge`

```lua
Screen:getBadge() --> string
```

What the badge shows, or "" if there is none.

### `getBarSize`

```lua
Screen:getBarSize() --> string
```

The bar size set with setBarSize.

### `getMenu`

```lua
Screen:getMenu() --> string[]
```

The widget's menu items.

### `isDrawerOpen`

```lua
Screen:isDrawerOpen() --> boolean
```

Whether the drawer is out.

### `openDrawer`

```lua
Screen:openDrawer()
```

Slides the drawer out.

### `openMenu`

```lua
Screen:openMenu()
```

Opens the widget's menu, as a long press would.

### `setBackgroundColor`

```lua
Screen:setBackgroundColor(color: string|integer)
```

Background colour: "#rrggbb", a name like "red", a theme role like "primaryContainer", or an ARGB integer.

### `setBadge`

```lua
Screen:setBadge(value: integer|string|nil)
```

Puts a badge over the widget's top right corner: a number (0 removes it), a short piece of text, or nil to remove it.

### `setBarSize`

```lua
Screen:setBarSize(name: string)
```

How tall the top bar is: "small" (the default), "medium" or "large". A tall bar gives the title its own room, the way Settings and Photos do.

### `setContent`

```lua
Screen:setContent(content: any)
```

Sets what the screen shows (usually a layout).

### `setDrawer`

```lua
Screen:setDrawer(panel: any)
```

Puts a panel behind the left edge that slides out when the user taps the top bar's menu icon or drags from the edge. Needs a title, since the icon lives in the top bar.

### `setFab`

```lua
Screen:setFab(fab: any)
```

Puts a Fab over the content, bottom right.

### `setGradient`

```lua
Screen:setGradient(from: string|integer, to: string|integer, direction?: string)
```

Fills the background with a gradient from one colour to another. The direction is "down" (the default), "up", "left", "right", "down right", "down left", "up right", "up left", "out" for a circle spreading from the middle, or "around" for a sweep.

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

### `setMenu`

```lua
Screen:setMenu(items: string[])
```

Gives the widget a menu that opens on a long press. Replaces setOnLongPress; an empty list removes it.

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

### `setOnClick`

```lua
Screen:setOnClick(function(widget) end)
```

Fired when the widget is tapped. A tap on a widget with its own touch handling (a text field's text area, a slider's track, a list's items) goes to that widget, so this fires only outside it: use its own event (setOnTextChange, setOnValueChange, setOnItemSelect).

### `setOnClose`

```lua
Screen:setOnClose(function(widget, result: any) end)
```

Fired when the screen closes, with the result close() was given (nothing, when the user pressed Back).

### `setOnLongPress`

```lua
Screen:setOnLongPress(function(widget) end)
```

Fired when the user presses and holds the widget.

### `setOnMenuSelect`

```lua
Screen:setOnMenuSelect(function(widget, item: string, index: integer) end)
```

Fired with (item, index) when the user picks something from the widget's menu.

### `setOnResize`

```lua
Screen:setOnResize(function(widget, width: integer, height: integer) end)
```

Fired with (width, height) in dp on the first layout and whenever the size changes: rotation, unfolding, setSize.
