# Service

`crescent.sys` · Runs the project's background.lua with no screen, behind a notification.

## Functions

### `isRunning`

```lua
Service.isRunning() --> boolean
```

Whether the background script is running.

### `start`

```lua
Service.start(title?: string, text?: string, script?: string)
```

Starts background.lua (or another file by name) behind a notification saying title and text. Starting it again only changes the words.

### `stop`

```lua
Service.stop()
```

Stops it. The script sees service:isStopping() turn true and then its world closes.
