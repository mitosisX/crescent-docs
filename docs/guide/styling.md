# Colours and text

## Colours

Anywhere a colour goes, you can pass:

| You write | Meaning |
|---|---|
| `"#1BA57B"`, `"#fff"`, `"#801BA57B"` | a hex colour (with alpha in the last form) |
| `"red"`, `"white"`, `"transparent"` | a colour name |
| `"primary"`, `"surfaceContainerHigh"` | a **theme role** |

### Theme roles

Roles are the colours of Material 3, Android's design system. Use them and your app looks right in
both light and dark mode, without any extra work:

```lua
card:setBackgroundColor("surfaceVariant")
title:setTextColor("onSurfaceVariant")
selected:setBackgroundColor("primaryContainer")
```

The roles come in pairs: a background and the colour for things on it.

| Background | Things on it |
|---|---|
| `primary` | `onPrimary` |
| `primaryContainer` | `onPrimaryContainer` |
| `secondary`, `secondaryContainer` | `onSecondary`, `onSecondaryContainer` |
| `tertiary`, `tertiaryContainer` | `onTertiary`, `onTertiaryContainer` |
| `error`, `errorContainer` | `onError`, `onErrorContainer` |
| `surface`, `surfaceVariant` | `onSurface`, `onSurfaceVariant` |
| `surfaceContainerLowest` … `surfaceContainerHighest` | `onSurface` |

Also: `background`, `onBackground`, `surfaceDim`, `surfaceBright`, `outline`, `outlineVariant`,
`inverseSurface`, `inverseOnSurface`, `inversePrimary`. A misspelt role tells you the one you meant.

`sys.System.isDarkMode()` says whether the phone is in dark mode.

## Gradients

Every widget takes `setGradient(from, to)`: two [colours](#colours) and, if you like, a direction.

```lua
header:setGradient("#ff8a00", "#ff0058", "down right")
ui.Button("Order now"):setCornerRadius(28):setGradient("primary", "tertiary", "right")
```

The direction is `"down"` (the default), `"up"`, `"left"`, `"right"`, or two words for a diagonal:
`"down right"`, `"up left"`. `"out"` spreads a circle from the middle and `"around"` sweeps round.
A `Card` keeps its rounded shape, and a `Button` keeps its corners.

## Badges

`setBadge` puts the little count over a widget's top right corner: a number, a short piece of text,
or `0` to take it away.

```lua
ui.IconButton("mail", "Mail"):setBadge(3)
ui.IconButton("notifications", "Alerts"):setBadge("9+")
```

A bottom bar badges its own items: `nav:setItemBadge(1, 3)`.

## Text

### Text roles

Material 3 also names its text styles. One call sets size, weight and spacing:

```lua
ui.Label("Brunch this weekend?"):setTextRole("titleMedium")
ui.Label("Ali · 40 mins ago"):setTextRole("labelMedium")
```

The roles are `display`, `headline`, `title`, `body` and `label`, each `Large`, `Medium` or `Small`.
Set the role first, then any `setTextSize` or `setBold`, because a role replaces them. It keeps your
text colour and font.

### By hand

```lua
label:setTextSize(18):setBold(true):setTextColor("primary"):setTextAlignment("center")
label:setFont("assets/fonts/JosefinSans.ttf")
label:setMaxLines(2)   -- cut with "…" after two lines; 0 means no limit
```

## setStyle

For quick styling there is a small CSS subset:

```lua
badge:setStyle("background-color: primary; color: onPrimary; padding: 4dp; border-radius: 12dp")
```

It understands `font-size`, `font-weight`, `color`, `background-color`, `padding` and
`border-radius`.

## Cards and buttons

A `Card` has no outline by default; `setOutlined(true)` draws a thin one. If you drew your own border
to get this look, you can drop it.

Material gives buttons five looks, and `setVariant` picks one:

```lua
ui.Button("Buy"):setVariant("filled")      -- the default: solid, for the main action
ui.Button("Save"):setVariant("tonal")      -- softer, for a second action
ui.Button("Share"):setVariant("elevated")
ui.Button("Cancel"):setVariant("outlined")
ui.Button("Learn more"):setVariant("text")
```

`Button:setCornerRadius(dp)` rounds a button's corners. A radius of half the button's height makes a
pill:

```lua
ui.Button("Order now"):setCornerRadius(28)
```

## Rounded corners

`Card`, `Image` and `TextField` take `setCornerRadius`: one value for all corners, two for top then
bottom, or four (top-left, top-right, bottom-right, bottom-left). A picture with a radius of half
its size is a circle:

```lua
ui.Image("assets/avatar.jpg"):setSize(40, 40):setCornerRadius(20)
```
