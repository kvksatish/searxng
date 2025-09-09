# DOCS/ - Documentation Directory

## 📁 Directory Overview
This directory contains SearXNG's comprehensive documentation built with Sphinx. It provides detailed documentation for users, administrators, and developers, covering everything from basic usage to advanced development topics. The documentation is organized by audience and includes interactive examples, configuration guides, and API references.

## 📂 Directory Structure
```
docs/
├── index.rst                 # Main documentation index
├── conf.py                   # Sphinx configuration
├── _themes/                  # Custom documentation theme
│   └── searxng/             # SearXNG-specific theme
│       ├── theme.conf       # Theme configuration
│       └── static/          # Theme assets (CSS, JS, images)
├── build-templates/          # Build-time template generation
├── admin/                    # Administrator documentation
│   ├── index.rst            # Admin guide index
│   ├── installation-scripts.rst  # Installation guides
│   ├── answer-captcha/      # CAPTCHA configuration
│   └── settings/            # Configuration documentation
├── user/                     # End-user documentation
├── dev/                      # Developer documentation
│   ├── answerers/           # Direct answer system docs
│   ├── engines/             # Search engine development
│   ├── plugins/             # Plugin development
│   ├── result_types/        # Result type documentation
│   └── searxng_extra/       # Extra utilities documentation
├── src/                      # Source code documentation
└── utils/                    # Documentation utilities
```

## 📖 Documentation Sections

### 👤 User Documentation (`user/`)
**Target Audience:** End users of SearXNG instances
**Content Coverage:**
- **Getting Started** - How to use SearXNG for searching
- **Search Features** - Advanced search techniques and operators
- **Privacy Guide** - Understanding privacy features and protections
- **Preferences** - Customizing search experience and settings
- **Special Queries** - Plugin-powered special query types
- **Mobile Usage** - Mobile-specific features and interface

**Key Topics:**
- Search syntax and operators
- Category-specific searching (images, videos, news, etc.)
- Language and region preferences
- Safe search configuration
- Keyboard shortcuts and hotkeys
- Result filtering and sorting

### 🛠️ Administrator Documentation (`admin/`)
**Target Audience:** System administrators and instance operators

#### Installation & Setup
**`installation-scripts.rst`** - Automated installation guides
- **Distribution Support** - Ubuntu, Debian, Arch Linux, Fedora
- **Docker Deployment** - Container-based installation
- **Manual Installation** - Step-by-step manual setup
- **Reverse Proxy** - Apache and nginx configuration
- **SSL/TLS Setup** - HTTPS configuration and security

#### Configuration Management (`settings/`)
**Comprehensive configuration documentation for all settings:**

**`settings.rst`** - Main settings overview and structure
**`settings_general.rst`** - General instance configuration
- Instance name and branding
- Debug mode and logging levels
- Metrics collection and monitoring
- Default language and localization

**`settings_server.rst`** - Server configuration
- Bind address and port settings
- Base URL configuration
- Public instance settings
- Rate limiting and security

**`settings_search.rst`** - Search behavior configuration
- Default search settings
- Safe search configuration
- Autocomplete providers
- Search result limits and timeouts

**`settings_engines.rst`** - Search engine configuration
- Engine enable/disable settings
- Engine-specific parameters
- Custom engine development
- Engine performance tuning

**`settings_ui.rst`** - User interface configuration
- Theme selection and customization
- UI element visibility
- Search categories as tabs
- Result display options

**`settings_outgoing.rst`** - Outgoing request configuration
- HTTP client settings
- Proxy configuration
- Timeout and retry settings
- User agent and headers

**`settings_redis.rst`** - Redis cache configuration
- Redis connection settings
- Cache key prefixes
- Performance optimization
- Memory usage management

**`settings_valkey.rst`** - Valkey cache configuration
- Valkey server settings
- Connection pooling
- Data persistence options

**`settings_plugins.rst`** - Plugin configuration
- Plugin enable/disable settings
- Plugin-specific configuration
- Custom plugin development
- Plugin performance impact

**`settings_brand.rst`** - Branding customization
- Instance branding and logos
- Custom CSS and styling
- Footer links and information
- Documentation URLs

**`settings_categories_as_tabs.rst`** - Category tab configuration
- Tab layout and organization
- Category grouping
- Custom category creation

#### Security & Monitoring (`answer-captcha/`)
**CAPTCHA Integration** - Bot protection configuration
- CAPTCHA provider setup
- Challenge configuration
- Performance impact analysis
- User experience considerations

### 💻 Developer Documentation (`dev/`)
**Target Audience:** Developers contributing to or extending SearXNG

#### Search Engine Development (`engines/`)
**Complete guide to developing custom search engines:**

**`demo/`** - Example engine implementations
- Simple HTML scraping engines
- JSON API integration examples
- Authentication handling examples
- Error handling patterns

**`offline/`** - Offline search engine development
- Local database integration
- File system search engines
- Custom data source engines

