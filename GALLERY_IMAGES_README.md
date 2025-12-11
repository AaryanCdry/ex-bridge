# Gallery Images Setup

## Current Status
The gallery section has been converted to an **infinite carousel slideshow** with the following features:

✅ **Infinite Auto-Play** - Images cycle every 5 seconds  
✅ **Navigation Controls** - Previous/Next chevron buttons  
✅ **Dot Navigation** - Click dots to jump to any image  
✅ **Progress Bar** - Visual indicator of slideshow progress  
✅ **Touch Support** - Swipe left/right on mobile  
✅ **Hover Pause** - Slideshow pauses on hover  
✅ **Smooth Transitions** - 700ms slide transitions  

## Current Gallery Images (5 images)
The gallery currently displays these images:
1. `asset/gallery/IMG-20241119-WA0012.jpeg` - Interactive Training
2. `asset/gallery/IMG-20241119-WA0028.jpg` - Group Learning
3. `asset/gallery/IMG-20250218-WA0010.jpg` - Advanced Lab
4. `asset/gallery/IMG-20250520-WA0035.jpg` - Active Learning
5. `asset/gallery/IMG-20250521-WA0012.jpg` - Hands-On Workshop

## How to Add More Images

To add the additional 11 images, follow these steps:

### Option 1: Upload Images Manually
1. Save image files to `/workspaces/ex-bridge/asset/gallery/`
2. Update the HTML section (lines 1848-1910) by adding new gallery-slide divs

### Option 2: Using Terminal
```bash
cd /workspaces/ex-bridge/asset/gallery/
# Copy your images here
```

### HTML Structure for Adding Images
The carousel is automatically created from `.gallery-slide` divs. To add more images, add them to the `#galleryTrack` section:

```html
<div class="gallery-slide min-w-full relative group">
    <img src="asset/gallery/YOUR-IMAGE-NAME.jpg" alt="Your description" class="w-full h-full object-cover">
    <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end">
        <div class="p-6 w-full">
            <p class="text-white font-bold text-lg">Your Title</p>
            <p class="text-gray-200 text-sm">Your Description</p>
        </div>
    </div>
</div>
```

### Update Dot Navigation
After adding images, update the dot navigation section (around line 1895) to match the number of images:

```html
<div class="absolute bottom-6 left-1/2 -translate-x-1/2 z-20 flex gap-3">
    <!-- Add one button for each image -->
    <button class="gallery-dot w-3 h-3 rounded-full bg-white/40 hover:bg-white/60 transition-all duration-300 backdrop-blur-sm" data-index="5"></button>
    <!-- ... etc -->
</div>
```

## JavaScript Configuration

The carousel auto-plays every **5 seconds**. To change this:
- Find `setTimeout` in the gallery carousel code (line ~3027)
- Change `5000` to your desired milliseconds

## Features Breakdown

| Feature | Details |
|---------|---------|
| **Auto-Play Duration** | 5 seconds per slide |
| **Transition Duration** | 700ms (CSS duration-700) |
| **Pause on Hover** | Yes |
| **Swipe Support** | Yes, threshold 50px |
| **Loop Behavior** | Infinite (wraps around) |
| **Responsive** | Yes (works on all devices) |

## Troubleshooting

**Images not showing?**
- Check file paths are correct in `src` attributes
- Verify images exist in `/workspaces/ex-bridge/asset/gallery/`
- Check browser console for 404 errors

**Slideshow not working?**
- Ensure JavaScript is enabled
- Check that `#galleryTrack` and `.gallery-slide` elements exist
- Verify Lucide icons are loaded for chevron buttons

**Dots not matching images?**
- Count gallery-slide divs and dots must match
- Each dot needs `data-index="n"` matching its position (0-based)

## Ready to Use
The carousel is fully functional and ready for your images. Just add the image files and HTML elements as described above.
