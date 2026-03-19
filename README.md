# 🌱 Garden Planner

A free, browser-based garden planning tool for designing raised beds, ground areas, and container gardens — with plant placement, companion planting guidance, a materials shopping list, and more.

**No sign-up. No install. No internet required after load.**

---

## ✨ Features at a Glance

- 🖼️ **Visual canvas** — drag, drop, zoom, and pan your garden layout
- 🌿 **55 plants** — with spacing, sun, water, and companion data built in
- 📐 **Square-foot grid** — see exactly how many plants fit in each bed
- 🛒 **Shopping list** — lumber, soil, seeds, hardware, and Amazon links
- 📱 **Mobile-friendly** — full touch support including pinch-to-zoom and swipe panels
- 💾 **Save & load** — export your plan as a JSON file, pick it up later
- ↩️ **Undo/redo** — 50-step history so you can experiment freely

---

## 🚀 Getting Started

1. Open `index.html` in any modern browser (Chrome, Safari, Firefox, Edge).
2. Set your **garden dimensions** in the left sidebar (width × length in feet).
3. Click **＋ Raised Bed**, **＋ Ground Area**, or **＋ Pot** to add planting spaces.
4. Drag beds around the canvas to arrange your layout.
5. Click any bed to select it, then add plants from the dropdown in the right panel.
6. Open the **Plant Organizer** to arrange plants square-foot by square-foot inside each bed.
7. Open the **Shopping List** to see a full materials breakdown.
8. Click **Save Plan** when you're done.

---

## 🗺️ Layout Overview

The app is divided into three panels:

### Left Sidebar
- Garden dimensions
- List of all beds, ground areas, and pots
- Obstacles list
- Quick-action buttons (Save, Load, Export PNG, Print, Undo, Redo)
- Tools: Plant Organizer · Shopping List · Bed Builder
- Local garden store link configuration

*On mobile the sidebar slides in as a drawer from the ☰ menu button.*

### Center Canvas
- Drag beds and obstacles to position them
- Scroll wheel / pinch = zoom in and out
- Drag empty space = pan
- Click a bed to select it
- Double-click a bed or obstacle to rename it
- Zoom controls and snap-to-grid toggle in the toolbar

### Right Panel
- Edit the selected item's name, dimensions, depth, and position
- Add or remove plants
- Write notes about the bed
- Open the Plant Organizer for that specific bed

*On mobile the right panel slides up from the bottom.*

---

## 🛏️ Bed Types

| Type | Description |
|---|---|
| **Raised Bed** | Rectangular, configurable depth (8", 12", 15", 18"). Includes lumber cost calculation. |
| **Ground Area** | In-ground planting space shown with a dashed border. No depth — no lumber needed. |
| **Pot / Planter** | Circular container, selectable diameter (1–3 ft). Great for herbs and small plants. |

Each bed can be customized with:
- **Name** — defaults to "Bed 1", "Bed 2", etc.
- **Width & Length** — in 0.5 ft increments, up to 40 ft
- **Position** — drag on canvas or enter X/Y coordinates
- **Color** — auto-assigned from a 7-color palette (consistent throughout the app)
- **Notes** — free-text field for reminders, seed variety, etc.

---

## 🌿 Plant Database (55 Plants)

All plants include companion planting, conflict, spacing, depth, sun, and water data.

### Vegetables
🍅 Tomatoes · 🌶️ Hot Peppers · 🫑 Bell Peppers · 🍆 Eggplant · 🥒 Cucumbers · 🎃 Squash · 🌽 Corn · 🥕 Carrots · 🥔 Potatoes · 🍠 Sweet Potatoes · 🥬 Lettuce · 🌱 Spinach · 🥦 Broccoli · 🫛 Green Beans · 🫘 Edamame · 🧅 Onions · 🧄 Garlic · 🌱 Radishes

### Herbs
🌿 Basil · 🌿 Chives · 🌿 Parsley · 🌿 Cilantro · 🌿 Thyme · 🌿 Oregano · 🌿 Mint · 🌿 Rosemary · 🌿 Dill · 🌿 Sage