**`online/`** - Online search engine development
- HTTP client usage patterns
- Response parsing techniques
- Pagination handling
- Rate limiting compliance

**`online_url_search/`** - URL-specific search engines
- Reverse lookup engines
- URL analysis engines
- Link validation engines

**Engine Development Topics:**
- **Engine Interface** - Required functions and variables
- **Request Generation** - Building search requests
- **Response Processing** - Parsing search results
- **Error Handling** - Robust error management
- **Testing** - Engine testing best practices
- **Performance** - Optimization techniques

#### Plugin Development (`plugins/`)
**Plugin System Documentation:**
- **Plugin Architecture** - Core plugin system design
- **Plugin Lifecycle** - Initialization, execution, cleanup
- **Hook System** - Pre-search, post-search, result hooks
- **Configuration** - Plugin settings and preferences
- **Testing** - Plugin testing frameworks
- **Examples** - Real plugin implementations

**Plugin Types:**
- **Result Processors** - Modify search results
- **Query Enhancers** - Enhance or modify queries
- **Answer Providers** - Direct answer generation
- **UI Extensions** - User interface enhancements

#### Direct Answer System (`answerers/`)
**Answerer Development:**
- **Answerer Interface** - Core answerer API
- **Data Sources** - Integrating external data
- **Response Formatting** - Rich answer presentation
- **Caching Strategies** - Performance optimization
- **Error Handling** - Graceful failure management

#### Result Types (`result_types/`)
**Custom Result Type Development:**
- **Result Type Interface** - Core result type API
- **Template Development** - Custom result templates
- **Metadata Handling** - Rich result metadata
- **Media Integration** - Images, videos, files
- **Structured Data** - Schema.org and rich snippets

#### Extra Utilities (`searxng_extra/`)
**Additional Development Tools:**
- **Update Scripts** - Data update automation
- **Development Utilities** - Development helpers
- **Testing Tools** - Advanced testing utilities
- **Deployment Scripts** - Production deployment tools

## 🎨 Documentation Theme (`_themes/searxng/`)

### Custom Theme Features
**SearXNG-Specific Styling:**
- **Brand Colors** - Consistent color scheme with main application
- **Typography** - Readable fonts and sizing
- **Navigation** - Intuitive documentation navigation
- **Code Highlighting** - Syntax highlighting for multiple languages
- **Responsive Design** - Mobile-friendly documentation

**Theme Configuration (`theme.conf`):**
- Parent theme settings
- Custom styling options
- Navigation configuration
- Footer customization

**Static Assets (`static/`):**
- **searxng.css** - Custom CSS styling
- **JavaScript** - Interactive documentation features
- **Images** - Documentation images and icons

## ⚙️ Documentation Build System

### Sphinx Configuration (`conf.py`)
**Build Settings:**
- **Extensions** - Sphinx extensions for enhanced functionality
- **Theme Configuration** - Custom theme settings
- **Build Options** - Output formats and optimization
- **Integration** - API documentation generation

**Key Extensions:**
- **AutoDoc** - Automatic API documentation from docstrings
- **Napoleon** - Google/NumPy style docstring support
- **ViewCode** - Source code links in documentation
- **Intersphinx** - Cross-project documentation linking

### Build Templates (`build-templates/`)
**Dynamic Documentation Generation:**
- **Engine Documentation** - Auto-generate engine documentation
- **Plugin Documentation** - Auto-generate plugin documentation
- **Configuration Reference** - Generate configuration documentation
- **API Reference** - Auto-generate API documentation

## 📊 Documentation Features

### Interactive Elements
- **Live Examples** - Working code examples
- **Configuration Builders** - Interactive configuration generators
- **Search Integration** - Documentation search functionality
- **Cross-References** - Extensive internal linking

### Multi-Format Output
- **HTML** - Web-based documentation (primary)
- **PDF** - Printable documentation
- **ePub** - E-reader compatible format
- **LaTeX** - Academic paper format

### Localization Support
- **Multi-Language** - Documentation in multiple languages
- **Translation Infrastructure** - Weblate integration
- **Locale-Specific Examples** - Region-appropriate examples

## 🔧 Documentation Maintenance

### Content Management
- **Version Control** - Git-based content management
- **Review Process** - Pull request-based updates
- **Automated Builds** - Continuous integration builds
- **Quality Assurance** - Link checking and validation

### Community Contributions
- **Contribution Guidelines** - How to contribute documentation
- **Style Guide** - Documentation writing standards
- **Review Process** - Documentation review workflow
- **Translation** - Community translation coordination

### Performance Optimization
- **Build Optimization** - Fast documentation builds
- **Caching** - Efficient build caching
- **CDN Integration** - Fast global documentation delivery
- **Search Optimization** - Fast documentation search

This documentation directory provides comprehensive, well-organized information for all SearXNG stakeholders, from end users to developers, with modern tooling and community-friendly contribution processes.