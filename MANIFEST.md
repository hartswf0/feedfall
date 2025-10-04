# VIDEO_STACKER_∞ — Project Manifest

## Project Overview

**VIDEO_STACKER_∞** is an experimental web application exploring physics-based video stacking through gamified interaction. It combines Three.js 3D rendering, physics simulation, and video playback into an embodied media experience.

---

## File Structure & Status

### 🟢 Active Production Files

| File | Purpose | Status | Tech Stack | Priority |
|------|---------|--------|------------|----------|
| `video_stacker_∞_index.html` | Main production build | ✅ Active | ES Modules, Local Video | **Primary** |
| `vs-stacker.html` | Advanced controls version | ✅ Active | YouTube, Full Features | **Secondary** |
| `video_stacker_∞_mobile_swipe_right_edge_controls_haptics_audio_index.html` | Mobile-optimized | ✅ Active | ES Modules, Touch UI | **Mobile** |
| `video_stacker_∞_you_tube_css_3_d_edition.html` | YouTube-focused | ✅ Active | YouTube API, CSS3D | **Platform** |

### 🟡 Prototype/Development Files

| File | Purpose | Status | Notes |
|------|---------|--------|-------|
| `video-02.html` | Local video prototype | 🔧 Prototype | ES Modules testbed |
| `video-refactor.html` | Optimization experiment | 🔧 Prototype | Audio/haptics focus |
| `video_full.html` | Simplified core demo | 🔧 Prototype | Teaching/embed use |

### 🔴 Deprecated Files (Duplicates)

| File | Status | Action |
|------|--------|--------|
| `video-01.html` | ❌ Duplicate of index.html | Mark for deletion |
| `video-stacker-02.html` | ❌ Duplicate of video-02.html | Mark for deletion |

### 📄 Documentation

| File | Purpose |
|------|---------|
| `ANALYSIS.md` | Deep technical & philosophical analysis |
| `MANIFEST.md` | This file — project structure |
| `README.md` | User-facing documentation (to be created) |

---

## Technology Matrix

### Core Dependencies

**3D Rendering:**
- Three.js (r128 legacy, 0.160-0.161 modern)
- CSS3DRenderer (for YouTube iframes)
- OrbitControls (ES module versions only)

**Physics:**
- Cannon.js 0.6.2 (legacy CDN)
- cannon-es 0.20.0 (modern ES modules)

**Video:**
- YouTube IFrame API (platform versions)
- HTML5 `<video>` (local versions)
- VideoTexture (Three.js)

**Audio/Haptics:**
- Web Audio API (procedural synthesis)
- Navigator.vibrate (haptic feedback)

### Import Strategies

