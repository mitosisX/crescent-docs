# Response

`crescent.net` · What a server sent back. net.Http hands you one; you never make one yourself.

## Create

```lua
local net = require("crescent.net")
net.Response()
```

## Properties

Each property has a getter and a setter: `getName()` / `setName(value)`; booleans also read as `isName()`. Setters return the widget, so calls chain.

| Property | Type | What it is |
|---|---|---|
| `ok` | `boolean` | True when the status is 200 to 299 (read only) |
| `status` | `integer` | The HTTP status: 200 when all went well, 404 when the page is not there, 0 when nothing answered (read only) |
| `text` | `string` | The body as text (read only) |
| `url` | `string` | The address that answered, after any redirect (read only) |

## Methods

### `getHeader`

```lua
Response:getHeader(name: string) --> string
```

One header the server sent, by name (upper or lower case), or an empty string.

### `getHeaderNames`

```lua
Response:getHeaderNames() --> string[]
```

The names of every header the server sent.
