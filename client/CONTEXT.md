# CLIENT/ - Frontend Assets and Build System Directory

## 📁 Directory Overview
This directory contains the modern frontend build system for SearXNG's user interface. It uses Vite + TypeScript + LESS for a performant, maintainable frontend development experience with modern tooling and optimization.

## 📂 Directory Structure
```
client/
└── simple/                        # Simple theme frontend assets
    ├── package.json               # Dependencies and build scripts
    ├── vite.config.ts             # Vite build configuration
    ├── tsconfig.json              # TypeScript configuration
    ├── biome.json                 # Code formatting configuration
    ├── .stylelintrc.json          # CSS/LESS linting rules
    ├── README.rst                 # Development instructions
    ├── generated/                 # Generated/compiled assets
    │   └── pygments.less          # Syntax highlighting styles
    ├── src/                       # Source code directory
    │   ├── js/                    # TypeScript/JavaScript modules
    │   │   ├── core/              # Core functionality modules
    │   │   ├── main/              # Main application features
    │   │   └── pkg/               # Package integrations
    │   ├── less/                  # LESS stylesheet source files
    │   ├── svg/                   # SVG icon assets
    │   └── brand/                 # Branding assets (logos, icons)
    └── tools/                     # Build tools and utilities
        ├── plg.ts                 # Custom Vite plugins
        ├── img.ts                 # Image processing utilities
        ├── jinja_svg_catalog.ts   # SVG catalog generation
        └── jinja_svg_catalog.html.edge # Template for SVG catalog
```

## 🛠️ Build System Configuration

### 📦 Package Configuration (`package.json`)
**Package Name:** `@searxng/theme-simple`
**Build System:** Vite + TypeScript + LESS

**Key Dependencies:**
- **ionicons** (8.0.0) - Modern icon library
- **normalize.css** (8.0.1) - CSS normalization
- **ol** (10.6.0) - OpenLayers mapping library
- **swiped-events** (1.2.0) - Touch gesture handling

**Development Tools:**
- **@biomejs/biome** - Code formatting and linting
- **vite** (rolldown-vite) - Build tool and dev server
- **typescript** - Type checking and compilation
- **less** - CSS preprocessor
- **lightningcss** - Fast CSS processing
- **stylelint** - CSS/LESS code quality
- **sharp** - Image processing
- **svgo** - SVG optimization

**Build Scripts:**
```json
{
  "build": "npm run build:icons && npm run build:vite",
  "build:icons": "node theme_icons.ts",
  "build:vite": "vite build",
  "fix": "npm run fix:stylelint && npm run fix:biome && npm run fix:package",
  "lint": "npm run lint:biome && npm run lint:tsc"
}
```

**Browser Support:**
- Chrome >= 93
- Firefox >= 92  
- Safari >= 15.4
- Modern browsers only (no IE support)

### ⚙️ Vite Configuration (`vite.config.ts`)
**Build Configuration:**
- **Output Directory:** `searx/static/themes/simple/`
- **Public Path:** `/static/themes/simple/`
- **Asset Organization:** Separate CSS, JS, and image directories
- **Source Maps:** Enabled for debugging
- **Bundle Analysis:** Optional bundle size analysis

**Entry Points:**
- **CSS Files:**
  - `searxng-ltr.css` - Left-to-right language styles
  - `searxng-rtl.css` - Right-to-left language styles  
  - `rss.css` - RSS feed styling
  - `ol.css` - OpenLayers map styles

- **JavaScript Modules:**
  - `searxng.core` - Core application functionality
  - `ol` - OpenLayers mapping integration

**Asset Processing:**
- **SVG Optimization** - SVGO processing for smaller file sizes
- **PNG Generation** - Convert SVG to PNG for favicon/icons
- **Image Optimization** - Sharp image processing
- **CSS Processing** - Lightning CSS for performance

**File Naming Convention:**
- JavaScript: `js/[name].min.js`
- CSS: `css/[name].min[extname]`
- Images: `img/[name][extname]`

### 🎨 TypeScript Configuration (`tsconfig.json`)
**Compiler Options:**
- **Target:** Modern ES2020+
- **Module System:** ESNext with bundler resolution
- **Strict Mode:** Enabled for type safety
- **Source Maps:** Enabled for debugging
- **Path Mapping:** Configured for clean imports

## 💻 Source Code Structure (`src/`)

### 📜 JavaScript/TypeScript Modules (`src/js/`)

#### Core Modules (`core/`)
- **`index.ts`** - Main application entry point
- **`listener.ts`** - Event handling system
- **`nojs.ts`** - No-JavaScript fallback functionality
- **`router.ts`** - Client-side routing
- **`toolkit.ts`** - Utility functions and helpers

