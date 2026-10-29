# Task

`crescent.sys` · Runs one of the project's script files off the screen's thread, in its own Lua world.

## Create

```lua
local sys = require("crescent.sys")
sys.Task(script: string)
```

## Methods

### `isRunning`

```lua
Task:isRunning() --> boolean
```

Whether the task is running.

### `start`

```lua
Task:start(args: any)
```

Starts the file, handing it these values as its ... (text, numbers and true/false only).

### `stop`

```lua
Task:stop()
```

Asks the task to stop. The file sees task:isStopping() turn true; a file that never checks runs to its end.

## Events

Every handler receives the widget first, then the values listed.

### `setOnDone`

```lua
Task:setOnDone(function(widget, result: any) end)
```

Fired when the file reaches its end, with whatever it returned.

### `setOnError`

```lua
Task:setOnError(function(widget, message: string) end)
```

Fired when the file raises an error. Without this, the error goes to the console.

### `setOnMessage`

```lua
Task:setOnMessage(function(widget, value: any) end)
```

Fired for each value the file sends back with task:send(value).
