# Icons

Crescent ships the full **Material Icons** set, over two thousand icons, by name. Find a name at
[fonts.google.com/icons](https://fonts.google.com/icons?icon.set=Material+Icons) and use it as
written there, with underscores: `star_border`, `arrow_back`, `chat_bubble_outline`.

```lua
ui.Icon("inbox")                                   -- an icon on its own
ui.IconButton("star_border", "Favourite")          -- a round button that is just an icon
ui.Button("Compose"):setIcon("edit")               -- an icon beside the text
ui.Fab("Compose"):setIcon("edit")
screen:addAction("more_vert", "More options", fn)  -- in the top bar
nav:addItem("inbox", "Inbox", page)                -- in a bottom bar
field:setLeadingIcon("search")                     -- inside a text field
```

A misspelt name says which one you meant: `ui.Icon("inbx")` → *did you mean 'inbox'*.

## Colour and size

```lua
ui.Icon("check"):setTint("onPrimary"):setIconSize(18)
```

`setTint(nil)` goes back to the theme's colour. Icons in buttons, bars and fields follow the
theme on their own, including the selected and disabled states.

## Descriptions

An icon on its own says nothing to someone using TalkBack. Give tappable icons a description:
`IconButton` and `addAction` take one, and every widget has `setDescription`.

!!! tip "Tap targets"
    A plain `ui.Icon` is only as big as the icon. For something to tap, use `ui.IconButton`, which
    has a finger-sized touch area.
