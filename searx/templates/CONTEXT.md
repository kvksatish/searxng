# SEARX/TEMPLATES/ - User Interface Templates Directory

## 📁 Directory Overview
This directory contains all HTML templates that define SearXNG's web user interface. The templates use Jinja2 templating engine and provide a clean, responsive, privacy-focused search interface. Currently implements the "simple" theme with comprehensive template coverage.

## 📂 Directory Structure
```
searx/templates/
└── simple/                    # Simple theme (primary UI theme)
    ├── base.html              # Base template with common structure
    ├── index.html             # Homepage search interface
    ├── search.html            # Search results page layout  
    ├── results.html           # Search results listing
    ├── preferences.html       # User preferences management
    ├── stats.html             # Instance statistics page
    ├── info.html              # Information pages
    ├── 404.html               # Error page template
    ├── answer/                # Direct answer templates
    ├── elements/              # Reusable UI elements
    ├── filters/               # Search filter components
    ├── messages/              # User message templates
    ├── preferences/           # Preference panel templates
    └── result_templates/      # Result type-specific templates
```

## 🏗️ Core Template Architecture

### 🎯 Main Layout Templates

#### `base.html` - **Foundation Template**
**Purpose:** Base template providing common HTML structure and functionality
**Key Features:**
- **HTML5 Document Structure** - Semantic HTML layout
- **Meta Tags** - SEO and mobile optimization tags
- **CSS/JavaScript Loading** - Asset management and loading
- **Navigation Header** - Search box and navigation elements
- **Footer Content** - Links and instance information
- **Theme Support** - Light/dark theme switching
- **Responsive Design** - Mobile-friendly layout
- **Content Security Policy** - Security headers
- **Internationalization** - Multi-language support blocks

#### `page_with_header.html` - **Header-Enabled Pages**
**Purpose:** Template for pages requiring the search header
**Usage:** Preferences, statistics, info pages
**Features:** Search header with navigation + main content area

### 🔍 Search Interface Templates

#### `index.html` - **Homepage Template**
**Purpose:** Main search page where users start their search
**Key Elements:**
- **Search Input** - Main query input field with autocomplete
- **Category Tabs** - General, Images, Videos, News, etc.
- **Search Options** - Language, safe search filters
- **Engine Selection** - Optional engine-specific search
- **Keyboard Shortcuts** - Hotkey support integration
- **Focus Management** - Automatic input focus
- **Progressive Enhancement** - Works without JavaScript

#### `simple_search.html` - **Minimal Search Interface**  
**Purpose:** Lightweight search page for embedded use
**Features:** Simplified search input without full navigation

#### `search.html` - **Search Results Container**
**Purpose:** Main container for search results and related elements
**Components:**
- **Results Area** - Container for search result listings
- **Sidebar Elements** - Infoboxes, suggestions, corrections
- **Pagination** - Result page navigation
- **Search Refinements** - Filter and sorting options
- **Error Handling** - Display search errors and messages

#### `results.html` - **Results Listing Template**
**Purpose:** Renders the actual search results list
**Features:**
- **Result Items** - Individual search result rendering
- **Result Types** - Different templates for different content types
- **Metadata Display** - Result source, date, relevance
- **Thumbnail Support** - Image and video thumbnails
- **URL Processing** - Clean URL display and tracking removal
- **Keyboard Navigation** - Arrow key result navigation

### 📊 Specialized Page Templates

#### `preferences.html` - **Settings Management**
**Purpose:** Comprehensive user preferences interface
**Sections:**
- **General Settings** - Language, theme, search behavior
- **Privacy Settings** - Tracking, cookies, image proxy
- **UI Preferences** - Layout, colors, shortcuts
- **Engine Configuration** - Enable/disable search engines
- **Plugin Management** - Configure plugin behavior
- **Advanced Options** - Power user settings

