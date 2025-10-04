# VIDEO_STACKER_∞ — GIZMO EDITION
## Complete Implementation Roadmap

**Status**: vs-plu.html has foundation ready. Full GIZMO EDITION requires staged implementation.

---

## ✅ PHASE 1: COMPLETED (vs-plu.html)

### Core Infrastructure
- ✅ Three.js + Cannon.js physics system
- ✅ CSS3D renderer for video surfaces
- ✅ TV creation with unique IDs
- ✅ Metadata system (tags, layers, notes)
- ✅ Scene save/export as JSON
- ✅ Keyboard shortcuts (20+ commands)

### Visual Systems
- ✅ **Animated water shader** (caustic effects, wave motion)
- ✅ **4 environments** (CALM, ENERGETIC, VOID, GALLERY)
- ✅ **TV ID labels on frame** (cyan text on bezel)
- ✅ **8 camera presets** optimized for mobile
- ✅ Cinematic lighting with fog

### Controls
- ✅ V - Cycle camera presets
- ✅ 1-8 - Jump to specific camera
- ✅ E - Cycle environments
- ✅ F - Fill to 100 TVs
- ✅ I - Toggle ID visibility
- ✅ Ctrl+S - Save scene

---

## 🚧 PHASE 2: GIZMO SYSTEM (Priority 1)

### 2.1 Visual Gizmos
**File**: Create `gizmo-system.js` module

```javascript
class TVGizmo {
  constructor(tv) {
    this.tv = tv;
    this.arrows = this.createTranslateArrows();
    this.rings = this.createRotationRings();
    this.stabilityRing = this.createStabilityIndicator();
  }
  
  createTranslateArrows() {
    // X/Z plane drag arrows (red/blue)
    // Y lift handle (green)
    // Touch-friendly hit targets
  }
  
  createRotationRings() {
    // Y-axis rotation (15° snap)
    // X/Z tilt (±10° range)
  }
  
  createStabilityIndicator() {
    // Ground ring: green→amber→red
    // Shows center of mass projection
  }
}
```

**Tasks**:
- [ ] ArrowHelper meshes for X/Y/Z axes
- [ ] Torus rings for rotation
- [ ] Ground projection circle with color gradient
- [ ] Raycasting for gizmo interaction
- [ ] Snap-to-grid feedback (visual glow)
- [ ] Touch event handlers (long-press to activate)

**Estimated**: 2-3 hours

---

## 🚧 PHASE 3: FIVE MODES (Priority 2)

### 3.1 Mode Framework
```javascript
const MODES = {
  BUILD: {
    physics: 'gentle',
    gizmos: true,
    ui: ['drop', 'nudge', 'snap', 'tag'],
    camera: 'orbit'
  },
  GAME: {
    physics: 'strict',
    gizmos: false,
    ui: ['drop', 'nudge_paddles'],
    camera: 'track_top',
    scoring: true
  },
  LIBRARY: {
    physics: false,
    layout: 'grid',
    ui: ['search', 'filter', 'tag'],
    camera: 'overview'
  },
  ZETTEL: {
    physics: false,
    layout: 'graph',
    ui: ['search', 'link', 'tag'],
    camera: 'graph_view'
  },
  WATER: {
    physics: 'damped',
    gizmos: false,
    ui: ['exit'],
    camera: 'slow_orbit',
    ambient: true
  }
};
```

### 3.2 Mode-Specific Features

**BUILD Mode**:
- [ ] Gizmo appears on TV select
- [ ] Snap-to-grid toggle
- [ ] Multi-select with Shift
- [ ] Group operations
- [ ] Undo/redo stack

**GAME Mode**:
- [ ] Score system (height + stability)
- [ ] Next TV preview in HUD
- [ ] Edge nudge paddles (◀ ▶)
- [ ] Topple detection → debris particles
- [ ] Combo/streak tracking
- [ ] High score persistence

**LIBRARY Mode**:
- [ ] Grid/ring layout algorithm
- [ ] Tag filter UI
- [ ] Search box (live filter)
- [ ] Tap TV → play preview
- [ ] Thumbnail generation

