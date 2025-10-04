# BLUEPRINT: 14-TV Pyramid Scene — "Out of Life" Installation

## The Vision

**A static pyramid of 14 TVs**, each playing a different timestamp from the same YouTube video, creating a **temporal sculpture** where the viewer experiences the video fragmented across physical space.

**Video**: `MT3snSsqcHs` — "Out of Life" (24:01 total duration)  
**Formation**: Pyramid (1-2-3-4-4 row structure)  
**Interaction**: Static installation (no physics, no dropping)

---

## Timestamp Map

```
00:00  Out of Life                    → TV #1
02:11  Flashing Lights                → TV #2
04:22  How to Break Off an Engagement → TV #3
06:33  Nevermore                      → TV #4
08:44  Bloodline                      → TV #5
10:55  Resurrecting Atlantis          → TV #6
13:06  DJ Turn Me Up                  → TV #7
15:17  Newly Single                   → TV #8
17:28  Yet Heard                      → TV #9
19:39  Magic Ride                     → TV #10
21:50  Reunion                        → TV #11
24:01  How to Win My Heart            → TV #12
[Need 2 more timestamps]               → TV #13, #14
```

---

## Pyramid Structure (Spatial Layout)

```
Formation: 5 rows (bottom-up)

Row 5 (Top):           [TV1]
                      /      \
Row 4:           [TV2]        [TV3]
                /    \        /    \
Row 3:      [TV4]   [TV5]  [TV6]   [TV7]
           /   \    /   \   /   \   /   \
Row 2:  [TV8] [TV9][TV10][TV11][TV12][TV13]
        |_____|_____|_____|_____|_____|_____|
Row 1 (Base):      [TV14 - Foundation]

OR Alternative (1-2-3-4-4):
Row 5 (Top):              [TV1]
Row 4:                [TV2] [TV3]
Row 3:            [TV4] [TV5] [TV6]
Row 2:       [TV7] [TV8] [TV9] [TV10]
Row 1 (Base):[TV11][TV12][TV13][TV14]
```

**Recommended**: 1-2-3-4-4 pyramid (14 TVs total)

---

## File Analysis: Which Base to Use?

### Option 1: `video_stacker_∞_you_tube_css_3_d_edition.html` ★★★★★

**Strengths:**
- ✅ Pure CSS3D for YouTube (perfect for this)
- ✅ YouTube IFrame API integration
- ✅ Player management (`MAX_ACTIVE_PLAYERS`)
- ✅ Exhibit mode (hands-off operation)
- ✅ Clean architecture

**Required Modifications:**
- Remove physics (no Cannon.js needed)
- Remove drop mechanics
- Add pre-positioned TV creation
- Add timestamp parameter to YouTube embeds
- Disable user input (or make camera-only)

**Difficulty**: ⭐⭐ (Moderate - remove complexity)

---

### Option 2: `vs-stacker.html` ★★★★

**Strengths:**
- ✅ Advanced YouTube controls
- ✅ Focus system (could highlight active TV)
- ✅ Remote panel (could control playback)
- ✅ Per-TV control capabilities

**Required Modifications:**
- Remove physics
- Remove drop mechanics
- Add pre-positioned creation
- Add timestamp control
- Adapt remote for pyramid view

**Difficulty**: ⭐⭐⭐ (Moderate-High - lots of features to adapt)

---

### Option 3: Build from Scratch (Minimal) ★★★★★

**Strengths:**
- ✅ Only what's needed
- ✅ No legacy mechanics
- ✅ Clean, focused code

**Required:**
- Three.js scene + camera
- CSS3DRenderer
- YouTube IFrame API
- 14 pre-positioned TV meshes
- Timestamp-based YouTube embeds

**Difficulty**: ⭐⭐⭐⭐ (High - build everything)

---

## RECOMMENDED APPROACH

**Base File**: `video_stacker_∞_you_tube_css_3_d_edition.html`

**Why:**
1. Already has YouTube CSS3D integration
2. Exhibit mode for hands-off operation
3. Player management built-in
4. Clean separation of concerns
5. Easy to remove physics

**Strategy**: **Subtraction**, not addition

---

## Technical Blueprint

### Part 1: Remove Physics

```javascript
// DELETE these sections:
// - Cannon.js import
// - world = new CANNON.World()
// - All CANNON.Body creation
// - world.step() in animate loop
// - Collision detection
// - Drop mechanics
// - Stability calculation
```

### Part 2: Pyramid Generator

