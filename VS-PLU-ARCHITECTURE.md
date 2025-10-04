# VIDEO_STACKER_PLUS (vs-plu.html) - Architecture Documentation

## Vision: 3D Media Zettelkasten / EDL Hybrid System

A spatial media organization system combining:
- **Minecraft**: Block-based 3D building/assembly
- **Tetris**: Precise stacking and arrangement
- **EDL** (Edit Decision List): Timeline/sequence management  
- **Zettelkasten**: Knowledge graph for media with tags and links

---

## Core Concepts

### 1. TV as Media Node
Each TV is a rich data structure:
```javascript
{
  id: "TV-001",               // Unique identifier
  group: THREE.Group,         // 3D mesh
  body: CANNON.Body,          // Physics body
  cssObj: CSS3DObject,        // Video/content surface
  
  // Metadata (Zettelkasten)
  tags: ["poem", "intro", "melancholy"],
  links: ["TV-005", "TV-012"], // Connected TVs
  metadata: {
    title: "Opening Scene",
    notes: "Use for intro sequence",
    created: Date,
    modified: Date
  },
  
  // Content (EDL)
  layers: [
    { type: 'youtube', videoId: 'xxx', start: 0, opacity: 1.0 },
    { type: 'text', content: 'Overlay text', opacity: 0.7 },
    { type: 'image', url: '...', opacity: 0.5 }
  ],
  
  // Assembly
  position: {x, y, z},
  rotation: {x, y, z},
  snapToGrid: true,
  locked: false,
  groupId: "scene-01"
}
```

### 2. Environmental Presets

**CALM (Water Effect)**
- Animated water plane with shader
- Blue-teal fog
- Soft ambient lighting
- Reflections on water surface
- Gentle wave motion

**ENERGETIC**
- Warm red/orange tones
- Faster camera motion
- No water

**VOID**
- Pure black background
- Minimal fog
- Spotlight focus

**GALLERY**
- Neutral gray
- Even lighting
- Grid floor visible

### 3. Layout Algorithms

**STACK** - Traditional vertical stacking
```javascript
position = { x: 0, y: index * (TV.h + gap), z: 0 }
```

**GRID** - Organized rows/columns
```javascript
const cols = Math.ceil(Math.sqrt(count));
position = {
  x: (index % cols) * spacing,
  y: 0.5,
  z: Math.floor(index / cols) * spacing
}
```

**SPIRAL** - Rising spiral pattern
```javascript
const angle = index * 0.6;
const radius = 0.5 + index * 0.12;
position = {
  x: Math.cos(angle) * radius,
  y: index * 0.3,
  z: Math.sin(angle) * radius
}
```

**CIRCLE** - Concentric circles
```javascript
const ring = Math.floor(index / 12);
const angleInRing = (index % 12) * (Math.PI * 2 / 12);
const radius = 3 + ring * 1.5;
position = {
  x: Math.cos(angleInRing) * radius,
  y: ring * 0.5,
  z: Math.sin(angleInRing) * radius
}
```

**WAVE** - Undulating pattern
```javascript
position = {
  x: (index % 10) * 1.2 - 6,
  y: Math.sin(index * 0.5) * 2 + index * 0.15,
  z: Math.floor(index / 10) * 1.2
}
```

**TETRIS** - Stackable blocks with gaps
```javascript
// Random gaps creating Tetris-like formations
// TVs can "fall" to fill gaps
```

**MINECRAFT** - Chunked grid with elevation
```javascript
// 16x16 chunks
// Variable heights creating terrain-like structure
```

### 4. Assembly Tools

**SELECT** (👆)
- Click to select TV
- Shows bounding box + ID tag
- Multi-select with Shift

**MOVE** (🚚)
- Drag selected TV in 3D space
- Gizmo with X/Y/Z arrows
- Smooth physics integration

**SNAP** (🧲)
- Grid snapping (0.1, 0.5, 1.0 units)
- Align to other TVs
- Auto-arrange tools

**CLONE** (📋)
- Duplicate TV with all metadata
- New unique ID assigned
- Preserves tags and layers

**GROUP** (📦)
- Select multiple TVs as group
- Move/rotate as single unit
- Named groups for scenes

**TAG** (🏷️)
- Add/edit tags on TV
- Visual tag display
- Filter by tags

### 5. Holographic Layers System

Each TV can have multiple content layers:

```javascript
// Layer types
{
  type: 'youtube',
  videoId: 'xxx',
  start: 0,
  opacity: 1.0,
  blend: 'normal',
  zIndex: 0
}

{
  type: 'text',
  content: 'Poem verse 1...',
  fontSize: 16,
  color: '#ffffff',
  opacity: 0.8,
  zIndex: 1
}

{
  type: 'image',
  url: 'overlay.png',
  opacity: 0.6,
  zIndex: 2
}

{
  type: 'shader',
  fragmentShader: '...',
  uniforms: {...},
  zIndex: 3
}
```

**Layer Controls:**
- Reorder layers (drag & drop)
- Toggle visibility
- Adjust opacity
- Blend modes (normal, multiply, screen)

### 6. Tagging & Zettelkasten System

**Tag Structure:**
```javascript
{
  name: "melancholy",
  color: "#4a90e2",
  tvs: ["TV-001", "TV-045", "TV-067"],
  notes: "Scenes with melancholic tone"
}
```

