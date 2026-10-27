# Timer

`crescent.sys` · Calls a function every interval milliseconds while started.

## Create

```lua
local sys = require("crescent.sys")
sys.Timer(interval?: integer)
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `interval` | `integer` | Milliseconds between ticks |

## Methods

### `isRunning`

```lua
Timer:isRunning()
```

Whether the timer is ticking.

### `start`

```lua
Timer:start()
```

Starts ticking.

### `stop`

```lua
Timer:stop()
```

Stops ticking.

## Functions

### `singleShot`

```lua
Timer.singleShot(msec: integer, callback: function)
```

Calls a function once after msec milliseconds.

## Events

Every handler receives the widget first, then the values listed.

### `setOnTick`

```lua
Timer:setOnTick(function(widget) end)
```

Fired every interval while started.
