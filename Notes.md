# Website Development Notes

## SVG Favicon Issues & Solutions

### Problem
- Custom SVG favicon appeared very small in browser tabs
- Logo looked much smaller compared to other websites' favicons
- Initial assumption was that the file size or dimensions were wrong

### Root Cause Analysis
The issue wasn't the actual size of the SVG file, but rather:

1. **ViewBox Problem**: The SVG had a massive viewBox (`"-102.4 -102.4 716.80 716.80"`) creating a 716x716 canvas with lots of empty space around the actual figure
2. **Complex Design**: Used a detailed human silhouette figure with thin lines and complex curves that don't scale well to tiny favicon sizes (16x16, 32x32 pixels)
3. **Visual Impact**: Unlike bold, simple favicon designs (letters, geometric shapes), detailed figures lose clarity at small sizes

### How to Access SVG Code (Not Just Image)
**Problem**: SVG files often open as images by default in file explorers
**Solution**: Open SVG files as text/code to edit them:

- **In VS Code**: Right-click file → "Open With" → Text Editor
- **Alternative**: Drag SVG file directly into VS Code
- **File Explorer**: Right-click → "Open with" → Notepad/VS Code

### SVG ViewBox Explanation
The viewBox is located in the opening `<svg>` tag:
```xml
<svg viewBox="x y width height">
```

- **x, y**: Starting coordinates (top-left corner)
- **width, height**: Size of the viewable area
- **Larger viewBox**: Creates more "canvas" space = logo appears smaller
- **Smaller viewBox**: Crops to focus on content = logo appears bigger

### Solution Applied
- **Removed background**: Eliminated the black circular background to simplify
- **Reduced stroke width**: Made the design cleaner
- **Understanding gained**: Favicons work best with bold, simple designs rather than complex detailed figures

### Key Lessons
1. **Favicon Design Philosophy**: Simple, bold shapes work better than detailed illustrations
2. **ViewBox Impact**: Controls how much "zoom" your SVG has - smaller viewBox = more zoomed in
3. **Professional Favicons**: Most use letters, geometric shapes, or high-contrast simple designs
4. **File Access**: SVG files need to be opened as text/code to edit the underlying XML structure

### Future Favicon Considerations
- Use bold, thick elements instead of thin lines
- Ensure high contrast for visibility
- Consider how the design will look at 16x16 pixels
- Simple geometric shapes or letters often work better than complex illustrations
- Test favicon in actual browser tabs, not just the file preview

---

*Notes from debugging session on October 3, 2025*