#### Main Application Features (`main/`)
- **`autocomplete.ts`** - Search autocomplete functionality
- **`infinite_scroll.ts`** - Infinite scrolling for results
- **`keyboard.ts`** - Keyboard shortcuts and navigation
- **`mapresult.ts`** - Map result rendering and interaction
- **`preferences.ts`** - User preferences management
- **`results.ts`** - Search results display and interaction
- **`search.ts`** - Search functionality and form handling

#### Package Integrations (`pkg/`)
- **`ol.ts`** - OpenLayers mapping library integration

### 🎨 Stylesheets (`src/less/`)
**LESS Preprocessing:** Modern CSS with variables, mixins, and nesting

**Core Stylesheets:**
- **`style.less`** - Base styles and variables
- **`style-ltr.less`** - Left-to-right language styles
- **`style-rtl.less`** - Right-to-left language styles
- **`index.less`** - Homepage specific styles
- **`search.less`** - Search results page styles
- **`preferences.less`** - Settings page styles
- **`stats.less`** - Statistics page styles

**Component Stylesheets:**
- **`autocomplete.less`** - Autocomplete dropdown styling
- **`animations.less`** - CSS animations and transitions
- **`code.less`** - Code syntax highlighting styles
- **`embedded.less`** - Embedded widget styles
- **`info.less`** - Information page styles
- **`new_issue.less`** - Issue reporting form styles
- **`result_templates.less`** - Result type specific styles
- **`toolkit.less`** - UI toolkit components
- **`weather.less`** - Weather widget styles

**Utility Stylesheets:**
- **`definitions.less`** - LESS variables and constants
- **`mixins.less`** - Reusable LESS mixins
- **`toolkit_loader.less`** - Loading animations
- **`rss.less`** - RSS feed styling

### 🖼️ Visual Assets

#### SVG Icons (`src/svg/`)
- **`empty_favicon.svg`** - Default favicon placeholder
- **`select-dark.svg`** - Dark theme select arrow
- **`select-light.svg`** - Light theme select arrow
- **`ionicons/`** - Ionicons library icons
  - `information-circle-outline.svg`
  - `newspaper-outline.svg`

#### Brand Assets (`src/brand/`)
- **`searxng.svg`** - Main SearXNG logo
- **`searxng-wordmark.svg`** - SearXNG wordmark logo
- **`img_load_error.svg`** - Image loading error placeholder

## 🔧 Build Tools (`tools/`)

### Custom Vite Plugins (`plg.ts`)
**`plg_svg2svg`** - SVG optimization plugin
- SVGO processing for smaller file sizes
- Customizable optimization settings
- Batch processing support

**`plg_svg2png`** - SVG to PNG conversion plugin
- Generate PNG versions of SVG assets
- Multiple size generation
- Sharp image processing integration

### Image Processing (`img.ts`)
- Image optimization utilities
- Format conversion functions
- Responsive image generation

### SVG Catalog System (`jinja_svg_catalog.*`)
- Generate SVG sprite catalogs
- Template-based SVG organization
- Integration with Jinja2 templates

## 🚀 Development Workflow

### Development Server
```bash
# Start development server
npm exec -- vite

# Or using manage script
./manage vite.simple.dev
```

### Build Process
```bash
# Production build
npm run build

# Individual build steps
npm run build:icons    # Generate icon assets
npm run build:vite     # Vite compilation
```

### Code Quality
```bash
# Fix all code issues
npm run fix

# Individual fixes
npm run fix:biome      # Code formatting
npm run fix:stylelint  # CSS/LESS formatting
npm run fix:package    # Package.json sorting
```

### Linting & Type Checking
```bash
# Run all linting
npm run lint

# Individual checks
npm run lint:biome     # Code linting
npm run lint:tsc       # TypeScript checking
```

## 🎯 Key Features

### Modern Development Experience
- **Hot Module Replacement** - Live reloading during development
- **TypeScript Support** - Full type checking and IntelliSense
- **Source Maps** - Debugging support in development and production
- **Fast Builds** - Vite's optimized build system
- **Code Splitting** - Automatic bundle optimization

### Performance Optimization
- **Tree Shaking** - Remove unused code
- **Minification** - Compressed CSS and JavaScript
- **Asset Optimization** - Optimized images and SVGs
- **Bundle Analysis** - Optional bundle size analysis
- **Cache Optimization** - Efficient browser caching

### Code Quality
- **Biome Integration** - Modern code formatting and linting
- **StyleLint** - CSS/LESS code quality enforcement
- **TypeScript Strict Mode** - Type safety guarantees
- **Consistent Formatting** - Automated code formatting

### Asset Management
- **SVG Optimization** - Automated SVG compression
- **Icon Generation** - PNG favicon generation from SVG
- **Responsive Images** - Multiple image format support
- **Asset Fingerprinting** - Cache-busting file names

This client directory represents a modern, maintainable frontend development setup that produces optimized assets for SearXNG's user interface while providing an excellent developer experience with fast builds, hot reloading, and comprehensive code quality tools.