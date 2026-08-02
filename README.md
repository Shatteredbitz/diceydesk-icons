# Dicey Desk — Steam inventory icons

Public asset host for the Steam Inventory Service. Nothing here is source code; the game lives in a
private repository.

Steam does not host item images. An itemdef carries an `icon_url`, and Valve **fetches that URL and
caches the result**, which is why these have to be publicly reachable — and why the filenames must
never change once published.

## Naming

    icons/<die>_<theme>.png       512 px, icon_url_large
    icons/<die>_<theme>_sm.png    200 px, icon_url

e.g. `icons/d20_kifs.png`. Named by **identity, not by itemdefid**: ids are an allocation detail that
can be re-issued, and a URL that moved when an id moved would break every itemdef already published.

## Why the dice are colourless

Colour, numeral ink and border are **per-item tags**, not part of the itemdef. One itemdef covers all
twelve colourways, so every owner of it shares this single picture — painting it in one hue would
make it wrong for the other eleven. The icon shows the shape and the theme, which is all the itemdef
actually determines. Colour reaches the buyer as a row on the item card instead.

Themes whose colours *are* their identity — the flags, and the raymarched orbs — keep them, because
for those the colour is not a colourway.

Shells are neutral per tier rather than one flat grey (`#6f7075` Common through `#ccced6`
Legendary), so a grid of icons reads as a rarity ladder before a single name is read.

## Replacing an icon

Valve caches on first fetch. A corrected picture at the same URL will **not** appear. Replacing one
means publishing it under a new filename and updating `icon_url` on every affected itemdef.

## Regenerating

`DeskDice/Icons/Render ALL Dice Icons` in the Unity project. 210 itemdefs at two sizes.
