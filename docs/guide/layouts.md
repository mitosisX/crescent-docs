# Layouts

Layouts hold other widgets. Pick the one whose shape matches what you want.

| Layout | Shape |
|---|---|
| [`Column`](../reference/ui/Column.md) | children top to bottom |
| [`Row`](../reference/ui/Row.md) | children left to right |
| [`Stack`](../reference/ui/Stack.md) | children on top of each other |
| [`Grid`](../reference/ui/Grid.md) | children in a grid |
| [`Scroller`](../reference/ui/Scroller.md) | one child that scrolls |
| [`Card`](../reference/ui/Card.md) | one child on a rounded, raised panel |

Layouts with many children use `addChild`. Layouts with exactly one use `setContent`.

## Column and Row

```lua
local form = ui.Column():setSpacing(8):setMargins(16)
form:addChild(ui.Label("Name"))
form:addChild(ui.TextField())
form:addChild(ui.Button("Save"))
```

`setSpacing` puts space between children; `setMargins` puts space around the layout.

### Sharing the space

Give `addChild` a second number to let a child take the spare room:

```lua
local bar = ui.Row():setAlign("vcenter")
bar:addChild(ui.Label("Total"), 1)   -- takes all the spare width
bar:addChild(ui.Label("$42"))        -- only as wide as it needs
```

Two children with `1` share the spare room equally; `2` takes twice as much as `1`.

`addSpace(16)` adds a fixed gap. `addStretch()` adds a gap that grows, which pushes what follows to
the far end.

## Stack

A `Stack` draws its children on top of each other: a badge on a picture, a button over a list.

```lua
local photo = ui.Stack()
photo:addChild(ui.Image("assets/beach.jpg"), "fill")
photo:addChild(ui.Label("New"), "top")
```

The second argument places the child: `"center"`, `"top"`, `"bottom"`, `"left"`, `"right"`, or
`"fill"` to cover the whole stack. Later children are drawn on top.

## Scroller

When the content is taller than the screen, wrap it in a `Scroller`:

```lua
local page = ui.Column()
for i = 1, 100 do page:addChild(ui.Label("Row " .. i)) end
screen:setContent(ui.Scroller():setContent(page))
```

`setHorizontal(true)` scrolls sideways instead: a row of cards, a carousel.

## Card

```lua
local card = ui.Card():setCornerRadius(16)
card:setContent(ui.Column():addChild(ui.Label("Brunch this weekend?")))
card:setOnClick(function() ... end)
```

A card's `setMargins` is the space *inside* it, around its content.

## Sizes

Every size is in **dp**, the unit Android uses so things look the same size on every screen.
`setWidth`, `setHeight` and `setSize` fix a widget's size; without them it is as big as its content.

`sys.System.getScreenWidth()` gives the screen's width in dp. To react when it changes (the phone
turns, a foldable opens), use `setOnResize`:

```lua
root:setOnResize(function(_, width, height)
  if width > 600 then showTwoPanes() else showOnePane() end
end)
```
