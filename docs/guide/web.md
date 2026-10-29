# The web

[`crescent.net`](../reference/net/Http.md) fetches things. Like everything else that takes time in
Crescent, it simply waits: the answer comes back on the next line, and the screen keeps working
while your script waits for it.

```lua
local net = require("crescent.net")

local answer = net.Http.get("https://example.com")
print(answer:getStatus())      -- 200
print(answer:getText())        -- the page
```

## An answer is not a mistake

A server saying "not found" has answered you. You get a [`Response`](../reference/net/Response.md)
with `getStatus()` of 404, and `isOk()` false. Only a failure to talk at all — no network, an
address that does not exist, a server that never replies — raises an error, at the line that asked
for it:

```lua
local answer = net.Http.get(url)
if answer:isOk() then
  show(answer:getText())
else
  ui.Dialogs.alert("No luck", "The server said " .. answer:getStatus())
end
```

So check `isOk()` for the server's verdict, and wrap the call in `pcall` if you want to survive a
flight-mode phone:

```lua
local ok, answer = pcall(net.Http.get, url)
if not ok then
  ui.Snackbar.show("No connection")
end
```

## Sending something

```lua
net.Http.post(url, '{"name":"Ada"}', { headers = { ["Content-Type"] = "application/json" } })

net.Http.postForm(url, { user = "ada", pass = secret })   -- like a web form
```

`put`, `delete` and `request` are there for the rest; `request("PATCH", url, body)` takes any
method.

Every call takes the same options table, and all of it is optional:

| Option | What it does |
|---|---|
| `headers` | a table of name to value |
| `timeout` | milliseconds to wait before giving up (15000 by default) |
| `userAgent` | what to call yourself |

Headers come back the same way, by name, in any case: `answer:getHeader("Content-Type")`.

## Files, in and out

`download` writes straight to a file, so something big never sits in memory. The response's text
is the path it wrote:

```lua
local saved = net.Http.download("https://example.com/report.pdf", "downloads/report.pdf")
print(saved:getText())                        -- where it went
print(fs.getFileSize("downloads/report.pdf"))
```

`upload` sends a file the way a web form does. `field` names what the server expects, and `fields`
are plain values sent beside it:

```lua
net.Http.upload(url, "photos/cat.jpg", { field = "photo", fields = { caption = "my cat" } })
```

## Pictures

An [`Image`](../reference/ui/Image.md) takes an address as happily as a path. It fills itself in
when the picture arrives, so your screen can be up before it does:

```lua
local photo = ui.Image()
photo:setScale("crop")
photo:setOnLoad(function() spinner:setVisible(false) end)
photo:setSource("https://example.com/cat.jpg")
```

Each address is kept in the phone's cache for a week, so going back to a screen shows the picture
at once and asks the network for nothing. `ui.Image.setCacheSeconds(0)` keeps it for good;
a smaller number for pictures that change.

## Doing it off the screen

A fetch inside a handler is fine — the screen keeps working. But if you have fifty of them, or
some heavy work to do with what comes back, move the whole job off the screen's thread with
[`sys.Task`](background.md).

## Two things to know

- A built app gets the internet permission because your script asks for the web. Nothing to set up.
- Plain `http://` addresses work, not only `https://`.