**Visual Tag Display:**
- Floating label above TV
- Color-coded by tag type
- Size based on tag count
- Toggle visibility

**Tag Filtering:**
- Show only TVs with specific tags
- AND/OR logic for multiple tags
- Save tag combinations as views

**Linking System:**
```javascript
{
  from: "TV-001",
  to: "TV-005",
  type: "sequence", // or "reference", "contrast"
  notes: "Transition to next scene"
}
```

Visual links rendered as lines between TVs.

### 7. Scene Management (EDL)

**Scene Structure:**
```javascript
{
  id: "scene-001",
  name: "Opening Sequence",
  tvs: ["TV-001", "TV-002", "TV-003"],
  duration: 45, // seconds
  transitions: [
    { from: "TV-001", to: "TV-002", type: "fade", duration: 2 },
    { from: "TV-002", to: "TV-003", type: "cut", duration: 0 }
  ],
  layout: "STACK",
  environment: "CALM",
  cameraPath: [
    { time: 0, pos: [0,3,6], look: [0,1,0] },
    { time: 15, pos: [2,4,7], look: [0,2,0] }
  ]
}
```

**Export Options:**
- JSON scene file
- EDL format for editing software
- Timeline visualization
- Preview playback mode

### 8. Water Shader Implementation

```glsl
// Vertex shader - wave motion
varying vec2 vUv;
uniform float time;

void main() {
  vUv = uv;
  vec3 pos = position;
  pos.z += sin(pos.x * 2.0 + time) * 0.1;
  pos.z += cos(pos.y * 2.0 + time * 0.7) * 0.1;
  gl_Position = projectionMatrix * modelViewMatrix * vec4(pos, 1.0);
}

// Fragment shader - water color/reflection
uniform float time;
varying vec2 vUv;

void main() {
  vec2 uv = vUv;
  vec3 waterColor = vec3(0.04, 0.2, 0.3);
  
  // Caustics effect
  float caustic = sin(uv.x * 10.0 + time) * cos(uv.y * 10.0 + time * 0.7);
  caustic = caustic * 0.5 + 0.5;
  
  waterColor += caustic * 0.1;
  gl_FragColor = vec4(waterColor, 0.8);
}
```

---

## UI/UX Design (Mobile-First)

### Bottom Toolbar (Thumb-Accessible)
```
[Layout] [+Add] [×13] [×100] [Reset]
```

### Side Rail (Right)
```
[Media]
[Camera]
[Environment]
[Tools]
```

### Top HUD
```
TVs: 45/100 | Layout: Grid | View: Orbit | Tags: ✓
```

### Gesture Controls
- **Single tap**: Select TV
- **Double tap**: Edit TV details
- **Pinch**: Zoom camera
- **Two-finger drag**: Rotate camera
- **Long press**: Context menu

### Context Menu (Long Press on TV)
```
🏷️  Edit Tags
📝  Edit Layers
📋  Clone
🔗  Link To...
🗑️  Delete
📦  Add to Group
```

---

## Performance Optimizations for 100 TVs

### Level of Detail (LOD)
```javascript
// Distant TVs use simplified geometry
if (distance > 10) {
  tv.group.children[0].visible = false; // Hide shell detail
  tv.cssObj.visible = false; // Hide video
  tv.showProxy = true; // Show simple cube
}
```

### Occlusion Culling
```javascript
// Don't render TVs behind camera or other TVs
raycaster.intersect(tv, camera);
if (tv.occluded) tv.visible = false;
```

### Lazy Video Loading
```javascript
// Only load videos for visible TVs
if (tv.visible && !tv.videoLoaded) {
  loadVideoForTV(tv);
}
```

### Physics Optimization
```javascript
// Sleep distant/settled TVs
if (distance > 15 && tv.settled) {
  tv.body.sleep();
}
```

---

## Keyboard Shortcuts

```
V - Cycle camera modes
E - Cycle environments
L - Cycle layouts
T - Toggle tags
I - Toggle IDs
G - Grab/move selected
D - Duplicate selected
X - Delete selected
S - Save scene
Shift+S - Save scene as...
Ctrl+Z - Undo
Space - Play/pause timeline
1-7 - Switch tools
```

---

## Data Persistence

### LocalStorage Schema
```javascript
{
  version: "1.0.0",
  tvs: [...],
  scenes: [...],
  tags: [...],
  mediaLibrary: [...],
  settings: {
    environment: "CALM",
    layout: "GRID",
    gridSnap: 0.5,
    showTags: true,
    showIDs: true
  }
}
```

### Export Formats

**JSON** - Full scene data
**EDL** - Edit decision list
**CSV** - Spreadsheet of TVs with metadata
**HTML** - Standalone viewer

---

## Next Implementation Steps

1. ✅ Add constants and state (DONE)
2. Add water shader to CALM environment
3. Implement layout algorithms (all 7)
4. Create holographic layer system
5. Build tagging UI
6. Add assembly tools with gizmos
7. Implement scene save/load
8. Add keyboard shortcuts
9. Create timeline/EDL export
10. Mobile gesture controls

---

This architecture creates a unique spatial media management system that's part 3D editor, part knowledge management, part video editor - perfect for assembling and organizing complex video projects with rich metadata and spatial relationships.
