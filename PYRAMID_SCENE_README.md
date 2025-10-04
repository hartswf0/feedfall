# Pyramid Scene — "Out of Life" Installation

## Overview

A static installation of **14 TVs arranged in a pyramid formation**, each playing a different timestamp from the same YouTube video, creating a fragmented temporal experience.

**Video**: [MT3snSsqcHs](https://youtu.be/MT3snSsqcHs) — "Out of Life" (24:01 duration)

---

## Quick Start

1. Open `pyramid-scene.html` in a modern browser
2. Wait for all 14 YouTube players to initialize
3. All TVs play simultaneously from different timestamps
4. Use controls:
   - **⟲** Toggle slow camera orbit
   - **🔊/🔇** Mute/unmute all TVs
   - **⌂** Reset camera to default view

---

## Pyramid Structure

```
Row 5 (Top):              [TV 1]
                         /      \
Row 4:              [TV 2]      [TV 3]
                   /     \      /     \
Row 3:        [TV 4] [TV 5] [TV 6] [TV 7]
             /   \   /   \   /   \   /   \
Row 2:   [TV 8][TV 9][TV 10][TV 11][TV 12][TV 13]
Row 1:        [TV 14 - Foundation]
```

**Total**: 14 TVs (1-2-3-4-4 row configuration)

---

## Timestamp Mapping

| TV# | Timestamp | Title | Seconds |
|-----|-----------|-------|---------|
| 1 | 00:00 | Out of Life | 0 |
| 2 | 02:11 | Flashing Lights | 131 |
| 3 | 04:22 | How to Break Off an Engagement | 262 |
| 4 | 06:33 | Nevermore | 393 |
| 5 | 08:44 | Bloodline | 524 |
| 6 | 10:55 | Resurrecting Atlantis | 655 |
| 7 | 13:06 | DJ Turn Me Up | 786 |
| 8 | 15:17 | Newly Single | 917 |
| 9 | 17:28 | Yet Heard | 1048 |
| 10 | 19:39 | Magic Ride | 1179 |
| 11 | 21:50 | Reunion | 1310 |
| 12 | 24:01 | How to Win My Heart | 1441 |
| 13 | 06:00 | Interlude | 360 |
| 14 | 12:00 | Bridge | 720 |

---

## Technical Details

### Built From
- **Base**: `video_stacker_∞_you_tube_css_3_d_edition.html`
- **Modifications**: Removed physics, drop mechanics, gameplay
- **Architecture**: Static scene generation

### Stack
- **Three.js** 0.128.0 (WebGL rendering)
- **CSS3DRenderer** (YouTube iframes in 3D)
- **YouTube IFrame API** (video playback)

### Key Features
- ✅ Pre-positioned static TVs (no physics)
- ✅ Timestamp-based YouTube embeds
- ✅ Simultaneous playback of 14 streams
- ✅ Optional camera orbit
- ✅ Global mute control
- ✅ YouTube controls enabled on each TV
- ✅ LED pulse animations
- ✅ Dramatic lighting (spotlights + rim lights)

---

## Controls

### UI Buttons (Top Right)
- **⟲** — Toggle automatic camera orbit (slow rotation around pyramid)
- **🔊/🔇** — Mute/unmute all TVs simultaneously
- **⌂** — Reset camera to default position

### YouTube Controls
Each TV has **embedded YouTube controls**:
- Play/Pause
- Seek bar (scrub through video)
- Volume slider
- Fullscreen

**Note**: Controls are interactive—click directly on any TV.

---

## Customization

### Change Video

Edit in `pyramid-scene.html`:
```javascript
const VIDEO_ID = 'MT3snSsqcHs'; // Replace with your YouTube ID
```

### Change Timestamps

Edit the `TIMESTAMPS` array:
```javascript
const TIMESTAMPS = [
  { label: 'Section 1', time: 0 },
  { label: 'Section 2', time: 120 },
  // ... 14 total entries
];
```

### Change Pyramid Formation

Edit `PYRAMID_ROWS`:
```javascript
const PYRAMID_ROWS = [1, 2, 3, 4, 4]; // rows from top to bottom
// Or try: [2, 3, 4, 5] for 14 TVs
// Or: [1, 3, 5, 5] for different shape
```

### Adjust TV Size

```javascript
const TV = { w:0.64, h:0.42, d:0.46 }; // width, height, depth
```

### Modify Camera Position

In `init()`:
```javascript
camera.position.set(0, 2.5, 6); // x, y, z
camera.lookAt(0, 1.8, 0);       // look at point
```

---

## Performance

### Expected Load
- **14 YouTube iframes** playing simultaneously
- **28 WebGL meshes** (2 per TV: shell + bezel)
- **Target**: 60 FPS on modern desktop, 30+ FPS on mobile

### Optimization Tips

1. **Reduce active players**:
   ```javascript
   // In createStaticTV(), change playerVars:
   autoplay: 0, // Don't autoplay
   ```

2. **Lower resolution**:
   ```javascript
   const pxW = 256; // Down from 384
   ```

3. **Disable shadows**:
   ```javascript
   renderer.shadowMap.enabled = false;
   ```

4. **Simplify lighting**:
   ```javascript
   // Remove rim lights, keep only ambient + spotlight
   ```

---

## Interaction Modes

### Current: Exhibition Mode
- Static camera (or slow orbit)
- All videos play simultaneously
- Minimal UI
- Suitable for gallery installation

### Alternative Modes (Future)

**Solo Mode**:
- Click TV to solo its audio (mute others)
- Highlight focused TV

**Timeline Sync**:
- Global timeline scrubber
- All TVs sync to same time + offset

**Conductor Mode**:
- Play/pause all
- Individual volume sliders
- Performance interface

---

## Troubleshooting

### Videos Don't Load
- **Check YouTube ID**: Ensure `MT3snSsqcHs` is embeddable
- **Check network**: YouTube API requires internet
- **Browser console**: Look for YouTube API errors

### Poor Performance
- **Close other apps**: 14 videos is resource-intensive
- **Use Chrome/Edge**: Better WebGL performance than Safari
- **Reduce quality**: Edit `pxW` (iframe width)

### Audio Overlap
- **Click Mute button** (🔊 → 🔇)
- **Lower system volume**
- **Consider spatial audio** (see Advanced Features below)

### Camera Position Issues
- **Click ⌂ button** to reset camera
- **Disable orbit** (click ⟲ if pulsing)
- **Zoom**: Edit camera position in code

---

## Advanced Features (Code)

### Spatial Audio (3D Positioning)

Add to `createStaticTV()`:
```javascript
// Web Audio API spatial panner
const audioCtx = new AudioContext();
const panner = audioCtx.createPanner();
panner.panningModel = 'HRTF';
panner.positionX.value = position.x;
panner.positionY.value = position.y;
panner.positionZ.value = position.z;
// Connect YouTube audio through panner
```

### Distance-Based Volume

Add to `animate()`:
```javascript
// Closer TVs are louder
tvs.forEach(tv => {
  const dist = tv.group.position.distanceTo(camera.position);
  const volume = Math.max(0, 1 - (dist / 10));
  if (tv.player && tv.player.setVolume) {
    tv.player.setVolume(volume * 100);
  }
});
```

### Click to Solo TV

```javascript
// In init(), add click handler
cssRenderer.domElement.addEventListener('click', (e) => {
  // Raycast to find clicked TV
  // Mute all except clicked
});
```

### Glow Effect on Active TVs

```javascript
// Add to each TV in createStaticTV()
const glowGeo = new THREE.PlaneGeometry(TV.w * 0.9, TV.h * 0.75);
const glowMat = new THREE.MeshBasicMaterial({
  color: 0x00ff88,
  transparent: true,
  opacity: 0.15,
  side: THREE.BackSide
});
const glow = new THREE.Mesh(glowGeo, glowMat);
glow.position.z = TV.d/2 + 0.06;
g.add(glow);
```

---

## Gallery Installation Setup

### Kiosk Mode (Fullscreen, No UI)

Add to `<body>` tag:
```html
<body onload="document.documentElement.requestFullscreen()">
```

Or press **F11** in browser.

### Auto-Start Orbit

In `init()`:
```javascript
orbitEnabled = true; // Start orbiting immediately
```

### Hide UI

Add CSS:
```css
#info, #controls { display: none !important; }
```

### Loop Video

Already enabled in `playerVars`:
```javascript
loop: 1,
playlist: VIDEO_ID // Required for looping
```

---

## File Structure

```
pyramid-scene.html
├── [HEAD]
│   ├── Three.js (WebGL)
│   ├── CSS3DRenderer
│   └── YouTube IFrame API
├── [STYLE]
│   ├── Dark theme (#000 bg, #0f0 accent)
│   ├── Minimal UI overlays
│   └── YouTube iframe styling
└── [SCRIPT]
    ├── CONFIG (VIDEO_ID, TIMESTAMPS, PYRAMID_ROWS)
    ├── generatePyramidPositions() → [{x,y,z,index}]
    ├── createStaticTV(pos, timestamp, index) → TV object
    ├── init() → create scene + 14 TVs
    └── animate() → render loop + LED pulses
```

---

## Conceptual Framework

### From Gameplay to Installation

**VIDEO_STACKER_∞ (original)**:
- Physics-based precarity
- User interaction required
- Failure is the narrative arc
- **Time**: Real-time, player-driven

**Pyramid Scene**:
- Spatial fragmentation
- Pre-composed static structure
- Stability as starting condition
- **Time**: Video time, multi-linear

### The New Metaphor

**Not**: Attention as weight that collapses  
**But**: Time as space that fragments

Same technology, **opposite philosophy**.

### Temporal Sculpture

Each TV is a **window** into the same temporal stream at different moments:
- Top TV (00:00) = beginning
- Bottom TVs = middle passages
- Simultaneous playback = **temporal simultaneity made spatial**

The viewer experiences:
- **Vertical reading** (scan pyramid from top to bottom)
- **Parallel listening** (multiple timelines overlapping)
- **Fragmented narrative** (no single linear progression)

---

## Connections to Existing Files

### Derived From
- `video_stacker_∞_you_tube_css_3_d_edition.html` (base architecture)

### Key Differences
| Feature | Original | Pyramid Scene |
|---------|----------|---------------|
| Physics | ✅ Cannon.js | ❌ Removed |
| User drops TVs | ✅ | ❌ Pre-positioned |
| Stability check | ✅ | ❌ Always stable |
| Collapse | ✅ Game over | ❌ No failure |
| Camera | Dynamic | Static/orbit |
| Videos | Sequential | Simultaneous |
| Interaction | Gameplay | Observation |

### Shared Tech
- ✅ Three.js scene
- ✅ CSS3DRenderer
- ✅ YouTube IFrame API
- ✅ Dramatic lighting
- ✅ LED indicators

---

## Credits & References

**Based on**: VIDEO_STACKER_∞ project  
**See**: `ANALYSIS.md`, `MANIFEST.md` for full context  
**Blueprint**: `BLUEPRINT_PYRAMID_SCENE.md`

**Video**: "Out of Life" — [MT3snSsqcHs](https://youtu.be/MT3snSsqcHs)

---

## Next Steps

### Enhancements
- [ ] Add spatial audio (3D sound positioning)
- [ ] Implement solo mode (click to focus one TV)
- [ ] Add timeline scrubber (sync all TVs)
- [ ] Create conductor interface (volume mixing)
- [ ] Export to Electron (desktop app for gallery)

### Alternative Formations
- [ ] Try different pyramid shapes (1-3-5-5, 2-3-4-5)
- [ ] Experiment with circular arrangements
- [ ] Test vertical tower (single column)
- [ ] Create double pyramid (⧖ shape)

### Content Experiments
- [ ] Different videos per TV (not timestamps)
- [ ] Live streams instead of recorded videos
- [ ] Generative video (shader-based)
- [ ] User-submitted video URLs

---

**Status**: Ready for exhibition · Self-contained · No dependencies beyond libraries

— Pyramid Scene Implementation Complete · 2024