**ZETTEL MAP Mode**:
- [ ] Force-directed graph layout
- [ ] Tag clustering
- [ ] Link visualization (lines between TVs)
- [ ] Node selection → focus in 3D
- [ ] Graph export (GraphJSON)

**WATER/CALM Mode**:
- [ ] Hide UI except exit button
- [ ] Enhance water intensity
- [ ] Soft ambient audio loop
- [ ] Buoyancy physics (spring dampers)
- [ ] Slow automatic orbit

**Estimated**: 4-6 hours

---

## 🚧 PHASE 4: HOLOGRAPHIC LAYERS (Priority 3)

### 4.1 Layer Compositing System
```javascript
class HoloLayer {
  constructor(config) {
    this.type = config.type; // 'video'|'image'|'text'|'shader'
    this.ref = config.ref;
    this.opacity = config.opacity || 1.0;
    this.blendMode = config.blendMode || 'add';
    this.zIndex = config.zIndex || 0;
    this.parallax = config.parallax || 0.05;
  }
  
  render(scene, camera) {
    // Render on HOLO layer with additive blend
    // Apply parallax offset based on camera position
  }
}
```

**Tasks**:
- [ ] Second render pass for HOLO layer
- [ ] Additive blending shader
- [ ] Per-TV layer stack UI
- [ ] Drag-to-reorder layers
- [ ] Opacity sliders
- [ ] Parallax calculation

**Estimated**: 3-4 hours

---

## 🚧 PHASE 5: MOBILE UX POLISH (Priority 1)

### 5.1 Touch Gestures
```javascript
const TouchHandler = {
  singleTap: (pos) => { selectTV(pos); },
  doubleTap: (pos) => { focusTV(pos); setCameraPreset('Close-up'); },
  longPress: (pos) => { showContextMenu(pos); },
  pinch: (scale) => { camera.zoom *= scale; },
  twoFingerDrag: (delta) => { orbitCamera(delta); },
  threeFingerSwipe: (dir) => { switchMode(dir); }
};
```

**Tasks**:
- [ ] Pointer event consolidation
- [ ] Gesture recognition
- [ ] Safe-area inset handling
- [ ] Bottom toolbar for thumb reach
- [ ] Large hit targets (min 44px)
- [ ] Haptic feedback (Vibration API)
- [ ] Orientation lock option

**Estimated**: 2-3 hours

---

## 🚧 PHASE 6: EDL & ZETTELKASTEN EXPORT (Priority 2)

### 6.1 Export Formats

**EDL JSON** (CMX-style):
```json
{
  "title": "My Scene",
  "framerate": 30,
  "edl": [
    {
      "id": "TV-001",
      "in": 0,
      "out": 136,
      "source": {"type": "youtube", "ref": "uDUoMnp1z_g"},
      "label": "Out of Life",
      "tags": ["intro", "poem:river"]
    }
  ]
}
```

**Zettelkasten Graph JSON**:
```json
{
  "nodes": [
    {"id": "TV-001", "label": "Out of Life", "tags": ["intro"], "x": 0, "y": 3, "z": 0}
  ],
  "links": [
    {"source": "TV-001", "target": "TV-005", "type": "backlink"},
    {"source": "TV-001", "target": "TV-003", "type": "tag:poem"}
  ]
}
```

**Tasks**:
- [ ] EDL formatter
- [ ] Graph builder from tags/backlinks
- [ ] CSV export for spreadsheet
- [ ] PNG snapshot (canvas.toDataURL)
- [ ] URL hash compression (gzip + base64)
- [ ] Import scene from JSON/hash

**Estimated**: 2-3 hours

---

## 🚧 PHASE 7: LAYOUT ALGORITHMS (Priority 2)

### 7.1 Spatial Arrangements

Already defined in vs-plu.html, need implementation:

```javascript
function applyLayout(layoutType) {
  tvs.forEach((tv, i) => {
    const pos = getLayoutPosition(i, layoutType, tvs.length);
    
    if (tv.body) {
      // Animate to position
      tv.body.position.set(pos.x, pos.y, pos.z);
      tv.body.velocity.set(0, 0, 0);
      tv.body.wakeUp();
    }
  });
}

function getLayoutPosition(index, layout, total) {
  switch(layout) {
    case 'TETRIS':
      // Random gaps, stackable blocks
      return calculateTetrisPosition(index);
    case 'MINECRAFT':
      // 16x16 chunks with variable height
      return calculateMinecraftPosition(index);
    // ... etc
  }
}
```

**Tasks**:
- [ ] Implement all 7 layout algorithms
- [ ] Smooth animation between layouts
- [ ] Physics disable during layout change
- [ ] Preview mode (ghost TVs show target positions)

**Estimated**: 3-4 hours

---

## 🚧 PHASE 8: PERFORMANCE OPTIMIZATION (Priority 3)

### 8.1 Techniques

**LOD (Level of Detail)**:
```javascript
function updateLOD() {
  tvs.forEach(tv => {
    const distance = camera.position.distanceTo(tv.group.position);
    
    if (distance > 15) {
      tv.cssObj.visible = false; // Hide video
      tv.useSimpleGeometry = true; // Low-poly mesh
    } else if (distance > 8) {
      tv.videoQuality = 'low'; // Reduce texture size
    }
  });
}
```

**Video Texture Management**:
```javascript
function pauseOffscreenVideos() {
  tvs.forEach(tv => {
    if (!isInViewFrustum(tv, camera)) {
      if (tv.video && tv.video.paused === false) {
        tv.video.pause();
      }
    }
  });
}
```

**Tasks**:
- [ ] Frustum culling
- [ ] Video pause/resume based on visibility
- [ ] Texture disposal on TV delete
- [ ] Geometry instancing for repeated TVs
- [ ] FPS monitoring and auto-quality adjustment
- [ ] requestVideoFrameCallback when available

**Estimated**: 2-3 hours

---

## 🚧 PHASE 9: ACCESSIBILITY (Priority 2)

### 9.1 Features

**Screen Reader Support**:
```html
<button aria-label="Drop new TV (Spacebar)" role="button">
  ➕
</button>
```

**Reduced Motion**:
```javascript
const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

if (prefersReducedMotion) {
  waterIntensity = 0;
  gizmoAnimations = false;
  cameraEasing = 0; // Instant movement
}
```

**Tasks**:
- [ ] ARIA labels on all buttons
- [ ] Keyboard navigation for modal
- [ ] High contrast theme
- [ ] Caption toggle for videos
- [ ] Focus indicators
- [ ] Reduced motion mode

**Estimated**: 2 hours

---

## 🚧 PHASE 10: SOUND & HAPTICS (Priority 3)

### 10.1 Audio System
```javascript
const AudioSystem = {
  sounds: {
    drop: new Audio('data:audio/wav;base64,...'),
    impact: new Audio('data:audio/wav;base64,...'),
    snap: new Audio('data:audio/wav;base64,...'),
    topple: new Audio('data:audio/wav;base64,...')
  },
  
  play(name, volume = 1.0) {
    if (!this.muted && this.sounds[name]) {
      this.sounds[name].volume = volume;
      this.sounds[name].currentTime = 0;
      this.sounds[name].play();
    }
  }
};
```

### 10.2 Haptic Patterns
```javascript
const HapticPatterns = {
  drop: [10], // Light
  impact: [20, 10, 20], // Medium bounce
  topple: [50, 30, 50, 30, 50], // Warning pattern
  snap: [5], // Subtle
  success: [10, 20, 10, 20, 30] // Celebration
};

function haptic(pattern) {
  if (navigator.vibrate && settings.haptics) {
    navigator.vibrate(HapticPatterns[pattern]);
  }
}
```

**Tasks**:
- [ ] Generate short audio buffers (WebAudio)
- [ ] Volume control slider
- [ ] Mute toggle (persist)
- [ ] Haptic patterns for each action
- [ ] Haptic settings toggle