```javascript
// ADD: Pyramid position calculator
function generatePyramidPositions(rows = [1,2,3,4,4]) {
  const positions = [];
  const TV_W = 0.64, TV_H = 0.42;
  const GAP_X = 0.1, GAP_Y = 0.1;
  
  let tvIndex = 0;
  let currentY = 0;
  
  rows.forEach((count, rowIndex) => {
    const rowWidth = (count * TV_W) + ((count - 1) * GAP_X);
    const startX = -rowWidth / 2 + TV_W / 2;
    
    for (let i = 0; i < count; i++) {
      positions.push({
        x: startX + (i * (TV_W + GAP_X)),
        y: currentY,
        z: 0,
        index: tvIndex++
      });
    }
    currentY += TV_H + GAP_Y;
  });
  
  return positions;
}
```

### Part 3: Timestamp YouTube URLs

```javascript
// ADD: Timestamp data
const VIDEO_ID = 'MT3snSsqcHs';
const TIMESTAMPS = [
  { label: 'Out of Life', time: 0 },
  { label: 'Flashing Lights', time: 131 },          // 2:11
  { label: 'How to Break Off an Engagement', time: 262 }, // 4:22
  { label: 'Nevermore', time: 393 },                // 6:33
  { label: 'Bloodline', time: 524 },                // 8:44
  { label: 'Resurrecting Atlantis', time: 655 },    // 10:55
  { label: 'DJ Turn Me Up', time: 786 },            // 13:06
  { label: 'Newly Single', time: 917 },             // 15:17
  { label: 'Yet Heard', time: 1048 },               // 17:28
  { label: 'Magic Ride', time: 1179 },              // 19:39
  { label: 'Reunion', time: 1310 },                 // 21:50
  { label: 'How to Win My Heart', time: 1441 },     // 24:01
  { label: 'Interlude 1', time: 360 },              // 6:00 (filler)
  { label: 'Interlude 2', time: 720 }               // 12:00 (filler)
];

// Modified YouTube embed URL with start time
function makeYouTubeURL(videoId, startTime) {
  return `https://www.youtube.com/embed/${videoId}?start=${startTime}&autoplay=1&mute=0&controls=1&playsinline=1&enablejsapi=1`;
}
```

### Part 4: Static TV Creation

```javascript
// REPLACE: makeTV() function
function createStaticTV(position, timestamp, index) {
  // WebGL shell (visual only, no physics)
  const g = new THREE.Group();
  const shell = new THREE.Mesh(
    new THREE.BoxGeometry(TV.w, TV.h, TV.d),
    new THREE.MeshStandardMaterial({color:0x121212, roughness:.8, metalness:.25})
  );
  shell.castShadow = true;
  shell.receiveShadow = true;
  g.add(shell);

  // Bezel
  const bezel = new THREE.Mesh(
    new THREE.BoxGeometry(TV.w*0.86, TV.h*0.72, 0.02),
    new THREE.MeshStandardMaterial({color:0x0a0a0a, roughness:.7})
  );
  bezel.position.z = TV.d/2 + 0.01;
  g.add(bezel);

  // CSS3D YouTube iframe
  const pxW = 384, pxH = Math.round(pxW/SCREEN_RATIO);
  const surface = document.createElement('div');
  surface.className = 'yt-surface';
  surface.style.width = pxW + 'px';
  surface.style.height = pxH + 'px';
  surface.style.background = '#000';

  // YouTube player with timestamp
  let player = null;
  const makePlayer = () => {
    player = new YT.Player(surface, {
      width: pxW,
      height: pxH,
      videoId: VIDEO_ID,
      playerVars: {
        autoplay: 1,
        controls: 1,           // Enable controls for scrubbing
        modestbranding: 1,
        rel: 0,
        playsinline: 1,
        mute: 0,               // Unmuted for audio experience
        start: timestamp.time  // KEY: Start at specific timestamp
      },
      events: {
        onReady: (e) => {
          e.target.seekTo(timestamp.time, true);
        }
      }
    });
  };

  if (YT_READY) makePlayer();
  else pendingPlayerCbs.push(makePlayer);

  const cssObj = new THREE.CSS3DObject(surface);
  const scale = (TV.w*0.86) / pxW;
  cssObj.scale.set(scale, scale, 1);
  cssObj.position.z = TV.d/2 + 0.012;

  // Position in pyramid
  g.position.set(position.x, position.y, position.z);

  // Label overlay (optional)
  const labelDiv = document.createElement('div');
  labelDiv.style.cssText = 'position:absolute; bottom:0; left:0; right:0; background:rgba(0,0,0,.8); color:#0f0; padding:4px; font-size:10px; text-align:center; font-family:monospace;';
  labelDiv.textContent = `${index + 1}: ${timestamp.label}`;
  surface.appendChild(labelDiv);

  scene.add(g);
  cssScene.add(cssObj);

  return { group: g, css: cssObj, player, label: timestamp.label };
}
```

### Part 5: Initialize Pyramid

```javascript
// REPLACE: init() function modifications
function init() {
  // ... (keep scene, camera, renderer setup)
  
  // Generate positions
  const positions = generatePyramidPositions([1, 2, 3, 4, 4]);
  
  // Create all 14 TVs
  positions.forEach((pos, i) => {
    const tv = createStaticTV(pos, TIMESTAMPS[i], i);
    tvs.push(tv);
  });
  
  // Position camera to view entire pyramid
  camera.position.set(0, 2.5, 6);
  camera.lookAt(0, 1.8, 0);
  
  // Optional: Orbit controls for viewer exploration
  // controls = new OrbitControls(camera, renderer.domElement);
  
  animate();
}
```

### Part 6: Simplified Animate Loop

```javascript
// REPLACE: animate() function
function animate() {
  requestAnimationFrame(animate);
  
  // No physics stepping
  // No collision detection
  // No stability checks
  
  // Optional: Subtle camera drift in exhibit mode
  if (exhibit) {
    const t = Date.now() * 0.0001;
    camera.position.x = Math.sin(t) * 1.2;
    camera.position.z = 6 + Math.cos(t * 0.7) * 0.8;
    camera.lookAt(0, 1.8, 0);
  }
  
  renderer.render(scene, camera);
  cssRenderer.render(cssScene, camera);
}
```

---

## Interaction Design Options

### Option A: Static Exhibition (Recommended)
- No user input
- Optional slow camera orbit
- All videos play simultaneously
- Pure sensory experience

### Option B: Camera Control
- Arrow keys or mouse drag to orbit
- Zoom in/out
- Click TV to solo audio (mute others)

### Option C: Timeline Scrubbing
- Global timeline UI
- Scrub through video
- All TVs sync to same global time + offset

### Option D: Conductor Mode
- Play/pause all
- Individual TV mute toggles
- Volume mixer
- "Performance" interface

---

## Visual Enhancements

### Lighting for Drama

```javascript
// Dramatic lighting setup
const ambientLow = new THREE.AmbientLight(0x1a1a2e, 0.3);
scene.add(ambientLow);

