# BuddycardsAPI — Developer Documentation

![Minecraft](https://img.shields.io/badge/Minecraft-1.20.1-brightgreen)
![Forge](https://img.shields.io/badge/Forge-47.4.10-orange)
![API](https://img.shields.io/badge/type-developer--api-blue)

---

# 🧠 Overview

BuddycardsAPI is a **data-driven content framework** built on top of Buddycards.

It enables:
- runtime content loading
- automatic asset generation
- JSON-defined card ecosystems

This document is intended for:
- mod developers
- modpack developers
- advanced users

---

# ⚙️ Architecture

Core pipeline:

1. JSON → ExternalContentLoader
2. Stored in → ExternalContentRepository
3. Registered via → BcaItems
4. Assets generated via:
   - GeneratedAssetWriter
   - GeneratedDataWriter

---

# 📦 Data Model

## CardDefinition

Fields:

- id (generated)
- displayName (String)
- set (String, namespaced)
- number (Integer)
- rarity (String)
- foil (Boolean, optional)
- cost (Integer, unused if battle disabled)
- power (Integer, unused if battle disabled)

---

## CardSetDefinition

- id
- displayName

---

## PackDefinition

- id
- set

---

## BinderDefinition

- id
- set

---

## BoosterBoxDefinition

- id
- pack OR set

---

## MedalDefinition

- id
- set
- effect (String)
- level (Integer)
- duration (Integer)

---

# 🧾 JSON Schema (Simplified)

## Card

{
  "displayName": "String",
  "set": "namespace:set",
  "number": int,
  "rarity": "common|uncommon|rare|epic",
  "foil": boolean (optional)
}

---

# ⚙️ Generation System

## Asset Generation

GeneratedAssetWriter creates:

- item models
- block models
- blockstates
- lang entries

---

## Data Generation

GeneratedDataWriter creates:

- recipes
- tags
- binder recipes
- booster box recipes

---

# 🏷️ Tag System

## Global Card Tag

buddycards:buddycards

Contains all API cards.

Used for:
- Buddysteel Blend

---

## Set-Specific Tags

buddycards:buddycards_<set>

Used for:
- binder recipes

---

# 🧱 Recipe Logic

## Buddysteel Blend

Uses:
- buddycards:buddycards

---

## Binder

Uses:
- buddycards:buddycards_<set>

---

## Booster Box

Generated per box:
- shaped: packs → box
- shapeless: box → packs

---

# 🎨 Texture Resolution

Paths resolve as:

item:
textures/item/<set>/<item>.png

block:
textures/block/<set>/

gui:
textures/gui/

---

# ⚙️ Registration Flow

Cards are registered through:

BcaItems.registerCards()

Important:

Item.Properties().stacksTo(64)

---

# 🧪 Runtime Behavior

Cards stack only if:
- identical item
- identical NBT

NBT differences:
- foil
- grading
→ prevent stacking

---

# 🎯 Creative Tabs

Handled via Buddycards:

- cards → cards tab
- others → main tab

---

# ⚠️ Constraints

- namespace must match everywhere
- JSON must be valid
- generated files are overwritten

---

# 🧪 Debugging

Check logs for:

- missing set
- invalid namespace
- missing texture

---

# 🚧 Extensibility

Possible future extensions:

- pack weighting tables
- custom drop logic
- multi-pack systems
- battle system integration

---

# 📜 License

Respects Buddycards license.

---

# 🧩 Final Notes

This API is designed as a **content layer**, not a gameplay rewrite.

It mirrors Buddycards behavior while enabling:
- scalability
- modular content
- pack-based design
