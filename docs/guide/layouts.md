# Layouts

Layouts hold other widgets. Pick the one whose shape matches what you want.

| Layout | Shape |
|---|---|
| [`Column`](../reference/ui/Column.md) | children top to bottom |
| [`Row`](../reference/ui/Row.md) | children left to right |
| [`Stack`](../reference/ui/Stack.md) | children on top of each other |
| [`Grid`](../reference/ui/Grid.md) | children in a grid |
| [`Scroller`](../reference/ui/Scroller.md) | one child that scrolls |
| [`Flow`](../reference/ui/Flow.md) | children left to right, wrapping onto the next line |
| [`Pager`](../reference/ui/Pager.md) | pages you swipe sideways |
| [`Carousel`](../reference/ui/Carousel.md) | a swipeable row whose items shrink at the edges |
| [`PullToRefresh`](../reference/ui/PullToRefresh.md) | one child that reloads when dragged down |
| [`Card`](../reference/ui/Card.md) | one child on a rounded, raised panel |

Layouts with many children use `addChild`. Layouts with exactly one use `setContent`.

## Column and Row

```lua
local form = ui.Column():setSpacing(8):setMargins(16)
form:addChild(ui.Label("Name"))
form:addChild(ui.TextField())
form:addChild(ui.Button("Save"))
```

`setSpacing` puts space between children; `setMargins` puts space around the layout. Spacing never
changes a child's own margins, so a child with `setMargins` keeps exactly the margins you gave it.

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

A [`Divider`](../reference/ui/Divider.md) is a hairline between things. In a `Row`, stand it up:

```lua
column:addChild(ui.Divider())
row:addChild(ui.Divider():setVertical(true))
```

## Flow

A `Row` pushes its last children off the screen when they do not fit. A
[`Flow`](../reference/ui/Flow.md) carries on underneath instead, which is what a row of tags or
filters wants:

```lua
local tags = ui.Flow():setSpacing(6)
for _, word in ipairs({ "red", "scented", "cut", "potted", "seasonal" }) do
  tags:addChild(ui.Chip(word))
end
```

## Stack

A `Stack` draws its children on top of each other: a badge on a picture, a button over a list.

```lua
local photo = ui.Stack()
photo:addChild(ui.Image("assets/beach.jpg"), "fill")
photo:addChild(ui.Label("New"), "top")
```

The second argument places the child: `"center"`, `"top"`, `"bottom"`, `"left"`, `"right"`, or
`"fill"` to cover the whole stack. Later children are drawn on top.

Two words pick a corner: `"top right"`, `"top left"`, `"bottom right"` or `"bottom left"`. A badge in
the corner of a picture:

```lua
photo:addChild(ui.Label("-20%"), "top right")
```

Anywhere a widget takes an alignment, two words like these work (`setAlign("top right")`).

## Scroller

When the content is taller than the screen, wrap it in a `Scroller`:

```lua
local page = ui.Column()
for i = 1, 100 do page:addChild(ui.Label("Row " .. i)) end
screen:setContent(ui.Scroller():setContent(page))
```

`setHorizontal(true)` scrolls sideways instead: a row of cards.

## Pull to refresh

Wrap a list or a `Scroller` in a [`PullToRefresh`](../reference/ui/PullToRefresh.md) and dragging it
down from the top reloads it. The spinner keeps turning until you say the reload is done:

```lua
local pull = ui.PullToRefresh():setContent(list)
pull:setOnRefresh(function()
  list:setItems(fetchFlowers())
  pull:setRefreshing(false)
end)
```

## Pager

A `Pager` shows one page at a time and lets the user swipe between them: a banner carousel, a
walkthrough. Give it a height, then add the pages:

```lua
local banner = ui.Pager():setHeight(160):setDots(true)
banner:addChild(ui.Image("assets/sale.jpg"))
banner:addChild(ui.Image("assets/new.jpg"))
banner:addChild(ui.Image("assets/gift.jpg"))
banner:setOnSelect(function(_, index) print("now on page", index) end)
```

`setDots(true)` draws small dots beneath the pages, one per page, with the open page highlighted.
The dots follow the app's theme colours. `setOnSelect` runs when a different page comes into view.
A `Pager` needs `setHeight`; without one it has nothing to size itself by.

`setPeek(24)` shows the edge of the next page, so it is clear there is more. `setVertical(true)`
swipes up and down instead of sideways. `setAutoAdvance(5)` moves on by itself every five seconds,
wrapping round at the end; `setAutoAdvance(0)` stops it.

## Carousel

A [`Carousel`](../reference/ui/Carousel.md) is a row the user swipes along where the items at the
edges shrink and clip instead of being cut off: a gallery, a shelf of cards.

```lua
local shelf = ui.Carousel():setHeight(180):setItemWidth(160)
for _, flower in ipairs(flowers) do
  shelf:addChild(ui.Image(flower.photo))
end
shelf:setOnItemSelect(function(_, index) openFlower(index) end)
```

`setLayout` picks how the items are sized: `"browse"` (the default) shows several at once, `"hero"`
one big one with the next peeking, and `"full"` one at a time.

## Card

```lua
local card = ui.Card():setCornerRadius(16)
card:setContent(ui.Column():addChild(ui.Label("Brunch this weekend?")))
card:setOnClick(function() ... end)
```

A card's `setMargins` is the space *inside* it, around its content.

A card has no outline. `setOutlined(true)` draws a thin one. `setAlign` places the content inside
the card: `"center"` centres it, and two words such as `"top right"` work too. The default,
`"fill"`, stretches it across the card's width.

```lua
local tile = ui.Card():setOutlined(true):setAlign("center")
```

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
