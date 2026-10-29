# Samples

The Player's **Samples** tab has these apps. Open one to read it, tap Run to try it, or copy it into
your projects to change it.

## Reply

Google's Material 3 mail app, rebuilt with Crescent's widgets: an inbox of email cards with round
avatars and star buttons, a search field, a floating Compose button that shrinks as you scroll, a
bottom navigation bar, and a thread screen. Long-press a card to select it. Turn the phone sideways
and the list and the thread sit side by side.

Shows: [an app's own colours](guide/styling.md#your-apps-colours) (Reply's amber, both halves, in
`theme.lua`), [theme roles](guide/styling.md), [text roles](guide/styling.md#text-roles),
[icons](guide/icons.md), [`NavigationBar`](reference/ui/NavigationBar.md),
[`setOnResize`](guide/layouts.md#sizes) and [`setOnScroll`](guide/screens.md#the-floating-button).

## Flower shop

A real shop design rebuilt in Lua: a splash screen, a login over a photo, then the shop home with a
swipeable banner, categories, a sideways list of popular bouquets and a floating bottom bar. The
cart and checkout are not built yet.

Shows: [`Pager`](guide/layouts.md#pager), [`Stack`](guide/layouts.md#stack) with corner placement,
sideways [`Scroller`](guide/layouts.md#scroller), [outlined cards](guide/styling.md#cards-and-buttons),
pill buttons, [`setStatusBarColor`](guide/screens.md#status-bar-colour), per-corner radius, and
bundled fonts.

## Dog photos

One picture from the web, fetched again whenever you ask. Short enough to read in a minute, and the
point is that nothing in it is a callback: the fetch waits on its own line and the screen keeps
moving.

Shows: [the web](guide/web.md), a [picture from an address](guide/web.md#pictures), and
[`Image`](reference/ui/Image.md) corners and scaling.

## Notes

A list of notes, one text file each. Tap a note to edit it on its own screen; Back saves it.

Shows: [screens](guide/screens.md), [files](guide/files.md), and
[waiting for a dialog](guide/waiting.md).

## To-do

A to-do list with checkboxes, saved between runs.

## Widgets

Every widget on one screen, to see how each one looks and behaves.
