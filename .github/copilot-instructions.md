# Lowkey Doom Website - AI Coding Agent Instructions

## Project Overview
This is a single-page HTML website for Lowkey Doom, featuring organic animated blob shapes with embedded content thumbnails. The site uses vanilla HTML/CSS/JS with no build system or external dependencies.

## Architecture & Key Patterns

### Blob-Based Design System
- **Core Component**: `.blob-thumb-wrap` containers with layered animated SVG clip-paths
- **Animation**: SVG `<clipPath>` elements with `<animate>` for organic morphing shapes  
- **Layering**: White background blob (`.gallery-blob-bg`) + colored foreground blob + thumbnail grid
- **Colors**: Gallery=#27a9e0 (blue), Merch=#f0271b (red), BTS=#ffd93a (yellow)

### CSS Architecture Conventions
- **Embedded Styles**: All CSS is in `<head>` - no external stylesheets
- **Z-index Strategy**: Background stripe=1, blobs=1-2, thumbnails=2, headers=1000, footer elements=0-4
- **Responsive**: Mobile-first with `@media (max-width: 768px)` breakpoint
- **Layout**: Flexbox-based with alternating blob alignment (`.align-left`/`.align-right`)

### Asset Organization
```
images/
  ├── logo.png, footer.png          # Main branding
  ├── red-stripe2.svg               # Background decoration  
  ├── cloud-1.png, cloud-2.png     # Animated footer elements
  ├── section-thumbs/               # Gallery preview images
  └── gallery/                      # Full-size modal images
```

### Animation Patterns
- **Blob morphing**: 12-15s duration SVG path animations with 3-4 keyframe states
- **Cloud movement**: CSS `translateX` from off-screen left to off-screen right
- **Performance**: `translateZ(0)`, `backface-visibility: hidden` for hardware acceleration

### Interactive Features
- **Thumbnail clicks**: Gallery images open Instagram, BTS images trigger modal overlays
- **Modal system**: Vanilla JS `openImageModal()` with backdrop dismissal
- **Email obfuscation**: Runtime DOM manipulation to prevent scraping

## Development Workflow

### File Structure
- **Single HTML file**: `index.html` contains all markup, CSS, and JS
- **Prototype file**: `blob.html` for testing blob animations in isolation
- **No build process**: Direct file editing, no compilation or bundling required

### Asset Management
- Images should maintain consistent naming: `section-thumbs/` for previews, `gallery/` for full-size
- SVG clips named by section: `#galleryClip`, `#merchClip`, `#btsClip`
- Logo variations numbered sequentially: `logo-footer.png`, `logo-footer2.png`, etc.

### Browser Compatibility
- Uses `-webkit-clip-path` fallbacks for Safari
- CSS Grid avoided in favor of Flexbox for broader support
- Hardware acceleration applied to animated elements

## Styling Conventions

### Color Palette
- Background: `#d1d1d1` (light gray)
- Text: `#111` (near black) 
- Accent colors match blob themes (blue/red/yellow)
- Footer text: `#fff` (white) with `#27a9e0` (blue) links

### Typography
- Font stack: `Arial, sans-serif` (system default)
- Headings: Large (4rem) with complex white text-shadow outlines
- Body text: 1.75rem with bold weight for readability

### Layout Principles
- Max-width constraints: 800px for content, 1100px for sections, 1300px for wrapper
- Negative margins for visual overlaps between sections
- Absolute positioning for layered footer elements

## Common Tasks

### Adding New Content Sections
1. Create new SVG `<clipPath>` with unique ID and animation
2. Add section with `.blob-thumb-wrap` structure
3. Include both background and foreground blob divs
4. Add thumbnail grid with appropriate border colors

### Modifying Animations  
- Blob shapes: Edit SVG path `d` attribute values in `<animate>` elements
- Timing: Adjust `dur` attribute (current range: 12-15s)
- Cloud speed: Modify animation duration in CSS `@keyframes`

### Image Updates
- Maintain aspect ratios: thumbnails are 190px width with auto height
- Border styling: 10px solid with section-specific colors
- Background: white behind thumbnails for consistency

This is a visual-first project focused on smooth animations and artistic presentation rather than complex functionality.