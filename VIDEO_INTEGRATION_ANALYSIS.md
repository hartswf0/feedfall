# FeedFall Video Integration Analysis

## 📊 Summary

**Total HTML Files:** 30  
**Files with New Video (uDUoMnp1z_g):** 5  
**Files Needing Update:** ~15-20 legacy files  

---

## ✅ Files WITH New YouTube Video Integration

These files already have the **"uDUoMnp1z_g"** 13-segment video:

1. **feed-to-water.html** ✓ - Full integration with water effects
2. **jj.html** ✓ - Full integration with 13 segments
3. **multi-mode.html** ✓ - Full integration with geometry modes
4. **prod.html** ✓ - Production version
5. **vss.html** ✓ - Full integration

---

## 🔧 Files NEEDING Video Update

### High Priority (Legacy files with CSS3D but old videos)

1. **crt-stack.html** - Uses VIDEO_ID '6AiCk06MgmQ' (different video)
2. **eno-crt.html** - Likely has old video setup
3. **hom.html** - Has CSS3D but needs new segments
4. **hut.html** - Has CSS3D but needs new segments  
5. **inicio.html** - Has most CSS3D code, needs update
6. **ivst.html** - Has CSS3D support
7. **vs-stty.html** - Has CSS3D, needs specific segments
8. **vs-stacker.html** - Has CSS3D support
9. **wreck.html** - Has CSS3D support

### Medium Priority (YouTube CSS3D editions - may have partial support)

10. **video_stacker_∞_you_tube_css_3_d_edition.html**
11. **video_stacker_∞_you_tube_css_3_d_edition (1).html**
12. **video_stacker_∞_you_tube_css_3_d_edition (2).html**
13. **video_stacker_∞_you_tube_css_3_d_edition (3).html**
14. **video_stacker_∞_you_tube_css_3_d_edition (4).html**

### Lower Priority (May need full rebuild)

15. **video-01.html** - Older version
16. **video-02.html** - Older version
17. **video-refactor.html** - Refactored version
18. **video-stacker-02.html** - Older stacker
19. **video_full.html** - Full version needs check
20. **video_stacker_∞_index.html** - May need segments

### Utility Files (May not need videos)

21. **index.html** - Launcher/menu (probably doesn't need videos)
22. **index-launcher.html** - Launcher (probably doesn't need videos)
23. **pyramid-scene.html** - Pyramid demo (check if it needs videos)

### Mobile-specific

24. **video_stacker_∞_mobile_swipe_right_edge_controls_haptics_audio_index.html**
25. **video_stacker_∞_mobile_swipe_right_edge_controls_haptics_audio_index (1).html**

---

## 📺 Standard Video Configuration

The new standard video setup uses:

### Video ID
```javascript
youtubeId: 'uDUoMnp1z_g'
```

### 13 Segments
```javascript
segments: [
    { name: 'Out of Life', start: 0, time: '0:00–2:15' },
    { name: 'Flashing Lights', start: 136, time: '2:16–4:31' },
    { name: 'How to Break Off an Engagement', start: 272, time: '4:32–6:47' },
    { name: 'Nevermore', start: 408, time: '6:48–9:03' },
    { name: 'Bloodline', start: 544, time: '9:04–11:19' },
    { name: 'Resurrecting Atlantis', start: 680, time: '11:20–13:35' },
    { name: 'DJ Turn Me Up', start: 816, time: '13:36–15:51' },
    { name: 'Newly Single', start: 952, time: '15:52–18:07' },
    { name: 'Yet, Heard', start: 1088, time: '18:08–20:23' },
    { name: 'Magic Ride', start: 1224, time: '20:24–22:39' },
    { name: 'Reunion', start: 1360, time: '22:40–24:55' },
    { name: 'How to Win My Heart', start: 1496, time: '24:56–27:11' },
    { name: 'Hot Minute', start: 1632, time: '27:12–29:32' }
]
```

---

## 🔄 Update Strategy

### For files with existing CSS3D infrastructure:

1. Find and replace old VIDEO_ID/youtubeId
2. Replace TIMESTAMPS array with new segments
3. Update any createTV/spawn functions to use segments
4. Ensure iframe src uses: `?start=${segment.start}&autoplay=1&mute=1&controls=1&playsinline=1`

### For files needing major refactor:

1. Import CSS3DRenderer if not present
2. Add segments config at top
3. Update TV creation to loop through segments
4. Add CSS3D scene and renderer
5. Sync CSS3D pivots with 3D meshes in animate loop

---

## 🎯 Recommended Action Plan

### Phase 1: Quick Wins (1-2 files to test)
- Update **crt-stack.html** (replace '6AiCk06MgmQ' with new video)
- Update **inicio.html** (has good CSS3D infrastructure)

### Phase 2: Core Legacy Files (5-10 files)
- **hom.html**, **hut.html**, **wreck.html**
- **vs-stty.html**, **vs-stacker.html**
- **eno-crt.html**, **ivst.html**

### Phase 3: YouTube CSS3D Editions (5 files)
- All **video_stacker_∞_you_tube_css_3_d_edition** variants

### Phase 4: Older Versions (as needed)
- **video-01.html**, **video-02.html**, etc.

---

## 💡 Notes

- Some files may have **architectural differences** that make direct video swap difficult
- Files like **crt-stack.html** use filing cabinet metaphor - may want custom segment mapping
- **Mobile versions** may need performance considerations (fewer simultaneous videos)
- **Launcher files** probably don't need videos (they're navigation)
- Consider creating a **shared config file** for the 13 segments to avoid repetition

---

## 🚀 Next Steps

1. **Quick audit** - Open 2-3 legacy files to confirm structure
2. **Test update** - Update one file (e.g., `crt-stack.html`) completely
3. **Create template** - Document the exact find/replace pattern
4. **Batch update** - Apply to remaining high-priority files
5. **Test all** - Verify each updated file loads and plays videos correctly
