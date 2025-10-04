# 📚 VIDEO LIBRARY - WHERE YOU GO WHEN YOU LEAVE

## ✅ **ALL VIDEOS ADDED!**

Successfully added **39 videos** to the media library, including **26 timestamped poem segments**!

---

## 📼 **WHAT'S IN THE LIBRARY**

### **1. Codex Version 1 (13 poems)**
**Video:** `uDUoMnp1z_g`

Each poem is a separate TV with precise timestamps:

1. **Out of Life** (0:00-2:15) - `intro`, `poem`
2. **Flashing Lights** (2:16-4:31) - `poem`
3. **How to Break Off an Engagement** (4:32-6:47) - `poem`
4. **Nevermore** (6:48-9:03) - `poem`
5. **Bloodline** (9:04-11:19) - `poem`
6. **Resurrecting Atlantis** (11:20-13:35) - `poem`
7. **DJ Turn Me Up** (13:36-15:51) - `poem`
8. **Newly Single** (15:52-18:07) - `poem`
9. **Yet, Heard** (18:08-20:23) - `poem`
10. **Magic Ride** (20:24-22:39) - `poem`
11. **Reunion** (22:40-24:55) - `poem`
12. **How to Win My Heart** (24:56-27:11) - `poem`
13. **Hot Minute** (27:12-29:32) - `poem`, `outro`

### **2. Codex Version 2 (13 poems)**
**Video:** `G2NXjz5pGVw`

Same poems, different version (all tagged `v2`):

1. **Out of Life (v2)** (0:00-2:11)
2. **Flashing Lights (v2)** (2:11-4:22)
3. **How to Break Off an Engagement (v2)** (4:22-6:33)
4. **Nevermore (v2)** (6:33-8:44)
5. **Bloodline (v2)** (8:44-10:55)
6. **Resurrecting Atlantis (v2)** (10:55-13:06)
7. **DJ Turn Me Up (v2)** (13:06-15:17)
8. **Newly Single (v2)** (15:17-17:28)
9. **Yet Heard (v2)** (17:28-19:39)
10. **Magic Ride (v2)** (19:39-21:50)
11. **Reunion (v2)** (21:50-24:01)
12. **How to Win My Heart (v2)** (24:01-26:12)
13. **Hot Minute (v2)** (26:12-28:23)

### **3. Standalone Videos (13)**

- **Where You Go When You Leave (Main)** - `main`, `music`, `visual`
- **Pro Segments** - `segments`
- **Part 2** - `part2`, `poem`
- **Visual-Poetry Journey (26min)** - `journey`, `full`
- **DVR Recording** - `dvr`
- **Living H20** - `h2o`
- **Out of Life (Lead Clip)** - `clip`, `lead`
- **WGWYL 02** - `series`
- **WGWYL 01** - `series`
- **WYGWYL 00** - `series`

---

## 🏷️ **TAG SYSTEM**

Videos are organized by tags for easy filtering:

### **Content Tags:**
- `poem` - Individual poem segments (26)
- `main` - Main production video
- `clip` - Shorter clips
- `full` - Full-length features

### **Version Tags:**
- `v2` - Second version of poems (13)
- `intro` - Opening segments
- `outro` - Closing segments

### **Series Tags:**
- `series` - Part of WGWYL series
- `part2` - Sequel content
- `journey` - Full journey video

### **Style Tags:**
- `music` - Music video style
- `visual` - Visual emphasis
- `dvr` - DVR recording aesthetic
- `h2o` - Living H20 content
- `segments` - Professional segments

---

## 🎬 **HOW IT WORKS**

### **Timestamped Videos:**
```javascript
{ 
  name: 'Out of Life', 
  url: 'https://www.youtube.com/watch?v=uDUoMnp1z_g',
  start: 0,      // Start at 0 seconds
  end: 135,      // End at 2:15
  tags: ['poem', 'intro']
}
```

**Creates embed URL:**
```
https://www.youtube.com/embed/uDUoMnp1z_g?start=0&end=135
```

**Each poem is its own TV!**

### **Full Videos:**
```javascript
{ 
  name: 'Visual-Poetry Journey (26min)',
  url: 'https://youtu.be/MT3snSsqcHs',
  tags: ['journey', 'full']
}
```

---

## 📱 **USAGE IN FEED MODE**

