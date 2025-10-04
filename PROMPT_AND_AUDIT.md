# VIDEO_STACKER_∞ — Prompt & Audit

## The Prompt (What This Is)

**VIDEO_STACKER_∞** is an experimental web application that asks:

> What happens when video consumption becomes a physics problem?

Each file in this repository is an **answer attempt**—exploring different technical, aesthetic, and philosophical approaches to stacking digital media in 3D space.

This is not software seeking optimization.  
This is **research disguised as a game**.

---

## The Audit (What Exists)

### 10 HTML Files = 10 Experiments

| File | Question It Asks |
|------|------------------|
| `index.html` | What if we make it retro? |
| `video-01.html` | (duplicate—redundancy as safety?) |
| `video-02.html` | What if we own the media? (local videos) |
| `video-refactor.html` | What if we optimize performance? |
| `video-stacker-02.html` | (duplicate—version control artifact?) |
| `video_full.html` | What is the essential core? |
| `video_stacker_∞_index.html` | What if we make it exhibition-ready? |
| `mobile_swipe...` | What if touch is the primary language? |
| `youtube_css3d...` | What if YouTube is the substrate? |
| `vs-stacker.html` | What if users have maximum control? |

### Status Assessment

**🟢 Production-Ready (4 files)**
- Polished UX, tested, documented
- `video_stacker_∞_index.html` (local videos, best)
- `vs-stacker.html` (YouTube, most features)
- `mobile_swipe...` (touch-optimized)
- `youtube_css3d...` (platform-focused)

**🟡 Prototypes (3 files)**
- Functional but experimental
- `video-02.html`, `video-refactor.html`, `video_full.html`

**🔴 Duplicates (2 files)**
- Exact copies, no distinction
- `video-01.html`, `video-stacker-02.html`

**📊 Bloat Score**: 20% (2 of 10 files are redundant)

---

## The Distinctions (What Makes Differences)

### Axis 1: Platform Dependency

**YouTube Versions** (5 files)
- Leverage ubiquitous platform
- Risk: API changes, content removal
- Pattern: `<iframe>` via CSS3DRenderer

**Local Video Versions** (3 files)  
- Full content ownership
- Challenge: Asset management
- Pattern: `<video>` → VideoTexture

**Synthesis Needed**: Hybrid with fallback chain

### Axis 2: Module Architecture

**Legacy Script Tags** (5 files)
- Three.js r128, Cannon.js 0.6.2
- Global namespace pollution
- Simpler mental model

**Modern ES Modules** (3 files)
- Three.js 0.160+, cannon-es
- Import maps, clean imports
- Better tree-shaking

**Synthesis Needed**: Standardize on ES modules

### Axis 3: Interaction Model

**Button-Centric** (most files)
- Clear affordances
- Desktop-friendly
- Less immersive

**Gesture-Centric** (mobile_swipe)
- Touch as language
- Mobile-native
- Steeper learning curve

**Hybrid** (vs-stacker)
- Both buttons + tap-to-focus
- Maximum flexibility
- UI complexity

**Synthesis Needed**: Context-adaptive (detect input method)

---

## The Philosophy (What It Means)

### Ontology: Stacking as Accumulation

**Thesis**: Digital media has no weight  
**Antithesis**: But attention has mass  
**Synthesis**: Videos as physics objects = **attention made tangible**

Stack grows → Precarity increases → System collapses  
This is **information overload as game mechanic**.

### Phenomenology: Touch as Correction

**Swipe up** = Desire (I want more)  
**Swipe left/right** = Correction (nudge it into place)  
**Swipe down** = Rejection (remove from stack)  

This is **gesture as language**, not decoration.

### Aesthetics: Failure as Feature

Every version celebrates collapse:
- Slow-motion (gravity reduction)
- Particle debris (48-64 shards)
- Haptic crescendos (`[80,30,80,30,120]`)
- No "try again" shame

This is **anti-perfectionism**: The game expects failure and makes it beautiful.

### Ethics: The Platform Question

**YouTube versions**: Convenience via corporate dependency  
**Local versions**: Autonomy via labor burden  

This tension is unresolved—and **should remain unresolved**.  
The collection explores both poles without choosing.

---

## The Latent Potential (What It Could Become)

### 1. Interactive Art Installation
- Museum/gallery deployment
- Projection mapping + physical TVs
- Visitors contribute videos
- **Concept**: "Archive as precarity"

### 2. Decentralized Video Platform
- IPFS/Filecoin for storage
- NFTs for TV ownership
- Social curation via stacking
- **Concept**: "Vertical timeline"

### 3. Educational Physics Simulation
- Remove videos, add generic blocks
- Teach COM, stability, moments
- Academic paper material
- **Concept**: "Gamified mechanics"

