# Notify

`crescent.sys` · Shows a line in the phone's notification shade.

## Functions

### `hide`

```lua
Notify.hide(id: integer)
```

Takes a notification away again, by the number show() handed back.

### `show`

```lua
Notify.show(title: string, text?: string) --> integer
```

Shows a notification and hands back its number, for hide(). Returns 0 when the user has not allowed notifications, having just been asked.