**Legacy (Script Tags):**
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/renderers/CSS3DRenderer.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/cannon.js/0.6.2/cannon.min.js"></script>
```

**Modern (ES Modules):**
```html
<script type="importmap">
{
  "imports": {
    "three": "https://unpkg.com/three@0.160.0/build/three.module.js",
    "three/addons/": "https://unpkg.com/three@0.160.0/examples/jsm/"
  }
}
</script>
<script type="module">
import * as THREE from 'three';
import * as CANNON from 'https://cdn.jsdelivr.net/npm/cannon-es@0.20.0/dist/cannon-es.js';
</script>
```

---

## Feature Comparison

### Core Mechanics (All Files)
- ✅ Physics-based TV stacking
- ✅ Stability calculation
- ✅ Collapse on failure
- ✅ Score/height/streak tracking
- ✅ High score persistence (localStorage)

### Advanced Features (By File)

| Feature | index.html | vs-stacker | mobile_swipe | youtube_css3d | video_∞_index |
|---------|------------|------------|--------------|---------------|---------------|
| **YouTube Integration** | ✅ | ✅ | ❌ | ✅ | ❌ |
| **Local Video** | ❌ | ❌ | ✅ | ❌ | ✅ |
| **Swipe Gestures** | Basic | Advanced | **Best** | Basic | Basic |
| **Remote Controls** | ❌ | **✅** | ❌ | ❌ | ❌ |
| **Focus System** | ❌ | **✅** | ❌ | ❌ | ❌ |
| **Playlist Editor** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Haptic Feedback** | ✅ | **Best** | **Best** | ✅ | ✅ |
| **Procedural Audio** | ✅ | **Best** | **Best** | ✅ | ❌ |
| **Camera Presets** | 4 | 4 | 5 | 5 | 5 |
| **Auto Mode** | ✅ | ✅ | ❌ | **✅** | ❌ |
| **Exhibit Mode** | ❌ | ❌ | ❌ | **✅** | **✅** |
| **Self-Tests** | ❌ | **✅** | **✅** | ❌ | **✅** |
| **UI Auto-Hide** | ❌ | **✅** | **✅** | ❌ | ❌ |
| **Next Preview** | ❌ | ❌ | ❌ | ❌ | **✅** |
| **Idle Hiss Mode** | ❌ | ❌ | ❌ | ❌ | **✅** |

---

## Physics Configuration

### TV Dimensions (Standardized)
```javascript
const TV = { w: 0.60, h: 0.40, d: 0.45 }; // width, height, depth in world units
```

### Physics Constants

| Constant | Value | Purpose |
|----------|-------|---------|
| `gravity` | -9.8 to -9.82 | Falling acceleration |
| `GAP_Y` | 0.05 | Vertical spawn spacing |
| `PHYS_LIMIT` | 0.22 | Stability threshold |
| `STAB_ALPHA` | 0.7 | Overhang penalty weight |
| `K` / `WINDOW_K` | 6 | Recent TVs for stability calc |
| `sleepSpeedLimit` | 0.1 | Body sleep threshold |
| `sleepTimeLimit` | 0.4-0.8 | Time before sleep |
| `linearDamping` | 0.05-0.32 | Air resistance |
| `angularDamping` | 0.3-0.45 | Rotation damping |
| `friction` | 0.6-0.65 | Contact friction |
| `restitution` | 0.05 | Bounce factor |

### Collapse Triggers
- Stability < 0 → Game Over
- Slow-motion: `gravity *= 0.3-0.35`
- Debris: 48-64 shards, 2.8-3s TTL

---

## UI/UX Patterns

### Themes

**Retro Green (default):**
```css
--ui: #0f0;
--bg: #000;
--glow: rgba(0,255,0,0.35);
```

**Neon Cyan (video-refactor):**
```css
--accent: #51e0c1;
--warn: #ff5a5f;
--ok: #65f28a;
```

**Blue Glass (video_∞_index):**
```css
--ink: #e9f0ff;
--accent: #51e0c1;
--glass: #86d1ff;
```

### Control Layouts

**Desktop:** Right-side floating controls + bottom dock
**Mobile:** Edge rails (left utility, right gameplay) + gesture hints
**Advanced:** Remote panel (vs-stacker only)

---

## Performance Optimizations

### Video Playback Budget
- **TOP_N_LIVE**: 6 (only top 6 TVs play video simultaneously)
- **MAX_ACTIVE_PLAYERS**: 6 (YouTube version)
- **Player Recycling**: Pause inactive players, unpause when in top-N

### Rendering
- **pixelRatio**: Capped at 1.5-1.7 (mobile performance)
- **Shadow maps**: Enabled but limited to key light
- **Fog**: Used to hide distant geometry

### Physics
- **Fixed timestep**: 1/60 or 1/120
- **Broadphase**: SAPBroadphase (Sweep and Prune)
- **Sleep**: Bodies sleep when stable (reduces computation)

---

## Input Methods

### Touch Gestures

**Swipe Up** → Drop TV  
**Swipe Left/Right** → Nudge falling TV  
**Swipe Down** → Cull bottom TV (mobile_swipe version only)  
**Tap** → Focus TV (vs-stacker only)  

### Button Controls

**Primary:**
- DROP (main action)
- NUDGE Left/Right
- CULL (remove bottom)

**Secondary:**
- View cycle (camera presets)
- Mute toggle
- Mode cycle (HYBRID/GAME/GALLERY)
- Autofall toggle

**Advanced (vs-stacker):**
- Focus Play/Pause/Mute
- Focus Prev/Next
- Replace Video ID
- Enable Pointer Events (6s window)
- Fullscreen Focus
- Global Play/Pause/Mute
- TOP_N slider (1-12)
- Playlist Apply/Shuffle
- Theme switcher
- UI visibility toggle

---

## Content Strategy

### YouTube Versions
**Video Source (Current Standard):**
```javascript
const VIDEO_ID = 'uDUoMnp1z_g'; // 13-segment video
const TIMESTAMPS = [
  0,      // Out of Life (0:00)
  136,    // Flashing Lights (2:16)
  272,    // How to Break Off an Engagement (4:32)
  408,    // Nevermore (6:48)
  544,    // Bloodline (9:04)
  680,    // Resurrecting Atlantis (11:20)
  816,    // DJ Turn Me Up (13:36)
  952,    // Newly Single (15:52)
  1088,   // Yet, Heard (18:08)
  1224,   // Magic Ride (20:24)
  1360,   // Reunion (22:40)
  1496,   // How to Win My Heart (24:56)
  1632    // Hot Minute (27:12)
];
```
**Embed Format:**
```
https://www.youtube.com/embed/{VIDEO_ID}?start={TIMESTAMP}&autoplay=1&mute=1&controls=1&playsinline=1&enablejsapi=1
```

### Local Video Versions
**Video Sources:**
```javascript
const FEED = ['/videos/a.mp4', '/videos/b.mp4', '/videos/c.mp4'];
```
**Fallback:** Noise shader (procedural static) if video fails to load

---

## Audio Design

### Procedural Synthesis (Web Audio API)

**Sound Dictionary:**
- `drop`: 220-120 Hz, 0.25s (TV spawns)
- `land`: 160-90 Hz, 0.12s (TV settles)
- `nudge`: 320-520 Hz, 0.06-0.08s (lateral impulse)
- `collapse`: 220-40 Hz, 0.9s (game over)

**Implementation Pattern:**
```javascript
function makeSound(f0, f1, duration, gain) {
  const osc = audioCtx.createOscillator();
  const gainNode = audioCtx.createGain();
  osc.connect(gainNode).connect(audioCtx.destination);
  osc.frequency.setValueAtTime(f0, audioCtx.currentTime);
  osc.frequency.exponentialRampToValueAtTime(f1, audioCtx.currentTime + duration);
  gainNode.gain.setValueAtTime(gain, audioCtx.currentTime);
  gainNode.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + duration);
  osc.start();
  osc.stop(audioCtx.currentTime + duration);
}
```

### Haptic Patterns

| Event | Pattern | Duration (ms) |
|-------|---------|---------------|
| Light | Single pulse | 10 |
| Medium | Single pulse | 20 |
| Heavy | Single pulse | 35 |
| Success | Triple pulse | [10, 40, 10] |
| Error | Quintuple pulse | [30, 80, 30, 80, 30] |

---

## Testing Infrastructure

### Self-Test Harness (ES Module Versions)

**Coverage:**
- ✅ Library loading (Three.js, Cannon-es, OrbitControls)
- ✅ Initialization (scene, world, camera)
- ✅ Physics step execution
- ✅ TV spawn mechanics
- ✅ Stability calculation
- ✅ Playlist manipulation
- ✅ UI state toggling (vs-stacker)

**Invocation:**
```javascript
// Automatic on load
runSelfTests();

