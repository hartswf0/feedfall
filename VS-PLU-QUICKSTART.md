# VIDEO_STACKER_PLUS - Quick Start Guide

## 🎉 What Just Got Better

### ✅ TV IDs Now On Frame (Not Floating!)
- ID labels like `TV-001` now appear **on the bottom bezel** of each TV
- Cyan text on black background
- Press **I** to toggle visibility
- Much cleaner, professional look

### ✅ 8 Camera Presets for Mobile
Perfect for different viewing needs:

**Press Number Keys 1-8:**
1. **Default** - Balanced view (0, 3, 6.5)
2. **Close-up** - Intimate detail (0, 2.5, 4)
3. **Overview** - See everything (0, 8, 10)
4. **Left Side** - Profile view (-5, 3.5, 3)
5. **Right Side** - Profile view (5, 3.5, 3)
6. **Top-Down** - Bird's eye (0, 10, 1)
7. **Low Angle** - Dramatic hero shot (0, 1, 7)
8. **Dramatic** - Cinematic angle (3, 2, 5)

**Or Press V** to cycle through them!

### ✅ Better HUD
Now shows:
- Current camera preset name
- Environment name
- Gravity mode
- Selected TV ID

### ✅ Water Properly Positioned
- Water plane at y = -0.2 (below ground)
- TVs sit above water
- Caustic shimmer visible beneath

---

## 🎮 Complete Controls

### Camera
```
V     - Cycle camera presets
C     - Cycle camera mode (TOP/WIDE/FREE)
1-8   - Jump to specific preset
```

### Environment
```
E     - Cycle environments (CALM → ENERGETIC → VOID → GALLERY)
```

### TV Operations
```
A     - Add one TV
F     - Fill to 100 TVs
D     - Clone selected TV (with tags!)
Del   - Delete selected TV
I     - Toggle ID labels
```

### Layout & Physics
```
L     - Cycle layouts
G     - Cycle gravity
```

### Scene Management
```
Ctrl+S  - Save scene as JSON
Esc     - Deselect/cancel
```

---

## 🌊 Try This Right Now!

1. **Open vs-plu.html**
2. Wait for 3 TVs to appear
3. **Press E** → Watch environment change!
4. **Press 2** → Zoom to close-up view
5. **Press 6** → Jump to top-down view
6. **Press F** → Spawn 100 TVs
7. **Press I** → See all IDs on TV frames
8. **Press V** repeatedly → Cycle through all 8 cameras

---

## 📱 Mobile-Optimized Views

### For Phone Vertical:
- **Press 2** (Close-up) - Best for detail
- **Press 7** (Low Angle) - Dramatic
- **Press V** to explore

### For Phone Horizontal:
- **Press 3** (Overview) - See the whole scene
- **Press 1** (Default) - Balanced
- **Press 8** (Dramatic) - Cinematic

### For Tablet:
- **Press 3** (Overview) first
- **Press 4/5** (Sides) to inspect
- **Press 6** (Top-Down) for planning

---

## 🎨 Environments Explained