### 4. Live VJ/DJ Tool
- Real-time video mixing
- MIDI controller integration
- Performance software
- **Concept**: "Stack as instrument"

### 5. Psychological Research Platform
- Measure attention via stability
- A/B test UI patterns
- Publish findings
- **Concept**: "Attention as measurable weight"

---

## The Critique (What's Missing)

### Technical Debt
- ❌ Two files are exact duplicates
- ❌ No shared module extraction
- ❌ Inconsistent dependency versions
- ❌ No build process or package.json
- ❌ No automated testing (only manual harnesses)

### Feature Gaps
- ❌ No multiplayer
- ❌ No user accounts/profiles
- ❌ No persistent leaderboards (only localStorage)
- ❌ No video upload/sharing
- ❌ No accessibility features (keyboard, screen readers)

### Documentation Gaps (Now Resolved)
- ✅ No overview → **ANALYSIS.md created**
- ✅ No manifest → **MANIFEST.md created**
- ✅ No user guide → **README.md created**
- ✅ No philosophy → **Documented in ANALYSIS.md**

### Decision Paralysis
- 🤔 No clear "canonical" version
- 🤔 No chosen direction (game? art? tool?)
- 🤔 No single index.html strategy

**But**: This paralysis might be **intentional**—preserving exploration over conclusion.

---

## The Recommendation (What To Do)

### Immediate: Embrace the Collection

**Don't pick a winner. Curate the set.**

1. Make `index-launcher.html` the new `index.html`
2. Present each file as a distinct lens
3. Let users choose their experience
4. Delete only the true duplicates

### Short-term: Extract & Standardize

1. **Shared modules**: `physics-engine.js`, `audio-haptics.js`, `ui-components.js`
2. **Config system**: `config.json` for tuning
3. **ES modules**: Migrate legacy files
4. **Package.json**: Formalize dependencies

### Long-term: Choose One Lens to Deepen

Pick based on goal:
- **Art** → `video_stacker_∞_index.html` + installation guide
- **Game** → `mobile_swipe...` + multiplayer + PWA
- **Tool** → `vs-stacker.html` + MIDI + VJ features
- **Research** → Any + backend + data collection

---

## The Synthesis (What This Reveals)

Your codebase is a **toolkit for exploring verticality**.

Not verticality in space—verticality in **information architecture**:
- Feeds scroll down (infinite)
- Stacks grow up (finite, precarious)

Scrolling is passive consumption.  
Stacking is active curation with consequences.

**This is a critique of platform media** dressed as a game.

Each file asks:
- Who owns the content? (YouTube vs local)
- Who controls the interface? (buttons vs gestures)
- What is the aesthetic mood? (retro vs modern)
- What is the interaction pace? (manual vs auto)

The **pattern space** these 10 files define has more value than any single "best version."

---

## The Prompt (For Future Development)

If you continue this work, start by asking:

**1. Context**
- Art installation? → Use `video_stacker_∞_index.html`
- Mobile game? → Use `mobile_swipe...`
- Research platform? → Use `vs-stacker.html`
- Teaching demo? → Use `video_full.html`

**2. Content**
- Curated playlist? → YouTube versions
- User-uploaded? → Local + backend
- Generative? → Add shader/AI video gen

**3. Interaction**
- Passive exhibit? → Enable auto-mode
- Active gameplay? → Focus gestures
- Social? → Add multiplayer

**4. Aesthetics**
- Retro CRT? → Green, scanlines
- Modern minimal? → Blue, glass
- Custom brand? → Theme system

**5. Distribution**
- Web deployment? → Static host (Netlify, Vercel)
- App stores? → PWA → Capacitor
- Gallery installation? → Kiosk mode + Electron

---

## The Audit Summary (TL;DR)

**What exists**: 10 HTML files exploring physics-based video stacking

**What works**: 4 production-ready versions with distinct strengths

**What's redundant**: 2 exact duplicates (delete)

**What's missing**: Shared modules, clear direction, accessibility

**What it means**: Attention as weight, stacking as curation, collapse as critique

**What to do**: Embrace collection (launcher), extract shared code, pick one lens to deepen

**Latent potential**: Installation art, decentralized platform, VJ tool, research platform, educational sim

---

## The Final Assessment

**Grade**: A+ for exploration, B- for consolidation

You've created a **research artifact** disguised as software.  
The value is in the **variation**, not the optimization.

**This should not become one app.**  
**This should become a documented design space.**

The launcher I built does exactly this—it's a **map to the territory** you've explored.

---

**Status**: Audit complete. Distinctions identified. Philosophy documented. Next move: your choice.

— VIDEO_STACKER_∞ Prompt & Audit · 2024