**Estimated**: 1-2 hours

---

## 📦 PHASE 11: SINGLE-FILE BUILD (Final)

### 11.1 Inline Everything

Currently uses CDN for Three.js/Cannon.js. For true single-file:

**Option A: Minimal Custom Build**
```javascript
// Inline only what we use from Three.js
const THREE = (function() {
  // PerspectiveCamera, Scene, WebGLRenderer, Mesh, BoxGeometry...
  // ~50KB minified for essentials
})();
```

**Option B: Use lightweight alternatives**
```javascript
// babylon.js core (smaller)
// or custom WebGL renderer (most work)
```

**Tasks**:
- [ ] Extract Three.js essentials
- [ ] Inline Cannon-es (or switch to Matter.js)
- [ ] Base64 encode demo videos/images
- [ ] Minify inline CSS
- [ ] Total file size target: <500KB

**Estimated**: 4-6 hours

---

## 🎯 IMPLEMENTATION PRIORITY MATRIX

| Phase | Priority | Time | Complexity | User Impact |
|-------|----------|------|------------|-------------|
| 2: Gizmos | **HIGH** | 3h | Medium | Huge |
| 5: Mobile UX | **HIGH** | 3h | Medium | Huge |
| 3: Modes | HIGH | 5h | High | Large |
| 6: Export | MEDIUM | 3h | Medium | Medium |
| 7: Layouts | MEDIUM | 4h | Medium | Medium |
| 4: Holo Layers | MEDIUM | 4h | High | Medium |
| 8: Performance | MEDIUM | 3h | High | Large (mobile) |
| 9: Accessibility | MEDIUM | 2h | Low | Medium |
| 10: Sound/Haptics | LOW | 2h | Low | Small |
| 11: Single-file | LOW | 5h | High | Small |

**Total Estimated Time**: 34-42 hours

---

## 🚀 SUGGESTED IMPLEMENTATION ORDER

### Sprint 1 (8-10 hours) - **Core Functionality**
1. ✅ Phase 1 done (vs-plu.html foundation)
2. Phase 2: Gizmo system
3. Phase 5: Mobile touch gestures
4. Phase 3: BUILD + GAME modes

**Deliverable**: Playable tower-stacking game with gizmo editing

### Sprint 2 (6-8 hours) - **Organization**
1. Phase 3: LIBRARY + ZETTEL modes
2. Phase 6: EDL/Zettelkasten export
3. Phase 7: Layout algorithms

**Deliverable**: Full media organization system

### Sprint 3 (4-6 hours) - **Polish**
1. Phase 3: WATER/CALM mode enhancements
2. Phase 4: Holographic layers
3. Phase 8: Performance optimization

**Deliverable**: Complete feature set

### Sprint 4 (3-4 hours) - **Accessibility & Final**
1. Phase 9: Accessibility features
2. Phase 10: Sound & haptics
3. Final testing & bug fixes

**Deliverable**: Production-ready application

### Sprint 5 (Optional, 5+ hours) - **Single-file**
1. Phase 11: Inline all dependencies
2. Optimize & minify
3. Deploy version

---

## 📝 CURRENT STATUS

**vs-plu.html** has:
- ✅ Foundation (Three.js + Cannon.js)
- ✅ TV system with IDs on frame
- ✅ 8 camera presets
- ✅ Water shader
- ✅ Keyboard controls
- ✅ Scene save

**Ready to start**: Phase 2 (Gizmos) or Phase 5 (Mobile UX)

**Blockers**: None. All dependencies available.

---

## 🎬 NEXT STEPS

1. **Choose sprint approach** or **incremental feature adds**
2. **Test vs-plu.html** with current improvements
3. **Prioritize**: Gizmos vs Mobile gestures?
4. **Set milestone**: Playable game? Full Zettelkasten? Both?

**Would you like me to start implementing Phase 2 (Gizmos) or Phase 5 (Mobile Touch) next?**