// Spotlight from top
const spotlight = new THREE.SpotLight(0xffffff, 1.2);
spotlight.position.set(0, 6, 2);
spotlight.angle = Math.PI / 4;
spotlight.penumbra = 0.3;
spotlight.castShadow = true;
scene.add(spotlight);

// Colored rim lights
const rimLeft = new THREE.PointLight(0x00ff88, 0.6, 8);
rimLeft.position.set(-3, 2, 1);
scene.add(rimLeft);

const rimRight = new THREE.PointLight(0xff0088, 0.6, 8);
rimRight.position.set(3, 2, 1);
scene.add(rimRight);
```

### TV Glow Effect

```javascript
// Add glow to active TVs
tvs.forEach(tv => {
  const glowGeo = new THREE.PlaneGeometry(TV.w * 0.9, TV.h * 0.75);
  const glowMat = new THREE.MeshBasicMaterial({
    color: 0x00ff88,
    transparent: true,
    opacity: 0.1,
    side: THREE.BackSide
  });
  const glow = new THREE.Mesh(glowGeo, glowMat);
  glow.position.z = TV.d/2 + 0.05;
  tv.group.add(glow);
  
  // Pulse animation
  tv.glowMat = glowMat;
});

// In animate loop:
tvs.forEach((tv, i) => {
  if (tv.glowMat) {
    const phase = Date.now() * 0.001 + i * 0.5;
    tv.glowMat.opacity = 0.05 + Math.sin(phase) * 0.05;
  }
});
```

---

## Audio Mixing Strategy

### Challenge: 14 Simultaneous Audio Streams

**Option 1: Spatial Audio**
```javascript
// Use Web Audio API for 3D positioning
const audioCtx = new AudioContext();
tvs.forEach(tv => {
  const panner = audioCtx.createPanner();
  panner.panningModel = 'HRTF';
  panner.positionX.value = tv.group.position.x;
  panner.positionY.value = tv.group.position.y;
  panner.positionZ.value = tv.group.position.z;
  // Connect YouTube audio through panner
});
```

**Option 2: Volume Distance Attenuation**
```javascript
// Closer TVs are louder
function updateVolumes() {
  const listener = camera.position;
  tvs.forEach(tv => {
    const dist = tv.group.position.distanceTo(listener);
    const volume = Math.max(0, 1 - (dist / 8));
    if (tv.player && tv.player.setVolume) {
      tv.player.setVolume(volume * 100);
    }
  });
}
```

**Option 3: Solo Mode**
```javascript
// Click to solo one TV, mute others
function soloTV(index) {
  tvs.forEach((tv, i) => {
    const vol = (i === index) ? 100 : 10;
    if (tv.player) tv.player.setVolume(vol);
  });
}
```

---

## File Structure for New Scene

```
pyramid-scene.html          ← Main file
├── [HEAD]
│   ├── Three.js 0.128.0
│   ├── CSS3DRenderer
│   └── YouTube IFrame API
├── [STYLE]
│   ├── Dark theme
│   ├── Minimal UI
│   └── .yt-surface styling
└── [SCRIPT]
    ├── Config (VIDEO_ID, TIMESTAMPS)
    ├── generatePyramidPositions()
    ├── createStaticTV()
    ├── init() - create all 14
    ├── animate() - simple render loop
    └── Optional: controls, audio mixing
