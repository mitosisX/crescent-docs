# System

`crescent.sys` · System information and helpers.

## Functions

### `getClipboardText`

```lua
System.getClipboardText()
```

The clipboard's text, or an empty string.

### `getOSName`

```lua
System.getOSName()
```

Always "Android".

### `getOSVersion`

```lua
System.getOSVersion()
```

The Android version, e.g. "14".

### `getScreenHeight`

```lua
System.getScreenHeight()
```

The screen's height in dp.

### `getScreenWidth`

```lua
System.getScreenWidth()
```

The screen's width in dp, the unit every size in the API uses.

### `getStandardPath`

```lua
System.getStandardPath(name: string)
```

A standard folder: "data", "cache", "documents" or "external".

### `isDarkMode`

```lua
System.isDarkMode()
```

True when the phone is in dark mode.

### `randomChoice`

```lua
System.randomChoice(items: string[])
```

One item picked at random.

### `setClipboardText`

```lua
System.setClipboardText(text: string)
```

Copies text to the clipboard.

### `sleep`

```lua
System.sleep(ms: integer)
```

Waits this many milliseconds without freezing the screen.

### `splitString`

```lua
System.splitString(text: string, separator: string)
```

Splits text on a separator.

### `vibrate`

```lua
System.vibrate(ms?: integer)
```

Buzzes the phone for this many milliseconds.
