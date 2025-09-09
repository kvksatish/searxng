# SEARX/ - Core Application Directory Context

## 📁 Directory Overview
This is the heart of the SearXNG metasearch engine application. Contains all core modules, configuration, engines, templates, and business logic for the privacy-focused search platform.

## 📂 Directory Structure

### Core Subdirectories
```
searx/
├── answerers/          # Direct answer providers (Wikipedia, calculators, etc.)
├── botdetection/       # Bot detection and rate limiting mechanisms  
├── data/              # Static data files (engine descriptions, locales, etc.)
├── enginelib/         # Engine library utilities and traits
├── engines/           # 214 search engine implementations
├── favicons/          # Favicon management and resolution system
├── infopage/          # Informational pages in multiple languages
├── metrics/           # Performance metrics collection and reporting
├── network/           # Network utilities and HTTP client management
├── plugins/           # 11 plugin modules for extended functionality
├── result_types/      # Result type definitions and processors
├── search/            # Search logic, processors, and result handling
├── static/            # Static web assets (CSS, JS, images)
├── templates/         # HTML templates for web interface
└── translations/      # Internationalization files (60+ languages)
```

## 📄 Core Python Files

### Application Bootstrap & Configuration
- **`__init__.py`** (4,239 bytes) - Main module initialization, settings loading, logging configuration
- **`settings_defaults.py`** (10,392 bytes) - Default configuration schema, validation rules, environment variable mapping
- **`settings_loader.py`** (8,888 bytes) - Configuration file loading, YAML parsing, settings validation
- **`settings.yml`** (70,576 bytes) - Main configuration file with engine definitions, preferences, localization

### Web Application Core  
- **`webapp.py`** (51,676 bytes) - Main Flask application with 20+ routes, request handling, session management
- **`webadapter.py`** (11,420 bytes) - Web request/response adapters, parameter parsing, form handling
- **`webutils.py`** (12,040 bytes) - Web utility functions, HMAC generation, result templating, theme management
- **`flaskfix.py`** (2,668 bytes) - Flask framework patches and compatibility fixes

### Search Core Logic
- **`query.py`** (12,848 bytes) - Search query parsing, validation, external bang handling, language detection
- **`results.py`** (13,986 bytes) - Result container, aggregation, deduplication, ranking algorithms
- **`autocomplete.py`** (11,125 bytes) - Autocomplete functionality with multiple backend providers

### External Integrations
- **`external_bang.py`** (3,566 bytes) - DuckDuckGo-style !bang commands for direct site searches
- **`external_urls.py`** (2,640 bytes) - External URL generation and redirection handling

### Data Management & Caching
- **`cache.py`** (14,915 bytes) - Caching layer with multiple backends (memory, SQLite, Valkey/Redis)
- **`sqlitedb.py`** (16,127 bytes) - SQLite database operations for caching and storage
- **`valkeydb.py`** (1,868 bytes) - Valkey/Redis database interface
- **`valkeylib.py`** (7,731 bytes) - Valkey/Redis client library and connection management

### Security & Rate Limiting
- **`limiter.py`** (7,567 bytes) - Rate limiting implementation with IP-based controls
- **`limiter.toml`** (1,458 bytes) - Rate limiter configuration rules
- **`preferences.py`** (22,137 bytes) - User preferences management, validation, cookie handling

### Localization & Internationalization
- **`locales.py`** (15,954 bytes) - Locale handling, language detection, region mapping
- **`sxng_locales.py`** (8,073 bytes) - SearXNG-specific locale definitions and mappings
- **`babel_extract.py`** (1,828 bytes) - Babel message extraction for translations

### Specialized Features
- **`weather.py`** (21,296 bytes) - Weather information provider and formatting
- **`wikidata_units.py`** (9,060 bytes) - Unit conversion data from Wikidata
- **`answerers/`** - Direct answer providers (calculator, time zones, etc.)

### Monitoring & Metrics
- **`openmetrics.py`** (1,916 bytes) - OpenMetrics format export for monitoring systems
- **`version.py`** (6,709 bytes) - Version management, git information, build details

### Utilities & Helpers  
- **`utils.py`** (29,778 bytes) - Extensive utility functions (HTML parsing, text processing, URL handling)
- **`exceptions.py`** (4,212 bytes) - Custom exception classes for error handling
- **`extended_types.py`** (2,352 bytes) - Type definitions and extensions
- **`compat.py`** (1,332 bytes) - Compatibility shims for different Python versions
- **`unixthreadname.py`** (534 bytes) - Thread naming utilities for debugging

### Message Files
- **`searxng.msg`** (2,540 bytes) - Localization message catalog

## 🔧 Key Functionality

### Search Pipeline
1. **Query Processing** (`query.py`) - Parse and validate search queries
2. **Engine Execution** (`engines/`) - Parallel requests to 214+ search engines  
3. **Result Aggregation** (`results.py`) - Combine and deduplicate results
4. **Response Formatting** (`webapp.py`) - Return HTML, JSON, CSV, or RSS

### Security Features
- **Bot Detection** (`botdetection/`) - Automated bot identification and blocking
- **Rate Limiting** (`limiter.py`) - IP-based request throttling
- **Privacy Protection** - No user tracking, minimal data retention

### Customization
- **Plugin System** (`plugins/`) - Extensible functionality modules
- **Theme System** (`templates/`, `static/`) - Customizable web interface
- **Engine Configuration** - Flexible search engine management

### Performance Optimization
- **Caching Layer** (`cache.py`) - Multi-tier caching system
- **Connection Pooling** (`network/`) - HTTP connection management
- **Parallel Processing** - Concurrent engine requests

## 🌐 Internationalization
- **60+ Languages** supported via `translations/`
- **Automatic Language Detection** from browser headers
- **RTL Support** for Arabic, Hebrew, etc.
- **Regional Customization** for search preferences

## 📊 Monitoring & Analytics
- **Performance Metrics** via `/metrics` endpoint
- **Error Tracking** with detailed logging
- **Health Checks** via `/healthz` endpoint
- **Statistics Dashboard** at `/stats`

This core directory represents the complete metasearch engine implementation with enterprise-grade features for privacy, performance, and customization.