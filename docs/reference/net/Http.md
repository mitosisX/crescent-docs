# Http

`crescent.net` · Fetches things from the web. The script waits for the answer without the screen freezing.

## Functions

### `delete`

```lua
Http.delete(url: string, options?: table) --> Response
```

Asks a server to delete something.

### `download`

```lua
Http.download(url: string, path: string, options?: table) --> Response
```

Saves what a server sends straight to a file, so a big file never sits in memory. The response's text is the file's path.

### `get`

```lua
Http.get(url: string, options?: table) --> Response
```

Fetches a page or a file and hands back what the server said.

### `post`

```lua
Http.post(url: string, body: string, options?: table) --> Response
```

Sends text (often JSON) to a server. Set the content type in the headers if it matters.

### `postForm`

```lua
Http.postForm(url: string, fields: table, options?: table) --> Response
```

Sends a table of fields the way a web form does, for logging in and the like.

### `put`

```lua
Http.put(url: string, body: string, options?: table) --> Response
```

Replaces something on a server.

### `request`

```lua
Http.request(method: string, url: string, body?: string, options?: table) --> Response
```

Any other method ("PATCH", "HEAD"), when get and post are not enough.

### `upload`

```lua
Http.upload(url: string, path: string, options?: table) --> Response
```

Sends a file to a server the way a web form does. The options table may add `field` (the name the server expects, "file" by default) and `fields` (a table of plain values sent beside it).
