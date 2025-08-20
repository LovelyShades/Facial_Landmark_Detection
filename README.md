# 👁️‍🗺️ Facial Landmark Debugger (Web Demo)

[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)]()
[![Platform](https://img.shields.io/badge/Platform-Browser-blue.svg)]()
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()

A browser-based **Facial Landmark / Keypoint Debugger** that lets you upload an image, detect face landmarks (MediaPipe FaceMesh via TFJS), and **inspect, label, and practice** specific keypoint sets.  
Includes **zoom/pan**, **label toggles**, **point/font size controls**, and a **stackable mask overlay system** with tint, opacity, and blend modes.

> **Author:** Alanna Matundan  
> **Purpose:** Learning · Debugging · Practice/Study Tool

---

## ✨ Features
- 🖼️ **Image Upload & Detection** — one-click face landmark detection on your image
- 🔎 **Zoom & Pan** — mouse wheel zoom + click-drag pan (infinite canvas feel)
- 🔢 **Adjustable Visuals** — sliders for **point size** and **label font size**
- 🏷️ **Show/Hide Labels** — toggle numeric indices for all keypoints
- 🎯 **Selectable Keypoint** — click highlights nearest point with readable label
- 📚 **Practice Mode** — create/edit/delete **named sets of indices**, persist to **localStorage**, and “show only selected”
- 🎨 **Mask Overlay System** — upload multiple masks, set **tint**, **opacity**, **blend mode**; **reorder**, **toggle** visibility, or **remove**
- 🧹 **Session Controls** — remove image / clear masks / clear practice sets

---

## 🧰 Tech Stack
- **Language:** JavaScript (ES6+), HTML5, CSS3  
- **ML:** TensorFlow.js + `@tensorflow-models/face-landmarks-detection` (MediaPipe FaceMesh)  
- **Rendering:** HTML5 Canvas 2D  
- **Storage:** `localStorage` (practice sets)

---

## 🚀 Getting Started
### Prerequisites
A modern browser (Chrome/Edge/Firefox).  
To avoid any local file restrictions, serve the folder over HTTP:

```bash
# Option A: Python 3
python -m http.server 8000

# Option B: Node http-server (if installed)
npx http-server -p 8000

Then open:
http://localhost:8000
(You can also open the HTML file directly; CDNs are used for TFJS and the model, but some browsers restrict local file access, so a local server is recommended.)

📖 Usage
Upload an image with a clear, front-facing face.

The app detects landmarks and renders them over your image.

Use the sliders to adjust point size and font size.

Toggle Show Labels to see keypoint indices.

Zoom with the mouse wheel; pan by click-dragging inside the canvas.

Click near a landmark to select and highlight it.

Practice Mode
Toggle Practice Mode (▶ / ▼).

Create a named set (e.g., “Eyes”) with a comma-separated list of indices: 33, 7, 109

Add/Update/Delete sets; they’re saved to localStorage.

Use Show Only Selected to focus on just one set.

Mask Overlays
Upload one or more masks (PNG recommended).

For each mask you can:

Toggle visibility

Set Tint Color (color picker)

Adjust Opacity (0–1 slider)

Change Blend Mode (multiply, screen, overlay, etc.)

Reorder (↑ / ↓) or Remove (✕)

🧱 Project Structure

index.html      # App UI and controls (this file)
styles (inline) # Minimal, inline CSS for layout/controls
<Canvas>        # Main drawing surface

# External (CDN):
# - @tensorflow/tfjs
# - @tensorflow-models/face-landmarks-detection (MediaPipe FaceMesh)

🧪 How It Works (Brief)
Loads TFJS and the FaceMesh detector from CDN.

On image upload, resizes a copy for inference, then maps predicted keypoints back to the original resolution.

Draws the base image, then overlays:

Masks (stacked with chosen blend modes/tints)

Keypoints and labels (respecting zoom/pan)

Selection highlight (if a keypoint is selected)

Practice sets live in localStorage and drive visibility when “Show Only Selected” is enabled.

🧯 Troubleshooting
“No face detected”: Use a larger, front-facing image with good lighting.

Nothing appears: Ensure the canvas is visible and the image finished loading.

Slow on large images: The app downsamples for inference, but extremely large images can still be heavy.

Local file issues: Serve via a local HTTP server (see Getting Started).

📚 What I Learned
Using TFJS + MediaPipe FaceMesh in a browser workflow

Mapping detection coordinates between resized inference and display space

Implementing canvas zoom/pan with stable transforms

Designing a practice/study flow for keypoint subsets with persistence

Building a layered mask system (tint, opacity, blend modes, z-order)

🛣️ Future Improvements
Multi-face support + face selector

Save/Load sessions (image, masks, sets) to a file

Export CSV / JSON of selected keypoints

Screenshot/export annotated image

Keyboard shortcuts for zoom/pan/toggles

Performance pass for very large images

📜 License
Educational project — free to view and adapt with attribution for non-commercial use.
Please credit Alanna Matundan if you reuse ideas or UI patterns from this tool.
