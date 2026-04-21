# BuddycardsAPI

![Minecraft](https://img.shields.io/badge/Minecraft-1.20.1-brightgreen)
![Forge](https://img.shields.io/badge/Forge-47.4.10-orange)
![Status](https://img.shields.io/badge/status-stable-success)

BuddycardsAPI is a **data-driven extension mod for Buddycards** that allows you to create fully functional card sets using JSON and textures — no Java coding required.

This guide explains **everything you need to know** to create your own cards, packs, binders, booster boxes, and medals.

---

# 📦 Requirements

- Minecraft **1.20.1**
- Forge **47.4.10**
- Buddycards
- KubeJS
- Curios
- BuddycardsAPI

---

# 🚀 Getting Started

1. Install all required mods
2. Launch the game once
3. Navigate to `.minecraft/kubejs/`

---

# 📁 Folder Structure

## Data

kubejs/data/<namespace>/buddyinfo/

## Assets

kubejs/assets/<namespace>/textures/

---

# 🧾 Example Card

```json
{
  "displayName": "Test Card",
  "set": "test:test_set",
  "rarity": "common"
}
```

---

# 🎨 Textures

textures/item/<set>/<item>.png

---

# ⚙️ Features

- Cards, Packs, Binders, Booster Boxes, Medals
- Foils + Grading
- Auto Recipes
- Creative Tabs

---

# 🧪 Testing

Check:
- Creative tabs
- Crafting
- Packs opening

---

# 📜 License

Extends Buddycards. Follow original license.
