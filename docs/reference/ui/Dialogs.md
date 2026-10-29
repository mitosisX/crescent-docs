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
Dialogs.confirm(title: string, message: string) --> boolean
```

Asks a yes/no question; returns true for Yes.

### `pickDate`

```lua
Dialogs.pickDate(title?: string?, date?: string?) --> string?
```

Shows a date picker; returns the chosen date as "YYYY-MM-DD", or nil if cancelled. `date` is the starting date in the same form (default today).

### `pickTime`

```lua
Dialogs.pickTime(title?: string?, time?: string?) --> string?
```

Shows a time picker; returns the chosen time as "HH:MM" on a 24 hour clock, or nil if cancelled. `time` is the starting time in the same form (default now). The dial itself follows the phone's 12 or 24 hour setting.

### `prompt`

```lua
Dialogs.prompt(title: string, label: string, text?: string) --> string?
```

Asks for a line of text; returns it, or nil if cancelled.

### `toast`

```lua
Dialogs.toast(message: string)
```

A short message at the bottom of the screen. Does not wait.
