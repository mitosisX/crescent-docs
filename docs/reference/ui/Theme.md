# Theme

`crescent.ui` · The app's colours: one call at the top of your script sets them for every widget.

## Functions

### `clear`

```lua
Theme.clear()
```

Drops the app's own colours and goes back to the phone's.

### `isDarkMode`

```lua
Theme.isDarkMode()
```

Whether the dark half of the theme is showing.

### `set`

```lua
Theme.set(theme: table)
```

Sets the app's colours. Pass { color = "#805610" } to grow the whole theme from one colour, or { light = { primary = "#805610", ... }, dark = { ... } } for colours you already have, or both to start from a colour and change a few roles.

### `setDarkMode`

```lua
Theme.setDarkMode(dark: boolean|string)
```

Chooses the half of the theme to show: true for dark, false for light, "auto" (the default) to follow the phone.