#### `stats.html` - **Instance Statistics**
**Purpose:** Display performance and usage statistics
**Metrics:**
- **Engine Performance** - Response times and success rates
- **Error Statistics** - Failed requests and error types
- **Usage Analytics** - Search volume and patterns
- **System Health** - Server performance metrics
- **Configuration Info** - Active engines and settings

#### `info.html` - **Information Pages**
**Purpose:** Display informational content (about, help, etc.)
**Features:**
- **Markdown Support** - Rich content formatting
- **Multi-language** - Localized information pages
- **Navigation** - Page-to-page navigation
- **Responsive Layout** - Mobile-friendly information display

#### `new_issue.html` - **Bug Report Interface** 
**Purpose:** Help users report issues and problems
**Elements:**
- **Issue Templates** - Structured problem reporting
- **System Information** - Automatic environment details
- **GitHub Integration** - Link to issue tracker
- **User Guidance** - Help for effective bug reports

### 📋 Result Type Templates (`result_templates/`)

#### `default.html` - **Standard Web Results**
**Purpose:** Default template for general web search results
**Elements:**
- **Title Link** - Clickable result title
- **URL Display** - Clean, readable URL
- **Description** - Result snippet/description
- **Metadata** - Date, source, type information
- **Favicon** - Site icon display
- **Quick Actions** - Share, copy, archive links

#### `images.html` - **Image Search Results**
**Features:**
- **Thumbnail Display** - Image preview thumbnails
- **Image Metadata** - Size, format, source information
- **Lightbox Support** - Click-to-expand functionality
- **Grid Layout** - Responsive image grid
- **Image Proxy** - Privacy-protected image loading
- **Download Options** - Direct image access

#### `videos.html` - **Video Search Results**
**Components:**
- **Video Thumbnails** - Preview images with play buttons
- **Duration Display** - Video length information
- **Video Metadata** - Title, description, upload date
- **Platform Icons** - YouTube, Vimeo, etc. indicators
- **Embed Support** - Optional video embedding
- **Quality Information** - Resolution and format details

#### `files.html` - **File Download Results**
**Elements:**
- **File Type Icons** - PDF, DOC, XLS visual indicators
- **File Metadata** - Size, format, modification date
- **Download Links** - Direct file access
- **Preview Options** - File content preview when available
- **Security Indicators** - Safe download warnings

#### `map.html` - **Map and Location Results**
**Features:**
- **Map Integration** - Embedded map display
- **Location Information** - Address, coordinates, details
- **Directions Links** - Navigation integration
- **POI Details** - Points of interest information
- **Geolocation Support** - User location context

#### `paper.html` - **Academic Paper Results**
**Components:**
- **Paper Metadata** - Authors, journal, publication date
- **Abstract Display** - Paper summary
- **Citation Information** - Proper academic citations
- **DOI Links** - Digital Object Identifier linking
- **Open Access** - Free access indicators
- **Related Papers** - Similar research suggestions

#### `products.html` - **Shopping/Product Results**
**Elements:**
- **Product Images** - Item photographs
- **Price Information** - Current and historical pricing
- **Rating Display** - User ratings and reviews
- **Merchant Information** - Store and seller details
- **Availability** - Stock and shipping information
- **Comparison Tools** - Price comparison features

#### `torrent.html` - **Torrent Search Results**
**Features:**
- **Torrent Metadata** - Seeds, leechers, size
- **Magnet Links** - Direct torrent access
- **Content Information** - File lists and descriptions
- **Quality Indicators** - Video/audio quality ratings
- **Safety Warnings** - Legal and security notices

#### `code.html` - **Source Code Results**
**Components:**
- **Syntax Highlighting** - Formatted code display
- **Repository Information** - Git repository details
- **Language Detection** - Programming language identification
- **Code Snippets** - Relevant code excerpts
- **Repository Links** - GitHub, GitLab integration

#### `keyvalue.html` - **Structured Data Results**
**Purpose:** Display key-value pair information
**Usage:** Dictionary definitions, facts, specifications
**Layout:** Tabular data presentation with clear key-value relationships

