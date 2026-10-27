# Dialogs

`crescent.ui` · Dialogs. Each waits for the user, then returns the answer.

## Functions

### `alert`

```lua
Dialogs.alert(title: string, message: string)
```

A message with an OK button. Waits until it is dismissed.

### `confirm`

```lua
Dialogs.confirm(title: string, message: string)
```

Asks a yes/no question; returns true for Yes.

### `pickDate`

```lua
Dialogs.pickDate(title?: string?, date?: string?)
```

Shows a date picker; returns the chosen date as "YYYY-MM-DD", or nil if cancelled. `date` is the starting date in the same form (default today).

### `prompt`

```lua
Dialogs.prompt(title: string, label: string, text?: string)
```

Asks for a line of text; returns it, or nil if cancelled.

### `toast`

```lua
Dialogs.toast(message: string)
```

A short message at the bottom of the screen. Does not wait.
