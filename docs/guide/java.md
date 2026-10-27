# Using Android directly

Crescent's API covers the common things. For everything else, Lua can reach any Java or Kotlin
class on the phone.

```lua
local Build = java.import("android.os.Build")
print(Build.MODEL, Build.VERSION.RELEASE)

local StringBuilder = java.import("java.lang.StringBuilder")
local sb = StringBuilder()          -- call a class to construct it
sb:append("Hello, "):append("Lua")
print(sb:toString())
```

## The rules

- `java.import("full.class.Name")` gives you the class. Nested classes use `$`:
  `java.import("android.os.Build$VERSION")`.
- Call the class like a function to make one: `ArrayList()`.
- Methods use `:`, static methods too: `String:format("%s=%d", "x", 5)`.
- Fields and constants use `.`: `Build.MODEL`.
- Lua numbers, strings, booleans and `nil` convert to Java and back on their own. When a method
  has several versions, Crescent picks the one your arguments fit.
- Lua tables are not Java lists. Use `java.array("string", { "a", "b" })` to make an array, and
  `java.totable(list)` to turn a Java array or list into a Lua table.

## Widgets are Android views

Every Crescent widget *is* an Android view, so its Java methods work too:

```lua
local label = ui.Label("Hello")
print(label:getCurrentTextColor())   -- android.widget.TextView's own method
```

## Interfaces

Where Java wants an interface (a listener, a `Runnable`), pass a Lua function or a table of
functions, and Crescent wraps it.

!!! warning
    Android's own classes change between versions. Code that uses them directly can break on an
    older or newer phone where the Crescent API would not. Prefer the API where it has what you
    need.