### 🧩 Reusable Components (`elements/`)

#### `answers.html` - **Direct Answer Display**
**Purpose:** Show instant answers (calculator, weather, time)
**Features:**
- **Rich Formatting** - Styled answer presentation
- **Interactive Elements** - Clickable answer components
- **Source Attribution** - Answer source information
- **Multi-format Support** - Text, numbers, dates, etc.

#### `suggestions.html` - **Search Suggestions**
**Elements:**
- **Query Suggestions** - Alternative search terms
- **Auto-complete** - Real-time query completion
- **Recent Searches** - Search history integration
- **Trending Queries** - Popular search terms

#### `corrections.html` - **Spell Check and Corrections**
**Features:**
- **Spelling Corrections** - "Did you mean" functionality
- **Query Refinements** - Better search term suggestions
- **Automatic Correction** - Option to auto-correct queries

#### `infobox.html` - **Information Sidebar**
**Purpose:** Display structured information about search topics
**Content:**
- **Entity Information** - Person, place, organization details
- **Quick Facts** - Key information summary
- **Related Links** - Additional resources
- **Images** - Relevant photographs or logos

#### `engines_msg.html` - **Engine Status Messages**
**Purpose:** Display search engine status and error information
**Messages:**
- **Engine Failures** - When specific engines fail
- **Rate Limits** - When engines are throttled
- **Network Issues** - Connection problems
- **API Errors** - Service-specific errors

### 🎛️ Filter Components (`filters/`)

#### `languages.html` - **Language Filter**
**Features:**
- **Language Selection** - Choose search language
- **Auto-detection** - Automatic language detection
- **Regional Variants** - Country-specific languages
- **Popular Languages** - Prioritized common languages

#### `safesearch.html` - **Safe Search Filter**
**Options:**
- **Off** - No content filtering
- **Moderate** - Filter explicit content
- **Strict** - Maximum content filtering
- **Visual Indicators** - Clear filter status display

#### `time_range.html` - **Time Range Filter**
**Ranges:**
- **Any Time** - No time restrictions
- **Past Day/Week/Month/Year** - Time-based filtering
- **Custom Range** - User-defined date ranges
- **Recent Content** - Freshness-based filtering

### 💬 User Messages (`messages/`)

#### `no_results.html` - **No Results Found**
**Purpose:** Handle empty search results gracefully
**Elements:**
- **Helpful Suggestions** - How to improve search
- **Alternative Engines** - Try different search sources
- **Query Refinement** - Tips for better searches
- **Contact Information** - Report search issues

#### `no_cookies.html` - **Cookie Disabled Warning**
**Purpose:** Inform users about cookie requirements
**Information:**
- **Cookie Benefits** - Why cookies improve experience
- **Privacy Assurance** - Cookie usage explanation
- **Enable Instructions** - How to enable cookies

### 📱 Responsive Design Features

#### Mobile Optimization
- **Touch-Friendly** - Large tap targets for mobile
- **Responsive Grid** - Adaptive layout for different screens
- **Mobile Navigation** - Optimized mobile menu systems
- **Fast Loading** - Optimized for mobile networks
- **Offline Support** - Basic offline functionality

#### Accessibility
- **Keyboard Navigation** - Full keyboard accessibility
- **Screen Reader Support** - ARIA labels and descriptions
- **High Contrast** - Support for high contrast themes
- **Font Scaling** - Respect user font size preferences
- **Focus Management** - Clear focus indicators

#### Performance Optimization
- **Lazy Loading** - Load images and content on demand
- **Minified Assets** - Compressed CSS and JavaScript
- **Efficient Caching** - Browser caching optimization
- **Progressive Enhancement** - Core functionality without JavaScript

This templates directory provides a comprehensive, modern, and privacy-focused user interface that makes SearXNG accessible and usable across all devices while maintaining excellent performance and user experience standards.