### Flowers
🌼 Marigolds · 🌸 Nasturtiums · 🌻 Sunflowers · 🌹 Roses · 🌷 Tulips · 🌺 Hibiscus · 🪷 Lavender · 💐 Wildflowers

### Fruit
🍓 Strawberries · 🫐 Blueberries · 🍇 Grapes · 🍈 Melon · 🍉 Watermelon · 🍎 Apple · 🍐 Pear · 🍑 Peach · 🍒 Cherries · 🍋 Lemon · 🥝 Kiwi

---

## 📐 Plant Organizer

The **Plant Organizer** is a square-foot grid for each bed where you can precisely place plants cell by cell.

### How It Works
- Each cell = **1 square foot**
- The grid matches your bed's width × length (e.g. a 4×8 bed = 32 cells)
- Drag plants from the **palette** at the bottom onto any open cell
- Drag cells within the grid to rearrange plants
- Double-click (or double-tap on mobile) a plant emoji to remove it
- Use **Reset Layout** to auto-arrange all plants, or **Clear All Plants** to start fresh

### Spacing-Aware Emojis
Plants that need more than 1 sqft take up multiple cells automatically:

| Plant footprint | Grid span |
|---|---|
| 1 sqft | 1×1 |
| 4 sqft | 2×2 |
| 9 sqft | 3×3 |
| 16 sqft | 4×4 |

The app blocks you from placing a plant if there aren't enough consecutive free cells for its footprint.

### Companion Planting Alerts
- ✅ **Green banner** — good companions detected in the same bed
- ⚠️ **Red banner** — conflicting plants detected, consider separating them

---

## 🛒 Shopping List

The Shopping List tab aggregates everything across all your beds into a single buy list.

### What's Included

**Lumber**
- Board-by-board breakdown using a bin-packing algorithm to minimize waste
- Cut list with exact dimensions for each bed side
- Board sizing based on depth (2×6 for 6–11", 2×8 for 12"+)
- Cost estimates per board

**Hardware**
- Corner posts (4×4 sizing based on depth)
- Screws (quantity based on board count)

**Soil**
- Cubic feet per bed
- Bag count (standard 2 cu ft bags)
- Grand total soil volume

**Seeds & Plants**
- Every plant type used across all beds
- Count of how many plants/seeds to buy (from your grid layout)
- Amazon search link for seeds for each plant

**Where to Buy**
- Links to Amazon for lumber, posts, screws, and soil
- Optional local hardware store link (set your store in the sidebar)

---

## 💾 Save & Load

- **Save Plan** — downloads a `.json` file containing your garden layout, all beds, plants, and obstacles
- **Load Plan** — restores a previously saved `.json` file
- Plant grids are included in the save file so your organizer layouts are preserved

> Plans are **not** stored in the browser automatically — download your save file to keep your work.

---

## 📤 Export & Print

- **Export PNG** — saves the current canvas view as a PNG image
- **Print** — opens a printable view with your garden map and a materials table

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl+Z` / `Cmd+Z` | Undo |
| `Ctrl+Shift+Z` / `Cmd+Shift+Z` | Redo |
| `Delete` / `Backspace` | Delete selected bed or obstacle |

---

## 📱 Mobile Support

The app is fully usable on phones and tablets:

| Gesture | Action |
|---|---|
| Tap a bed | Select it, open detail panel |
| Drag a bed | Move it |
| Single-finger drag on empty space | Pan the canvas |
| Pinch two fingers | Zoom in/out |
| ☰ button (top left) | Open sidebar menu |
| Swipe panel down | Close the detail panel |

In the Plant Organizer on mobile, drag plants from the palette to the grid cells using touch.

---

## 🧱 Tech Stack

- **Single HTML file** — zero dependencies, no build step, no framework
- **HTML5 Canvas** — for the garden layout rendering
- **CSS Grid** — for the interactive plant organizer
- **Vanilla JavaScript** — all logic, no libraries
- Works entirely offline once loaded

---

## 📁 Project Structure

```
garden-planner/
└── index.html    # The entire app — HTML, CSS, and JS in one file
```

---

## 🤝 Contributing

Feature ideas and bug reports are welcome via [GitHub Issues](https://github.com/mvrieperry/garden-planner/issues).

---

## 📄 License

MIT — free to use, modify, and share.