```

---

## Latent Prompt (For AI/Future Development)

```
SYSTEM: You are building an art installation using the VIDEO_STACKER_∞ codebase.

CONTEXT: 
- Base file: video_stacker_∞_you_tube_css_3_d_edition.html
- Goal: Static pyramid of 14 TVs, each playing different timestamp of same video
- Video: MT3snSsqcHs ("Out of Life" - 24:01 duration)
- Formation: 1-2-3-4-4 pyramid (5 rows, 14 TVs total)

REQUIREMENTS:
1. Remove all physics (Cannon.js)
2. Remove drop/gameplay mechanics
3. Create pyramid position generator (row config: [1,2,3,4,4])
4. Embed YouTube iframes with start time parameter
5. Display all 14 simultaneously
6. Optional: Spatial audio, camera controls, solo mode

MODIFICATIONS:
- generatePyramidPositions(rows) → [{x,y,z,index}]
- createStaticTV(pos, timestamp, index) → static positioned TV
- Remove: world.step(), collision, stability, drop(), nudge()
- Keep: Three.js scene, CSS3DRenderer, YouTube API

TIMESTAMPS (seconds):
[0, 131, 262, 393, 524, 655, 786, 917, 1048, 1179, 1310, 1441, 360, 720]

INTERACTION OPTIONS:
A. Static (recommended) - no input, optional slow orbit
B. Camera control - orbit/zoom
C. Timeline scrub - sync all TVs
D. Conductor - play/pause, mute toggles

OUTPUT: Single HTML file, self-contained, exhibition-ready
```

---

## Synthesis: The Philosophical Shift

### From Game → To Installation

**VIDEO_STACKER_∞ (gameplay)**:
- Physics-based precarity
- User drops TVs
- Failure is the arc
- **Time**: Real-time, player-driven

**PYRAMID SCENE (installation)**:
- Spatial fragmentation
- Pre-composed structure
- Success is the starting state
- **Time**: Video time, multi-linear

### The New Ontology

**Gameplay version**: Attention as weight that collapses  
**Pyramid version**: Time as space that fragments

Same technology, **opposite philosophy**.

---

## Estimated Development Time

| Task | Time | Difficulty |
|------|------|------------|
| Remove physics | 30 min | Easy |
| Pyramid generator | 45 min | Medium |
| Static TV creation | 60 min | Medium |
| Timestamp URLs | 15 min | Easy |
| Camera positioning | 20 min | Easy |
| Testing/debugging | 60 min | Medium |
| Audio mixing (optional) | 90 min | Hard |
| Visual polish | 45 min | Medium |
| **TOTAL** | **4-6 hours** | **Medium** |

---

## Success Criteria

✅ All 14 TVs visible in pyramid formation  
✅ Each TV playing correct timestamp  
✅ Stable rendering (60fps)  
✅ YouTube controls accessible  
✅ Camera view captures full pyramid  
✅ Audio manageable (not overwhelming)  
✅ Exhibition-ready (can run unattended)  

---

## Next Steps

1. **Read this blueprint thoroughly**
2. **Choose interaction model** (A, B, C, or D)
3. **Decide on audio strategy**
4. **Copy `video_stacker_∞_you_tube_css_3_d_edition.html`** as starting point
5. **Follow Part 1-6 modifications**
6. **Test incrementally** (positions → embeds → audio)
7. **Polish lighting and UI**
8. **Deploy**

---

**This is not a game anymore. This is a temporal sculpture.**

— Blueprint complete · Ready for implementation