// Or manual via URL
// ?test=1
```

**Output:**
- Console table with pass/fail
- Toast notification with summary
- Test status footer (vs-stacker)

---

## Deployment Considerations

### Browser Compatibility

**Minimum Requirements:**
- ES6 (ES2015) support
- WebGL 1.0
- Web Audio API
- CSS3 transforms
- Pointer Events or Touch Events

**Optimal:**
- ES Modules support (Safari 10.1+, Chrome 61+, Firefox 60+)
- CSS3D transforms
- Vibration API (mobile)

### Asset Dependencies

**YouTube Versions:**
- ⚠️ Requires YouTube IFrame API availability
- ⚠️ Subject to YouTube embedding policies
- ⚠️ Video availability can change

**Local Video Versions:**
- ✅ Requires `/videos/` directory with MP4 files
- ✅ Fallback to noise shader if videos missing
- ✅ No external dependencies

### Performance Targets

**Desktop:**
- 60 FPS @ 1080p
- Up to 20 stacked TVs

**Mobile:**
- 60 FPS @ 720p (with pixelRatio cap)
- Up to 12 stacked TVs
- TOP_N_LIVE reduced to 4-6

---

## Roadmap & Future Work

### Phase 1: Consolidation (Current)
- [x] Deep analysis (ANALYSIS.md)
- [x] Manifest creation (this file)
- [ ] Remove duplicates
- [ ] Create unified README.md
- [ ] Rewrite index.html as synthesis

### Phase 2: Architecture
- [ ] Extract shared modules
  - [ ] `physics-engine.js`
  - [ ] `ui-components.js`
  - [ ] `audio-haptics.js`
  - [ ] `config.js`
- [ ] Create theme system
- [ ] Add package.json
- [ ] Build process (optional)

### Phase 3: Features
- [ ] Multiplayer (WebRTC or server)
- [ ] Leaderboard (backend + database)
- [ ] User video upload
- [ ] Playlist sharing
- [ ] Replay system
- [ ] Screenshot/video export

### Phase 4: Platform
- [ ] PWA (Progressive Web App)
- [ ] Offline support
- [ ] Installation prompts
- [ ] App store submission (mobile)

---

## Contributing Guidelines

### Code Style
- **Indentation**: 2 spaces (consistent across files)
- **Naming**: camelCase for variables, UPPER_SNAKE for constants
- **Comments**: Section headers with `=====` or `/* ===== */`

### Adding New Features
1. Identify base file (see Priority in file table)
2. Test in prototype file first
3. Document in ANALYSIS.md
4. Update this manifest
5. Merge to production file

### Testing Checklist
- [ ] Desktop Chrome/Firefox/Safari
- [ ] Mobile Chrome/Safari
- [ ] Touch + mouse input
- [ ] Portrait + landscape
- [ ] 1080p + 720p + 4K displays

---

## License & Attribution

**License**: [To be specified]

**Credits:**
- Three.js: MIT License
- Cannon.js / cannon-es: MIT License
- YouTube IFrame API: YouTube Terms of Service

**Author**: [To be specified]

---

## Contact & Support

**Repository**: [To be specified]  
**Issues**: [To be specified]  
**Documentation**: See `ANALYSIS.md` and `README.md`

---

**Last Updated**: 2024  
**Manifest Version**: 1.0  
**Project Status**: Active Development
