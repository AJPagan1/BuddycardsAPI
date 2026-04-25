# BuddycardsJS

![Minecraft](https://img.shields.io/badge/Minecraft-1.20.1-brightgreen)
![Forge](https://img.shields.io/badge/Forge-47.4.10-orange)
![Status](https://img.shields.io/badge/status-stable-success)
![Data Driven](https://img.shields.io/badge/system-data--driven-blue)

BuddycardsJS is a **data-driven extension for Buddycards** that lets you create full Buddycards-style content using JSON and textures.

This README documents the full non-battle feature set, including:

- sets
- cards
- packs
- binders
- booster boxes
- medals
- structure loot injection
- generated recipes, models, tags, and language files

---

## Requirements

Install all of these:

- Minecraft **1.20.1**
- Forge **47.4.10**
- Buddycards
- KubeJS
- Curios
- BuddycardsJS

---

## What BuddycardsJS Does

BuddycardsJS reads JSON files from your `kubejs` folder and generates the files needed to make your content work in-game.

It can automatically generate:

- item models
- block models
- blockstates
- `en_us.json`
- crafting recipes
- card tags
- Curios medal tags
- loot modifier files
- injected loot tables

---

## Folder Structure

### Data

Put JSON files here:

```text
kubejs/data/<namespace>/buddyinfo/
```

Supported folders:

```text
sets/
cards/
packs/
binders/
booster_boxes/
medals/
loot_injections/
```

### Assets

Put textures here:

```text
kubejs/assets/<namespace>/textures/
```

Supported folders:

```text
item/<set_path>/
block/<set_path>/
gui/
```

---

## Namespace Rules

Your namespace comes from the folder under `kubejs/data`.

Example:

```text
kubejs/data/example/buddyinfo/
```

This means your ids will be things like:

- `example:example_set`
- `example:buddycard_example`
- `example:buddycard_pack_example`
- `example:buddycard_binder_example`
- `example:buddycard_booster_box_example`
- `example:buddycard_medal_example`

Always use the correct namespace in your JSON references.

---

## Sets

Path:

```text
kubejs/data/<namespace>/buddyinfo/sets/<set_name>.json
```

### Full layout

```json
{
  "displayName": "Example Set",
  "description": "An example BuddycardsJS set.",
  "defaultCardsPerPack": 3,
  "defaultFoilsPerPack": 1
}
```

### Fields

- `displayName` — optional
- `description` — optional
- `defaultCardsPerPack` — optional
- `defaultFoilsPerPack` — optional

### Defaults

- `displayName` defaults from file name
- `defaultCardsPerPack` defaults to `3`
- `defaultFoilsPerPack` defaults to `1`

---

## Cards

Path:

```text
kubejs/data/<namespace>/buddyinfo/cards/<card_name>.json
```

### Full layout

```json
{
  "displayName": "Buddycard Example",
  "set": "example:example_set",
  "number": 1,
  "rarity": "common",
  "cost": 0,
  "power": 0,
  "texturePath": "example_set/buddycard_example",
  "shinyByDefault": false,
  "tooltip": "This is example flavor text."
}
```

### Fields

- `displayName` — optional
- `set` — required
- `number` — optional
- `rarity` — optional
- `cost` — optional
- `power` — optional
- `texturePath` — optional
- `shinyByDefault` — optional
- `tooltip` — optional

### Rarity options

- `common`
- `uncommon`
- `rare`
- `epic`

### Defaults

- `displayName` defaults from file name
- `number` defaults to `1`
- `rarity` defaults to `common`
- `cost` defaults to `0`
- `power` defaults to `0`
- `texturePath` defaults to `<set_path>/<card_name>`
- `shinyByDefault` defaults to `false`

### Card tooltip text

If you provide:

```json
"tooltip": "This is example flavor text."
```

BuddycardsJS generates the language key Buddycards already expects:

```text
item.<namespace>.<card_name>.tooltip
```

So this edits the existing Buddycards tooltip behavior instead of creating a separate custom tooltip system.

### Example texture path

If your JSON file is:

```text
kubejs/data/example/buddyinfo/cards/buddycard_example3.json
```

and your set is:

```json
"set": "example:example_set"
```

the default texture path is:

```text
kubejs/assets/example/textures/item/example_set/buddycard_example3.png
```

If you want a custom file name, use:

```json
"texturePath": "example_set/custom_card_art"
```

which points to:

```text
kubejs/assets/example/textures/item/example_set/custom_card_art.png
```

---

## Packs

Path:

```text
kubejs/data/<namespace>/buddyinfo/packs/<pack_name>.json
```

### Full layout

```json
{
  "displayName": "Buddycard Pack Example",
  "set": "example:example_set",
  "cards": 3,
  "foils": 1,
  "texturePath": "example_set/buddycard_pack_example",
  "rarityWeights": {
    "common": 70,
    "uncommon": 20,
    "rare": 8,
    "epic": 2
  },
  "entries": [
    {
      "card": "example:buddycard_example",
      "weight": 1
    }
  ]
}
```

### Fields

- `displayName` — optional
- `set` — recommended
- `cards` — optional
- `foils` — optional
- `texturePath` — optional
- `rarityWeights` — optional
- `entries` — optional

### Defaults

- `displayName` defaults from file name
- `cards` defaults to the set value, otherwise `3`
- `foils` defaults to the set value, otherwise `1`
- `texturePath` defaults to `<set_path>/<pack_name>`
- `rarityWeights` defaults to:
  - common `70`
  - uncommon `20`
  - rare `8`
  - epic `2`

### Notes

- Packs use Buddycards-style set tooltip behavior
- Pack name color matches Buddycards
- Packs stack like Buddycards
- Packs can be used in booster box recipes and loot injections

---

## Binders

Path:

```text
kubejs/data/<namespace>/buddyinfo/binders/<binder_name>.json
```

### Full layout

```json
{
  "displayName": "Buddycard Binder Example",
  "set": "example:example_set",
  "rows": 6,
  "guiTexturePath": "buddycard_binder_example"
}
```

### Fields

- `displayName` — optional
- `set` — required
- `rows` — optional
- `guiTexturePath` — optional

### Defaults

- `displayName` defaults from file name
- `rows` defaults to `6`
- item texture defaults to `<set_path>/<binder_name>`
- `guiTexturePath` defaults to `<binder_name>`

### Binder textures

If the binder JSON is:

```text
kubejs/data/example/buddyinfo/binders/buddycard_binder_example.json
```

and the set is:

```json
"set": "example:example_set"
```

the binder item texture should be:

```text
kubejs/assets/example/textures/item/example_set/buddycard_binder_example.png
```

If `guiTexturePath` is:

```json
"guiTexturePath": "buddycard_binder_example"
```

the GUI texture should be:

```text
kubejs/assets/example/textures/gui/buddycard_binder_example.png
```

### Binder recipe

Binders are generated with a recipe that uses:

- `1` leather
- `3` cards from the same set

BuddycardsJS automatically generates the needed set tag.

---

## Booster Boxes

Path:

```text
kubejs/data/<namespace>/buddyinfo/booster_boxes/<booster_box_name>.json
```

### Full layout

```json
{
  "displayName": "Buddycard Booster Box Example",
  "set": "example:example_set",
  "pack": "example:buddycard_pack_example"
}
```

### Fields

- `displayName` — optional
- `set` — recommended
- `pack` — strongly recommended

### Notes

- `pack` must match a real pack id exactly
- if the pack id is wrong, the booster box will not resolve correctly
- booster boxes use Buddycards-style multi-model generation

### Booster box textures

If the booster box JSON file is:

```text
kubejs/data/example/buddyinfo/booster_boxes/buddycard_booster_box_example.json
```

and the set is:

```json
"set": "example:example_set"
```

the textures should be:

```text
kubejs/assets/example/textures/block/example_set/buddycard_booster_box_example_bottom.png
kubejs/assets/example/textures/block/example_set/buddycard_booster_box_example_side.png
kubejs/assets/example/textures/block/example_set/buddycard_booster_box_example_top.png
```

### Booster box recipes

BuddycardsJS automatically generates:

- `6 packs -> 1 booster box`
- `1 booster box -> 6 packs`

---

## Medals

Path:

```text
kubejs/data/<namespace>/buddyinfo/medals/<medal_name>.json
```

### Full layout

```json
{
  "displayName": "Buddycard Medal Example",
  "set": "example:example_set",
  "medalType": "buddysteel",
  "effect": "minecraft:strength",
  "level": 1,
  "duration": 220,
  "itemTexturePath": "example_set/buddycard_medal_example"
}
```

### Fields

- `displayName` — optional
- `set` — required
- `medalType` — optional
- `effect` — required
- `level` — optional
- `duration` — optional
- `itemTexturePath` — optional

### Medal type options

- `buddysteel`
- `luminis`
- `zylex`

### Defaults

- `displayName` defaults from file name
- `medalType` defaults to `buddysteel`
- `level` defaults to `1`
- `duration` defaults to `220`
- `itemTexturePath` defaults to `<set_path>/<medal_name>`

### Notes

- Medals are added to the Curios medal tag automatically
- BuddycardsJS removes the effect line while preserving the normal set line and advanced tooltip behavior
- Medal item name color matches Buddycards

---

## Loot Injections

BuddycardsJS uses a **simple user-facing loot format** and generates the more complex Buddycards-style loot modifier files in the background.

Path:

```text
kubejs/data/<namespace>/buddyinfo/loot_injections/<file_name>.json
```

### Full layout

```json
{
  "targetLootTable": "simple_dungeon",
  "pack": "example:buddycard_pack_example",
  "weight": 1,
  "rolls": 2,
  "count": {
    "min": 1,
    "max": 2
  },
  "empty": 3
}
```

### Fields

- `targetLootTable` — required
- `pack` — required
- `weight` — optional
- `rolls` — optional
- `count.min` — optional
- `count.max` — optional
- `empty` — optional

### Defaults

- `weight` defaults to `1`
- `rolls` defaults to `1`
- `count.min` defaults to `1`
- `count.max` defaults to `2`
- `empty` defaults to `3`

### What `empty` means

`empty` is the weighted chance that the roll gives nothing.

So this:

```json
"weight": 1,
"empty": 3
```

means each roll is weighted like:

- 1 part = your pack
- 3 parts = nothing

This is what makes the loot feel much closer to Buddycards.

### Short alias support

If `targetLootTable` does **not** contain a namespace, BuddycardsJS assumes it is a chest loot table and expands it to:

```text
minecraft:chests/<value>
```

So:

```json
"targetLootTable": "simple_dungeon"
```

becomes:

```json
"targetLootTable": "minecraft:chests/simple_dungeon"
```

### Full id support

If `targetLootTable` already contains a namespace, BuddycardsJS uses it exactly as written.

So these are valid:

```json
"targetLootTable": "minecraft:chests/end_city_treasure"
```

```json
"targetLootTable": "minecraft:gameplay/fishing/treasure"
```

```json
"targetLootTable": "minecraft:archaeology/desert_pyramid"
```

### What short aliases support

Short aliases are recommended for vanilla **chest** loot tables, including Overworld, Nether, and End chest loot.

Examples:

- `simple_dungeon`
- `buried_treasure`
- `desert_pyramid`
- `shipwreck_treasure`
- `bastion_treasure`
- `nether_bridge`
- `end_city_treasure`
- `village_plains_house`
- `village_desert_house`
- `village_savanna_house`
- `village_snowy_house`
- `village_taiga_house`

### Recommended use

Use short aliases for:
- structure chest loot

Use full ids for:
- fishing
- archaeology
- entity loot
- anything outside `minecraft:chests/`

### What BuddycardsJS generates from loot injections

From one simple JSON file, BuddycardsJS automatically generates:

- `data/<namespace>/loot_modifiers/<file>.json`
- `data/<namespace>/loot_tables/inject/<file>.json`
- `data/forge/loot_modifiers/global_loot_modifiers.json`

This uses Buddycards’ loot modifier type under the hood, but keeps the user-facing format much simpler.

---

## Automatic Generation Summary

BuddycardsJS can generate:

### Assets

```text
kubejs/assets/<namespace>/models/item/
kubejs/assets/<namespace>/models/block/
kubejs/assets/<namespace>/blockstates/
kubejs/assets/<namespace>/lang/en_us.json
```

### Data

```text
kubejs/data/<namespace>/recipes/
kubejs/data/buddycards/tags/items/
kubejs/data/curios/tags/items/medal.json
kubejs/data/<namespace>/loot_modifiers/
kubejs/data/<namespace>/loot_tables/inject/
kubejs/data/forge/loot_modifiers/global_loot_modifiers.json
```

---

## Creative Tabs

BuddycardsJS content is placed into Buddycards’ creative tabs automatically:

- cards go into the Buddycards cards tab
- packs, binders, booster boxes, and medals go into the Buddycards main tab

---

## Crafting Summary

### Buddysteel Blend

BuddycardsJS cards are automatically added to the Buddycards card tag, so they work in the original Buddycards Buddysteel Blend recipe.

### Binder

Generated automatically:
- `1` leather
- `3` cards from the same set

### Booster Box

Generated automatically:
- `6` packs -> `1` booster box
- `1` booster box -> `6` packs

---

## Important Notes

### Card stacking

Cards stack if they are truly identical.

They may not stack if they differ by:
- foil state
- grading
- NBT

### Generated files

Do **not** manually edit generated files unless you know exactly what you are doing. They can be regenerated and overwritten.

### Fresh worlds after big registry changes

If you rename namespaces, mod ids, or item ids, use a fresh test world.

---

## Troubleshooting

### `.\gradlew.bat` is not recognized

You are probably not in the project folder. Make sure you are in the folder that contains:

- `build.gradle`
- `settings.gradle`
- `gradlew.bat`

### Items not showing up

Check:
- namespace spelling
- file path spelling
- JSON validity

### Booster box not generating

Most common reasons:
- wrong folder path
- wrong `pack` id
- missing set/pack references

### Too much loot in structures

Lower:
- `rolls`
- `count.max`

and increase:
- `empty`

To get closer to Buddycards feel, use something like:

```json
{
  "targetLootTable": "simple_dungeon",
  "pack": "example:buddycard_pack_example",
  "weight": 1,
  "rolls": 2,
  "count": {
    "min": 1,
    "max": 2
  },
  "empty": 3
}
```

### Seeing `item.<namespace>.<card>.tooltip` in-game

That means the generated language file is missing the tooltip key. Make sure the card JSON has a `tooltip` string and that the generated `en_us.json` was regenerated.

---

## Testing Workflow

When testing changes, it is often best to keep only:

- source JSON
- source textures

and delete generated files such as:

```text
models/
blockstates/
lang/
recipes/
tags/
loot_modifiers/
loot_tables/inject/
```

Then relaunch the game and let BuddycardsJS regenerate them.

---

## Example Minimal Set

### `sets/example_set.json`

```json
{
  "displayName": "Example Set"
}
```

### `cards/buddycard_example.json`

```json
{
  "displayName": "Buddycard Example",
  "set": "example:example_set",
  "number": 1,
  "rarity": "common",
  "tooltip": "This is example flavor text."
}
```

### `packs/buddycard_pack_example.json`

```json
{
  "displayName": "Buddycard Pack Example",
  "set": "example:example_set"
}
```

### `binders/buddycard_binder_example.json`

```json
{
  "displayName": "Buddycard Binder Example",
  "set": "example:example_set",
  "rows": 6,
  "guiTexturePath": "buddycard_binder_example"
}
```

### `booster_boxes/buddycard_booster_box_example.json`

```json
{
  "displayName": "Buddycard Booster Box Example",
  "set": "example:example_set",
  "pack": "example:buddycard_pack_example"
}
```

### `medals/buddycard_medal_example.json`

```json
{
  "displayName": "Buddycard Medal Example",
  "set": "example:example_set",
  "effect": "minecraft:strength"
}
```

### `loot_injections/simple_dungeon_example.json`

```json
{
  "targetLootTable": "simple_dungeon",
  "pack": "example:buddycard_pack_example",
  "weight": 1,
  "rolls": 2,
  "count": {
    "min": 1,
    "max": 2
  },
  "empty": 3
}
```

---

## Not Included

BuddycardsJS currently does **not** implement the Buddycards battle system.

That means:
- no battle abilities
- no combat requirement logic
- no battle mechanic parity

Everything documented here is focused on the non-battle side of Buddycards content creation.

---

## License / Credits

BuddycardsJS extends Buddycards and depends on Buddycards being present.

Respect the original Buddycards license and asset usage rules when distributing content packs, example packs, or derivative work.
