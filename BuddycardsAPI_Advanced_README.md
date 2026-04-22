# BuddycardsAPI (Advanced Edition)

![Minecraft](https://img.shields.io/badge/Minecraft-1.20.1-brightgreen)
![Forge](https://img.shields.io/badge/Forge-47.4.10-orange)
![Status](https://img.shields.io/badge/status-stable-success)
![Data Driven](https://img.shields.io/badge/system-data--driven-blue)

---

# 🎴 Overview

BuddycardsAPI is a **fully data-driven extension for Buddycards** that allows you to create complete card ecosystems using only JSON + textures.

This document is a **complete + advanced guide** for both beginners and modpack developers.

---

# 📦 Requirements

- Minecraft 1.20.1
- Forge 47.4.10
- Buddycards
- KubeJS
- Curios
- BuddycardsAPI

---

# 🚀 Setup

1. Install mods
2. Launch once
3. Go to `.minecraft/kubejs/`

---

# 📁 Folder Structure

## Data
kubejs/data/<namespace>/buddyinfo/

## Assets
kubejs/assets/<namespace>/textures/

---

# 🧾 BASIC CREATION

## Set
{
  "displayName": "Test Set"
}

## Card
{
  "displayName": "Test Card",
  "set": "test:test_set",
  "number": 1,
  "rarity": "common"
}

## Pack
{
  "displayName": "Test Pack",
  "set": "test:test_set"
}

## Binder
{
  "displayName": "Test Binder",
  "set": "test:test_set"
}

## Booster Box
{
  "displayName": "Test Booster Box",
  "pack": "test:test_pack"
}

## Medal
{
  "displayName": "Test Medal",
  "set": "test:test_set",
  "effect": "minecraft:strength"
}

---

# 🎨 TEXTURES

textures/item/<set>/<item>.png  
textures/block/<set>/  
textures/gui/

---

# ⚙️ AUTOMATIC SYSTEMS

- Recipes
- Tags
- Models
- Foils
- Grading
- Creative tabs

---

# 🧱 CRAFTING

Buddysteel Blend:
- 1 iron block
- 1 lapis block
- 3 cards

Binder:
- 1 leather
- 3 cards (same set)

Booster Box:
- 6 packs

---

# 🔥 ADVANCED CONFIGURATION

## 🎴 Card Metadata (Optional)

{
  "displayName": "Advanced Card",
  "set": "test:test_set",
  "number": 5,
  "rarity": "rare",
  "foil": true
}

---

## 🏷️ Tags

- buddycards:buddycards
- buddycards:buddycards_<set>

---

## ⚙️ Generation

Auto-generates:
- models
- recipes
- tags
- lang

---

## 🧪 Debugging

Check logs for:
- missing set
- invalid JSON

---

## 🧱 Stacking

Stacks only if identical

---

## 🎯 Creative Tabs

- cards tab
- main tab

---

# ⚠️ TROUBLESHOOTING

Items missing → namespace  
Textures broken → path  
Recipes broken → tags  
Crash → JSON  

---

# 📦 EXAMPLE PACK

example_kubejs_pack/

---

# 📜 LICENSE

Respects Buddycards license.
