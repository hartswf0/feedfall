# VIDEO_STACKER_∞

**Stack TVs. Watch videos. Don't let it collapse.**

An experimental web application exploring physics-based video stacking as embodied media interaction.

---

## Quick Start

### Desktop
1. Open `video_stacker_∞_index.html` (production build with local videos)
2. Click **DROP** to spawn a TV
3. Click **LEFT/RIGHT** to nudge while falling
4. Stack higher, but watch the **stability meter**
5. When stability < 0 → **COLLAPSE**

### Mobile
1. Open `video_stacker_∞_mobile_swipe_right_edge_controls_haptics_audio_index.html`
2. **Swipe UP** to drop
3. **Swipe LEFT/RIGHT** to nudge
4. **Swipe DOWN** to cull bottom TV

### Advanced (YouTube + Controls)
1. Open `vs-stacker.html`
2. Click **▣** button (bottom-right) to open Remote panel
3. Control individual TVs, manage playlists, adjust settings

---

## Files Overview

| File | Purpose | Best For |
|------|---------|----------|
| `video_stacker_∞_index.html` | Production build | **Recommended start** |
| `vs-stacker.html` | Advanced controls | Power users, DJ/VJ |
| `video_stacker_∞_mobile_swipe...` | Touch-optimized | Mobile devices |
| `video_stacker_∞_you_tube_css_3_d_edition.html` | YouTube-focused | Platform integration |
| `video-02.html` | Local video prototype | Development |
| `video_full.html` | Simplified demo | Teaching/embedding |

**See `MANIFEST.md` for complete file matrix.**

---

## Requirements

### Local Video Versions
Place MP4 files in `/videos/` directory:
- `/videos/a.mp4`
- `/videos/b.mp4`
- `/videos/c.mp4`

Or videos will fall back to procedural noise shader.

### YouTube Versions
No setup required—uses default playlist.  
Edit playlist via on-screen controls or in JavaScript.

---

## Controls

### Universal
- **DROP**: Spawn new TV
- **NUDGE LEFT/RIGHT**: Apply lateral impulse to falling TV
- **CULL**: Remove bottom TV
- **VIEW**: Cycle camera presets
- **MUTE**: Toggle audio

### Advanced (vs-stacker.html only)
- **Remote Panel**: Per-TV controls, playlist editor, theme switcher
- **Focus System**: Tap a TV to select it for individual control
- **TOP-N Slider**: Adjust how many videos play simultaneously (1-12)

---

## Physics

- **Stability** calculated from center-of-mass vs support footprint
- **Collapse** triggered when stability < 0
- Stack height increases difficulty (taller = more precarious)
- Clean landings (low velocity) = bonus points + streak multiplier

---

## Documentation

- **`ANALYSIS.md`**: Deep technical and philosophical analysis of all versions
- **`MANIFEST.md`**: Project structure, dependencies, feature comparison
- **`README.md`**: This file (user guide)

---

## Technical Stack

- **Three.js** (r128 or 0.160-0.161): 3D rendering
- **Cannon.js / cannon-es**: Physics simulation
- **CSS3DRenderer**: YouTube iframe integration
- **Web Audio API**: Procedural sound synthesis
- **Vibration API**: Haptic feedback (mobile)

---

## Browser Support

**Minimum:**
- Chrome 61+, Firefox 60+, Safari 10.1+
- WebGL 1.0, Web Audio API, ES6

**Optimal:**
- Modern browser with ES Modules support
- Mobile with touch + vibration support

---

## Development

### Run Locally
```bash
# Simple HTTP server (Python 3)
python -m http.server 8000

# Or use any local server
# Then open http://localhost:8000
```

### Modify Physics
Edit constants in JavaScript:
```javascript
const TV = { w: 0.60, h: 0.40, d: 0.45 };
const PHYS_LIMIT = 0.22;  // stability threshold
const STAB_ALPHA = 0.7;   // overhang penalty
```

### Add Videos
**YouTube versions:**
```javascript
const playlist = ["dQw4w9WgXcQ", "VIDEO_ID_2", ...];
```

**Local versions:**
```javascript
const FEED = ['/videos/my-video.mp4', ...];
```

---

## Troubleshooting

**Videos don't play:**
- YouTube: Check video IDs are valid and embeddable
- Local: Ensure `/videos/` directory exists with MP4 files
- Browser: Click to enable audio (autoplay policy)

**Performance issues:**
- Reduce `TOP_N_LIVE` (number of simultaneous video players)
- Lower screen resolution
- Disable shadows (edit `renderer.shadowMap.enabled = false`)

**Touch not working:**
- Ensure `touch-action: none` in CSS
- Check mobile browser supports Pointer/Touch Events

---

## License

[To be specified]

---

## Credits

Built with:
- [Three.js](https://threejs.org/) by Mr.doob and contributors
- [Cannon.js](https://schteppe.github.io/cannon.js/) / [cannon-es](https://pmndrs.github.io/cannon-es/) by Stefan Hedman & contributors
- YouTube IFrame API by Google

---

**Explore. Stack. Collapse. Repeat.**
