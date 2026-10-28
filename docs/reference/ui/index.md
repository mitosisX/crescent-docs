# crescent.ui

```lua
local ui = require("crescent.ui")
```

| Name | What it is |
|---|---|
| [Button](Button.md) | A tappable button. |
| [Card](Card.md) | A rounded raised panel holding one widget, usually a Column. |
| [Carousel](Carousel.md) | A swipeable row of items that shrink at the edges, for a gallery or a shelf of cards. Give it a height (setHeight). Positions count from 1. |
| [CheckBox](CheckBox.md) | A box that can be ticked. |
| [Chip](Chip.md) | A small rounded tappable label: a tag, a filter or something the user chose. Put several in a ChipGroup. |
| [ChipGroup](ChipGroup.md) | Chips in rows that wrap onto the next line. Positions count from 1. |
| [Column](Column.md) | Stacks widgets top to bottom. |
| [Dialogs](Dialogs.md) | Dialogs. Each waits for the user, then returns the answer. |
| [Divider](Divider.md) | A thin line between things. In a Row, setVertical(true) makes it stand up. |
| [Dropdown](Dropdown.md) | A drop-down list. Positions count from 1. |
| [Fab](Fab.md) | A floating action button, for a screen's main action. Screen:setFab puts it bottom right. |
| [Flow](Flow.md) | Children side by side, carrying on to the next line when the line is full. |
| [Grid](Grid.md) | Places widgets in rows and columns, counted from 1. Columns share the width equally. |
| [Icon](Icon.md) | A Material icon picked by name, such as "inbox" or "star_border". |
| [IconButton](IconButton.md) | A round button that shows only an icon, such as "star_border". Give it a description for screen readers. |
| [Image](Image.md) | Shows a picture from the app's files or assets. |
| [Label](Label.md) | Shows text. |
| [List](List.md) | A scrolling list of text items. Positions count from 1. |
| [NavigationBar](NavigationBar.md) | A bar of icon items along the bottom, each showing its own widget above it. Positions count from 1. |
| [NumberPicker](NumberPicker.md) | A number with - and + buttons (for a list of choices use Dropdown). |
| [Pager](Pager.md) | Pages you swipe through, one child per page, with optional dots. Give it a height (setHeight): pages fill the Pager. Positions count from 1. |
| [ProgressBar](ProgressBar.md) | A bar showing progress (default 0..100), or a spinning one while you wait. |
| [PullToRefresh](PullToRefresh.md) | Holds a list or a Scroller and reloads it when the user drags down from the top. Set refreshing to false when the reload is done. |
| [RadioButton](RadioButton.md) | One choice in a RadioGroup; picking it clears the others. |
| [RadioGroup](RadioGroup.md) | Holds RadioButtons so only one is picked at a time. Positions count from 1. |
| [Row](Row.md) | Lines widgets up left to right; they share the width equally. |
| [Screen](Screen.md) | A screen of the app. show() displays it; showing another stacks it and Back returns. A title adds a top bar. |
| [Scroller](Scroller.md) | Scrolls one child (usually a layout) when it is bigger than the screen: down the page, or sideways for a row of cards. |
| [SearchBar](SearchBar.md) | A rounded bar the user types a search into. setOnTextChange filters as they type; setOnSubmit fires when they press the keyboard's search key. |
| [SegmentedButton](SegmentedButton.md) | A row of joined buttons where one is chosen, for two to five short choices. Positions count from 1. |
| [Sheet](Sheet.md) | A panel that slides up from the bottom over the screen. show() opens it; dragging it down, tapping outside or close() dismisses it. |
| [Slider](Slider.md) | A draggable bar choosing a whole number in a range (default 0..100). |
| [Snackbar](Snackbar.md) | A short message at the bottom of the screen, with an optional button. |
| [Stack](Stack.md) | Draws children on top of each other: a background behind content, a badge over a picture. |
| [Switch](Switch.md) | An on/off switch, for settings. |
| [Tabs](Tabs.md) | A row of tabs, each showing its own widget underneath. Positions count from 1. |
| [TextArea](TextArea.md) | A multi-line text field, in a Material box with a floating label. |
| [TextField](TextField.md) | A one-line text field, in a Material box with a floating label. |
| [Theme](Theme.md) | The app's colours: one call at the top of your script sets them for every widget. |
