# 🧠 3D Memory Game — Flask + Three.js + Bootstrap

A browser-based memory matching game featuring a 3D card grid rendered with
Three.js, served through a lightweight Flask backend, and styled with
Bootstrap 5.

![Tech Stack](https://img.shields.io/badge/Flask-black?logo=flask)
![Tech Stack](https://img.shields.io/badge/Three.js-black?logo=three.js)
![Tech Stack](https://img.shields.io/badge/Bootstrap-5.3-purple?logo=bootstrap)

---

## Features

- 🎴 4×4 grid (8 matching pairs) of interactive 3D cards
- 🖱️ Click-to-flip cards with smooth animated 3D rotation
- 🎯 Real-time move counter and match tracker
- 🏆 Win detection with a completion message
- 🔄 One-click restart with a freshly shuffled deck
- 🎨 Procedurally generated card textures (no external image assets)
- 📱 Responsive Bootstrap layout — no custom CSS required

---

## Tech Stack

| Layer      | Technology              |
|------------|--------------------------|
| Backend    | Flask (Python)           |
| Frontend   | HTML5, Bootstrap 5.3     |
| 3D Engine  | Three.js (r128)          |
| Styling    | Bootstrap utility classes only (no internal/custom CSS) |

---

## Project Structure

```
session2/
├── app.py                  # Flask application entry point
├── templates/
│   └── index.html          # Game UI + Three.js game logic (internal JS)
└── README.md
```

---

## Getting Started

### Prerequisites
- Python 3.8+
- pip

### Installation

```bash
# Clone or navigate into the project folder
cd session2

# (Optional) create a virtual environment
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# Install dependencies
pip install flask
```

### Run the app

```bash
python app.py
```

Then open your browser and go to:

```
http://127.0.0.1:5000/
```

---

## How to Play

1. The board displays 16 face-down cards arranged in a 4×4 grid.
2. Click any card to flip it face-up and reveal its symbol.
3. Click a second card to try to find its match.
   - ✅ If the symbols match, both cards stay face-up permanently.
   - ❌ If they don't match, both cards flip back after a short delay.
4. Each pair of flips counts as one **move**.
5. Match all 8 pairs to win the game.
6. Click **Restart** at any time to reshuffle and play again.

---

## Implementation Notes

- **Card rendering**: Each card is a `THREE.Group` containing a front face,
  back face, and edge mesh, allowing a realistic 3D flip animation via
  `rotation.y` tweening.
- **Textures**: Card faces (the `?` back and the symbol fronts) are drawn
  dynamically onto an HTML5 `<canvas>` and applied as `THREE.CanvasTexture` —
  no external image files needed.
- **Interaction**: Uses `THREE.Raycaster` to detect which card was clicked
  in 3D space based on mouse coordinates.
- **Game state**: Managed entirely in-browser with vanilla JavaScript
  (deck shuffling, move/match counters, win condition) — Flask only serves
  the static template.

---

## Possible Enhancements

- 🔊 Add sound effects for flips and matches
- ⚙️ Difficulty selector (3×4, 4×4, 6×6 grids)
- 🖱️ OrbitControls for free camera rotation/zoom
- ⏱️ Add a timer / leaderboard
- 💾 Persist high scores via a Flask backend + database

---

## License

This project is provided as a demo/learning example and is free to use and modify.