### CALM (Default) 🌊
- **Water**: Animated shader with caustics
- **Fog**: Deep ocean blue (#0a1520)
- **Use for**: Meditation, poetry, reflection
- **Best camera**: 2 (Close-up) or 7 (Low Angle)

### ENERGETIC ⚡
- **No water**
- **Fog**: Warm red/orange
- **Use for**: Action sequences, energy
- **Best camera**: 8 (Dramatic) or 1 (Default)

### VOID 🌑
- **No water**
- **Fog**: Pure black
- **Use for**: Focus, isolation, minimalism
- **Best camera**: 2 (Close-up) or spotlight effect

### GALLERY 🖼️
- **No water**
- **Fog**: Neutral gray
- **Use for**: Professional presentation
- **Best camera**: 3 (Overview) or 1 (Default)

---

## 💡 Pro Tips

### Creating Scenes
1. **Press A** a few times to add TVs
2. **Press L** to try different layouts
3. **Press 1-8** to find best angle
4. **Press E** to match environment to mood
5. **Press Ctrl+S** to save

### Mobile Viewing
1. Start with **Press 1** (Default)
2. Tap a TV to select it
3. **Press 2** (Close-up) to focus
4. **Press V** to explore other angles
5. **Press I** to see all IDs

### Performance
- On slower devices: Stay under 50 TVs
- If laggy: Toggle physics off (coming soon)
- Water shader is optimized (60fps target)

---

## 🔍 What's in the HUD

**Top Left:**
```
TVs: 45/100          (current count / max)
Layout: stack        (current spatial arrangement)
View: Close-up       (current camera preset name)
```

**Top Right:**
```
ENV: Calm Water      (environment)
GRAV: Normal         (physics gravity)
VIEW: Close-up       (camera preset)
MODE: TOP           (tracking mode)
SELECTED: TV-015    (if TV selected)
```

---

## 📊 Scene Data

When you **press Ctrl+S**, you get JSON with:

```json
{
  "version": "1.0.0",
  "timestamp": 1234567890,
  "environment": "CALM",
  "layout": "stack",
  "tvs": [
    {
      "id": "TV-001",
      "position": {"x": 0, "y": 3, "z": 0},
      "tags": ["intro", "poem"],
      "metadata": {
        "title": "Opening Scene",
        "notes": "First segment"
      }
    }
  ]
}
```

**Use this for:**
- Version control
- Sharing scenes
- Backup before changes
- Analysis/processing

---

## 🎯 Common Workflows

### Video Essay Assembly
```
1. Press A 10-15 times (add TVs)
2. Press L to try layouts
3. Press 3 (Overview) to see structure
4. Press E to match mood
5. Select TVs and tag them (coming soon)
6. Press Ctrl+S to export
```

### Poetry Video
```
1. Press E until CALM environment
2. Press A for each stanza
3. Press 2 (Close-up) for intimate view
4. Watch water shimmer beneath
5. Press V slowly to explore angles
```

### Quick Browse
```
1. Press F (fill to 100)
2. Press L repeatedly (try layouts)
3. Press 1-8 (explore angles)
4. Press E (try environments)
5. Find your favorite combination
```

---

## 🐛 Troubleshooting

### Videos not playing?
- YouTube may block autoplay
- Try clicking a TV
- Check browser console for errors

### Performance issues?
- Close other tabs
- Don't exceed 50 TVs on mobile
- Try VOID environment (no water)

### Can't see IDs?
- Press **I** to toggle
- IDs are on bottom of TV frame
- Check if environment is too dark

### Water not visible?
- Make sure you're in CALM environment (**Press E**)
- Water is at y=-0.2 (below ground level)
- Look from **Press 7** (Low Angle) to see it clearly

---

## 🚀 Next Features (Coming Soon)

See `GIZMO-EDITION-ROADMAP.md` for full plan:

**Priority 1:**
- 🎯 Gizmo system (drag/rotate TVs in 3D)
- 📱 Mobile touch gestures
- 🎮 BUILD and GAME modes

**Priority 2:**
- 🗂️ LIBRARY mode (grid/ring layouts)
- 🕸️ ZETTEL MAP (graph visualization)
- 📤 EDL export for editing software

**Priority 3:**
- 🌈 Holographic overlay layers
- 🔊 Sound effects & haptics
- ⚡ Performance optimizations

---

## 📚 Documentation Files

- **VS-PLU-ARCHITECTURE.md** - Full technical specification
- **VS-PLU-README.md** - User guide with use cases
- **GIZMO-EDITION-ROADMAP.md** - Complete implementation plan
- **VS-PLU-QUICKSTART.md** - This file!

---

## ⌨️ Full Keyboard Reference

```
CAMERA:
V       Cycle presets
C       Cycle mode
1-8     Jump to preset

ENVIRONMENT:
E       Cycle

TVs:
A       Add
F       Fill to 100
D       Clone selected
Delete  Remove selected
I       Toggle IDs
Space   Drop (game mode)

LAYOUT:
L       Cycle

PHYSICS:
G       Cycle gravity

TOOLS:
Q       Select
W       Move
R       Snap
T       Tag

SCENE:
Ctrl+S  Save
Esc     Cancel
```

---

**Ready to build your 3D video Zettelkasten!** 🎬✨

Open **vs-plu.html** and start exploring with **Press 1-8** to see all the new camera angles!