### **Browse Poems Vertically:**
```
1. Press M (spawn 20 TVs)
2. Press P (feed mode)
3. Swipe up/down
4. Each TV shows:
   ┌─────────────────┐
   │                 │
   │  [POEM PLAYS]   │
   │                 │
   ├─────────────────┤
   │ Out of Life     │ ← Diegetic info
   │ 🏷️ poem, intro  │
   │ 📺 1 / 39       │
   └─────────────────┘
```

### **Filter by Tag:**
```javascript
// Show only poems
const poems = tvs.filter(tv => 
  tv.tags && tv.tags.includes('poem')
);

// Show only v2 versions
const v2 = tvs.filter(tv => 
  tv.tags && tv.tags.includes('v2')
);

// Show series
const series = tvs.filter(tv => 
  tv.tags && tv.tags.includes('series')
);
```

---

## 🎯 **SPATIAL ORGANIZATION IDEAS**

### **1. Timeline Layout:**
```
Intro poems → Middle poems → Outro poems
(vertical stack)
```

### **2. Version Comparison:**
```
Out of Life (v1)  ←→  Out of Life (v2)
Flashing Lights   ←→  Flashing Lights (v2)
...side by side...
```

### **3. Series Layout:**
```
WYGWYL 00
    ↓
WGWYL 01
    ↓
WGWYL 02
```

### **4. Topic Clusters:**
```
    [Love poems]
         ↓
[Breakup poems] ← [Main video] → [Journey video]
         ↓
  [Outro poems]
```

---

## 🚀 **TRY IT NOW**

```bash
open /Users/gaia/feedfall/feedfall/vs-plu.html

# In console, you'll see:
📚 Loaded 39 videos (26 timestamped segments)

# Add all poems to scene:
Press B (5 TVs)
Press N (10 TVs)
Press M (20 TVs)

# Open media library:
Press 📁 button
See all 39 videos!
Click any to add as TV

# Feed mode through poems:
Press P (feed mode)
Swipe through all poems
Each auto-plays its segment!
```

---

## 📊 **STATISTICS**

```
Total Videos:        39
Timestamped:         26 (67%)
Standalone:          13 (33%)
Unique Poems:        13
Poem Versions:       2
Series Videos:       3
Full Features:       2
```

---

## 🎨 **CREATIVE USES**

### **1. Poem Portfolio:**
- Add all 13 v1 poems as TVs
- Arrange in grid
- Feed mode to browse
- Professional showcase

### **2. Compare & Contrast:**
- Add v1 and v2 of same poem
- Place side by side
- Watch differences
- Cinematic mode

### **3. Series Binge:**
- Add all WGWYL videos
- Stack vertically
- Feed mode
- Scroll through series

### **4. Full Experience:**
- Start with "Out of Life (Lead Clip)"
- Add all v1 poems in order
- End with "Visual-Poetry Journey"
- Complete narrative arc

### **5. Spatial Story:**
- Center: Main video
- Orbit: Individual poems
- Outer ring: Series videos
- 3D constellation!

---

## 🎬 **EDL WORKFLOW**

**Edit Decision List with spatial arrangement:**

```
Timeline (vertical stack):
┌──────────────────────┐
│ Out of Life          │ ← Intro
├──────────────────────┤
│ Flashing Lights      │
├──────────────────────┤
│ How to Break Off...  │
├──────────────────────┤
│ Nevermore            │
├──────────────────────┤
│ ...                  │
├──────────────────────┤
│ Hot Minute           │ ← Outro
└──────────────────────┘

Feed mode = scrub through EDL!
```

---

## 📝 **TECHNICAL NOTES**

### **YouTube Embed API:**
- `?start=X` - Start at X seconds
- `&end=Y` - End at Y seconds
- Auto-stops at end time
- Perfect for segments!

### **Tag System:**
```javascript
tv.tags = ['poem', 'intro'];
// Allows filtering, grouping, color-coding
```

### **Diegetic Info:**
Shows tags as colored pills in feed mode!

---

## 🎉 **SUMMARY**

**vs-plu.html is now a POETRY VIDEO GALLERY!**

✅ **39 videos loaded**
✅ **26 timestamped poem segments**
✅ **2 complete versions** (compare!)
✅ **Tag-based organization**
✅ **Feed mode ready**
✅ **Spatial arrangement**
✅ **EDL workflow**

**Every poem is its own TV! Build your poetic universe in 3D space!** 📺✨🎬

---

**NEXT: Arrange them spatially, build sequences, create your visual poetry experience!** 🚀
