# Excalidraw Reference

Generate `.html` files with embedded Excalidraw diagrams. Open in browser (macOS: `open`, Linux: `xdg-open`, Windows: `start`).

## HTML Template

Replace `elementsData` array with designed elements:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Excalidraw Preview</title>
    <link rel="stylesheet" href="https://esm.sh/@excalidraw/excalidraw@0.18.0/dist/dev/index.css" />
    <script>window.EXCALIDRAW_ASSET_PATH = "https://esm.sh/@excalidraw/excalidraw@0.18.0/dist/prod/";</script>
    <script type="importmap">{"imports":{"react":"https://esm.sh/react@19.0.0","react/jsx-runtime":"https://esm.sh/react@19.0.0/jsx-runtime","react-dom":"https://esm.sh/react-dom@19.0.0","react-dom/client":"https://esm.sh/react-dom@19.0.0/client"}}</script>
    <style>*{margin:0;padding:0;box-sizing:border-box}html,body,#app{height:100%;width:100%}</style>
  </head>
  <body>
    <div id="app"></div>
    <script type="module">
      import React from "https://esm.sh/react@19.0.0";
      import { createRoot } from "https://esm.sh/react-dom@19.0.0/client";
      import * as ExcalidrawLib from "https://esm.sh/@excalidraw/excalidraw@0.18.0/dist/dev/index.js?external=react,react-dom";
      const { Excalidraw, convertToExcalidrawElements } = ExcalidrawLib;
      const elementsData = [/* INSERT ELEMENTS */];
      const elements = convertToExcalidrawElements(elementsData);
      function App() {
        return React.createElement("div", { style: { height: "100%", width: "100%" } },
          React.createElement(Excalidraw, {
            initialData: { elements, appState: { viewBackgroundColor: "#1e1e1e" }, scrollToContent: true },
            langCode: "en",
          }));
      }
      createRoot(document.getElementById("app")).render(React.createElement(App));
    </script>
  </body>
</html>
```

Default: dark mode (`#1e1e1e`). Use `#ffffff` for light mode if needed.

## Element Properties

```javascript
{ type, x, y, width, height, strokeColor, backgroundColor,
  fillStyle: "solid"|"hachure"|"cross-hatch", strokeWidth: 1|2|4,
  roughness: 0|1|2, opacity: 0-100, roundness: {type:3}|null }
```

Types: `rectangle`, `ellipse`, `diamond`, `line`, `arrow`, `text`, `freedraw`.

**Text**: `{ type: "text", x, y, text, fontSize, width: REQUIRED, fontFamily: 1|2|3, textAlign: "center" }`

Width: Latin chars `text.length * fontSize * 0.6`, CJK chars `text.length * fontSize * 1.0`, mixed: sum per-char.

fontSize: 16 (S), 20 (M), 28 (L), 36 (XL). fontFamily: 1 (hand-drawn), 2 (normal), 3 (code).

**Arrow/Line**: positive width = right, negative = left. Positive height = down, negative = up.

## Color Palette

| Color | Fill | Stroke |
|-------|------|--------|
| Blue | `#a5d8ff` | `#1971c2` |
| Green | `#b2f2bb` | `#2f9e44` |
| Yellow | `#ffec99` | `#f08c00` |
| Red | `#ffc9c9` | `#e03131` |
| Purple | `#d0bfff` | `#7048e8` |
| Gray | `#e9ecef` | `#495057` |
| Orange | `#ffd8a8` | `#e8590c` |
| Cyan | `#99e9f2` | `#0c8599` |

## Layout

Padding ≥40px between elements. Group spacing 80-100px. Text padding in shapes: 20px. Consistent flow direction (LTR or TTB). Avoid line intersections.

## Common Patterns

**Flowchart node:**
```javascript
[
  { type: "rectangle", x: 0, y: 0, width: 160, height: 60, backgroundColor: "#a5d8ff", strokeColor: "#1971c2", roundness: { type: 3 } },
  { type: "text", x: 80, y: 30, text: "Step 1", fontSize: 20, textAlign: "center" }
]
```

**Labeled arrow:**
```javascript
[
  { type: "arrow", x: 160, y: 30, width: 100, height: 0, strokeColor: "#495057" },
  { type: "text", x: 185, y: 10, text: "depends on", fontSize: 14, width: 84, fontFamily: 2, textAlign: "center", strokeColor: "#495057" }
]
```

**Bound text** (centered in shape):
```javascript
[
  { type: "rectangle", id: "box1", x: 0, y: 0, width: 160, height: 60, backgroundColor: "#a5d8ff", strokeColor: "#1971c2", roundness: { type: 3 } },
  { type: "text", x: 80, y: 30, text: "Concept", fontSize: 20, width: 96, textAlign: "center", containerId: "box1" }
]
```

**Dashed container:**
```javascript
{ type: "rectangle", x: 0, y: 0, width: 300, height: 200, backgroundColor: "transparent", strokeColor: "#dee2e6", strokeStyle: "dashed" }
```
