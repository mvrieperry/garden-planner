# Migration Plan: Single File → Vite + ES Modules

The app currently lives entirely in `index.html`. This document outlines how to migrate to a proper multi-file structure when the time comes, without changing any functionality.

---

## When to migrate

Consider migrating when any of these become true:

- `index.html` exceeds ~4,000 lines and is hard to navigate
- A second developer joins the project
- You want to write automated tests
- You need a bundler for tree-shaking, TypeScript, or npm packages

---

## Target structure

```
garden-planner/
├── index.html                  # Shell only — loads the app, no logic
├── package.json
├── vite.config.js
├── styles.css                  # All CSS extracted from <style> tag
└── src/
    ├── main.js                 # Entry point — initialises app, wires events
    ├── state.js                # beds, obstacles, garden, selectedId, history
    ├── constants.js            # SCALE, PLANT_DATA, PLANT_GROUPS, BED_COLORS
    ├── data/
    │   └── plantData.js        # PLANT_DATA object (large, isolated here)
    ├── canvas/
    │   ├── draw.js             # draw(), drawBed(), drawObstacle()
    │   ├── events.js           # mouse + touch + wheel handlers
    │   └── viewport.js         # viewX/Y/Zoom, screenToWorld, fitView
    ├── ui/
    │   ├── panel.js            # syncPanel(), updateProp(), syncPositionFields()
    │   ├── sidebar.js          # openSidebar(), closeSidebar(), renderLists()
    │   ├── report.js           # openReport(), generateBuildHTML(), generateShoppingHTML()
    │   ├── igrid.js            # plant organiser — initPlantGrid(), igridDrop(), etc.
    │   └── tutorial.js         # tutorial modal logic
    └── utils/
        ├── geometry.js         # ft(), px(), snap(), hitTest(), visualPos()
        ├── amazon.js           # amazonUrl(), whereToBuyBanner()
        └── storage.js          # saveData(), loadData(), saveHistory(), undo()
```

---

## Step-by-step migration

### 1. Set up Vite (~15 min)

```bash
npm create vite@latest garden-planner-v2 -- --template vanilla
cd garden-planner-v2
npm install
```

### 2. Extract CSS (~30 min)

Copy everything inside the `<style>` tag in `index.html` into `styles.css`. Import it in `main.js`:

```js
import './styles.css';
```

### 3. Extract constants (~30 min)

Move `SCALE`, `PLANT_DATA`, `PLANT_GROUPS`, `BED_COLORS` into `src/constants.js` and export them:

```js
export const SCALE = 36;
export const PLANT_DATA = { ... };
```

### 4. Extract state (~20 min)

Move all `let` globals (`beds`, `obstacles`, `garden`, `selectedId`, etc.) into `src/state.js`:

```js
export let beds = [];
export let obstacles = [];
export let garden = { width: 20, height: 18 };
export let selectedId = null;
// etc.
```

Functions that mutate state import from here.

### 5. Extract utilities (~30 min)

Move pure functions with no DOM dependencies into `src/utils/`:

- `ft()`, `px()`, `snap()` → `geometry.js`
- `saveData()`, `loadData()`, `saveHistory()`, `undo()` → `storage.js`
- `amazonUrl()`, `amazonBadge()`, `whereToBuyBanner()` → `amazon.js`

### 6. Extract canvas code (~1 hr)

Move canvas drawing and event handlers into `src/canvas/`. These files will import from `state.js` and `constants.js`.

### 7. Extract UI modules (~1 hr)

Move panel, sidebar, report modal, igrid, and tutorial logic into `src/ui/`. These are the most intertwined pieces — do them last.

### 8. Wire it all together in `main.js` (~30 min)

```js
import { initCanvas } from './canvas/draw.js';
import { bindEvents } from './canvas/events.js';
import { loadData }   from './utils/storage.js';

loadData();
initCanvas();
bindEvents();
```

### 9. Update `index.html`

Strip out all `<script>` and `<style>` content. Add:

```html
<script type="module" src="/src/main.js"></script>
```

### 10. Deploy to GitHub Pages

Add to `vite.config.js`:

```js
export default { base: '/garden-planner/' }
```

Add to `package.json`:

```json
"scripts": {
  "dev":    "vite",
  "build":  "vite build",
  "deploy": "npm run build && gh-pages -d dist"
}
```

```bash
npm install --save-dev gh-pages
npm run deploy
```

---

## Estimated total effort

| Task | Time |
|---|---|
| Vite setup | 15 min |
| CSS extraction | 30 min |
| Constants + state | 45 min |
| Utilities | 30 min |
| Canvas modules | 1 hr |
| UI modules | 1 hr |
| Wiring + testing | 1 hr |
| **Total** | **~5 hours** |

---

## Notes

- Do the migration in a separate branch (`git checkout -b vite-migration`)
- Migrate one module at a time, testing in the browser after each step
- The app has no tests today — consider adding [Vitest](https://vitest.dev/) for `geometry.js` and `storage.js` as a first step
- All existing save data (localStorage) is forward-compatible — no data migration needed
