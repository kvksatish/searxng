# SearXNG - Comprehensive Project Documentation

## 🎯 Project Overview

SearXNG is a privacy-respecting, hackable metasearch engine that aggregates results from over 200 search engines without storing any personal information about users. It's a fork of the original searx project with enhanced features, better performance, and active development.

### Key Features
- **Privacy-First**: No user tracking, no profiling, no data storage
- **Metasearch**: Aggregates results from 200+ search engines
- **Customizable**: Fully hackable and configurable
- **Self-Hostable**: Can be deployed on your own infrastructure
- **Open Source**: AGPL-3.0 licensed

## 📁 Project Structure

```
searxng/
├── searx/                      # Core application directory
│   ├── engines/                # 214 search engine implementations
│   ├── plugins/                # 11 plugin modules for extended functionality
│   ├── templates/              # HTML templates for UI
│   ├── static/                 # Static assets (CSS, JS, images)
│   ├── translations/           # Internationalization files
│   ├── search/                 # Search logic and processors
│   ├── favicons/              # Favicon management system
│   ├── botdetection/          # Bot detection mechanisms
│   ├── network/               # Network handling utilities
│   ├── answerers/             # Direct answer providers
│   ├── infopage/              # Information pages
│   ├── result_types/          # Result type definitions
│   ├── metrics/               # Performance metrics collection
│   ├── data/                  # Static data files
│   ├── webapp.py              # Main Flask application
│   ├── settings.yml           # Main configuration file
│   └── version.py             # Version management
├── searxng_extra/             # Additional utilities
│   └── update/                # Update scripts for various data sources
├── container/                 # Docker containerization
│   ├── dist.dockerfile        # Production Docker image
│   ├── builder.dockerfile    # Build stage Docker image
│   └── entrypoint.sh         # Container entry point script
├── docs/                      # Documentation
├── tests/                     # Test suite
├── utils/                     # Utility scripts
├── client/                    # Client-side assets
├── requirements.txt           # Python dependencies
├── setup.py                   # Python package setup
├── Makefile                   # Build automation
└── manage                     # Management script
```

## 🏗️ Architecture Overview

### Core Components

#### 1. **Web Application Layer** (`searx/webapp.py`)
- Flask-based web application
- Handles HTTP requests and responses
- Route management for search, preferences, and static content
- Session and cookie management
- Rate limiting and bot detection integration

#### 2. **Search Engine System** (`searx/engines/`)
- **214 search engines** integrated, including:
  - General search: Google, Bing, DuckDuckGo, Qwant, Startpage
  - Specialized: Wikipedia, WolframAlpha, GitHub, StackOverflow
  - Media: YouTube, Flickr, Unsplash, SoundCloud
  - Academic: PubMed, Semantic Scholar, arXiv
  - Maps: OpenStreetMap, Apple Maps
  - Shopping: eBay, Amazon
  - Torrents: 1337x, The Pirate Bay
- Each engine is a Python module with standardized interface
- Support for various protocols: HTTP/HTTPS, JSON APIs, XML feeds

#### 3. **Search Processing Pipeline** (`searx/search/`)
- Query parsing and validation
- Parallel engine requests
- Result aggregation and deduplication
- Ranking and scoring algorithms
- Response formatting (HTML, JSON, CSV, RSS)

#### 4. **Plugin System** (`searx/plugins/`)
Current plugins include:
- **ahmia_filter**: Filters out onion results from Ahmia
- **calculator**: Inline calculator for mathematical expressions
- **hash_plugin**: Generate hashes for strings
- **hostnames**: Display hostnames of results
- **oa_doi_rewrite**: Open Access DOI resolver
- **self_info**: Display information about the SearXNG instance
- **time_zone**: Time zone converter
- **tor_check**: Check if connection uses Tor (disabled in this instance)
- **unit_converter**: Convert between units
- **tracker_url_remover**: Remove tracking parameters from URLs

#### 5. **Bot Detection & Rate Limiting** (`searx/botdetection/`, `searx/limiter.py`)
- IP-based rate limiting
- User-agent analysis
- Behavioral pattern detection
- CAPTCHA integration capability
- Link token validation

#### 6. **Favicon System** (`searx/favicons/`)
- Multiple favicon resolvers (Google, DuckDuckGo, Yandex, etc.)
- Caching mechanism for performance
- Proxy support for privacy

#### 7. **Localization** (`searx/translations/`)
- Support for 60+ languages
- Weblate integration for community translations
- Dynamic language detection from browser

## ⚙️ Configuration System

### Main Configuration (`searx/settings.yml`)

```yaml
general:
  instance_name: "SearXNG"
  debug: false
  enable_metrics: true

brand:
  docs_url: https://docs.searxng.org/
  public_instances: https://searx.space

search:
  safe_search: 0  # 0: None, 1: Moderate, 2: Strict
  autocomplete: ""  # Options: google, duckduckgo, wikipedia, etc.
  favicon_resolver: ""  # Options: google, duckduckgo, yandex
  default_lang: "auto"
  ban_time_on_fail: 5
  max_ban_time_on_fail: 120

server:
  port: 8888
  bind_address: "127.0.0.1"
  base_url: false
  limiter: false
  public_instance: false
```

### Environment Variables
- `SEARXNG_SETTINGS_PATH`: Path to settings file
- `SEARXNG_DEBUG`: Enable debug mode
- `SEARXNG_PORT`: Server port
- `SEARXNG_BIND_ADDRESS`: Bind address
- `SEARXNG_BASE_URL`: Public URL of instance
- `SEARXNG_LIMITER`: Enable rate limiting
- `SEARXNG_PUBLIC_INSTANCE`: Enable public instance features

## 🐳 Docker Deployment

### Container Architecture
- **Base Image**: Alpine Linux based
- **Web Server**: Granian WSGI server
- **Process Management**: Built-in container orchestration
- **Volumes**:
  - `/etc/searxng`: Configuration files
  - `/var/log/searxng`: Log files
  - `/var/cache/searxng`: Cache data

### Docker Configuration
```dockerfile
EXPOSE 8080
ENV GRANIAN_HOST="::"
ENV GRANIAN_PORT="8080"
ENV GRANIAN_BLOCKING_THREADS="32"
ENV GRANIAN_WORKERS_KILL_TIMEOUT="30s"
```

## 🔧 Customizations in This Instance

Based on recent commits, this instance includes:

1. **Master branch rebuild** (commit: e7501eae)
2. **Docker configuration modifications**
3. **Google.com enforcement** for Google engines
4. **Custom version display** implementation
5. **Tor network check disabled**

## 📊 Performance & Metrics

### Metrics Collection (`searx/metrics/`)
- Search response times per engine
- Error tracking and recording
- Success/failure rates
- OpenMetrics format export at `/metrics`

### Optimization Features
- Parallel engine queries
- Result caching
- Connection pooling
- Static file compression (WhiteNoise)

## 🔒 Security Features

1. **Privacy Protection**:
   - No user tracking
   - No cookies (except preferences)
   - No JavaScript required for basic functionality
   - IP anonymization options

2. **Security Measures**:
   - Rate limiting
   - Bot detection
   - CSRF protection
   - XSS prevention
   - Content Security Policy headers

3. **Network Security**:
   - HTTPS enforcement capability
   - Proxy support for engine requests
   - DNS-over-HTTPS support

## 🔌 API & Integration

### Search API Endpoints
- `/search`: Main search endpoint
- `/autocomplete`: Autocomplete suggestions
- `/preferences`: User preferences
- `/stats`: Instance statistics
- `/config`: Public configuration

### Output Formats
- HTML (default web interface)
- JSON (API responses)
- CSV (data export)
- RSS (feed format)

## 🛠️ Development Tools

### Management Script (`manage`)
- `./manage install`: Install dependencies
- `./manage run`: Run development server
- `./manage test`: Run test suite
- `./manage translations`: Manage translations
- `./manage update`: Update data sources

### Makefile Commands
- `make install`: Setup development environment
- `make run`: Start development server
- `make test`: Run tests
- `make lint`: Code linting
- `make docs`: Build documentation

## 📦 Dependencies

### Core Dependencies
- **Flask**: Web framework
- **Babel**: Internationalization
- **httpx**: HTTP client
- **lxml**: XML/HTML parsing
- **PyYAML**: Configuration parsing
- **Pygments**: Syntax highlighting
- **WhiteNoise**: Static file serving

### Optional Dependencies
- **uvloop**: Performance optimization
- **setproctitle**: Process naming
- **redis/valkey**: Caching backend

## 🧪 Testing

### Test Structure (`tests/`)
- Unit tests for engines
- Integration tests for search pipeline
- UI tests for web interface
- Performance benchmarks

## 🌍 Community & Support

- **IRC**: #searxng on libera.chat
- **Matrix**: #searxng:matrix.org
- **GitHub Issues**: Bug reports and feature requests
- **Wiki**: Community documentation
- **Weblate**: Translation contributions

## 📝 License

SearXNG is licensed under the GNU Affero General Public License v3.0 or later (AGPL-3.0-or-later).

## 🚀 Getting Started

### Quick Start with Docker
```bash
docker pull searxng/searxng
docker run -d -p 8080:8080 searxng/searxng
```

### Development Setup
```bash
git clone https://github.com/searxng/searxng
cd searxng
./manage install
./manage run
```

## 📈 Project Statistics

- **Search Engines**: 214 integrated
- **Plugins**: 11 available
- **Languages**: 60+ supported
- **Active Development**: Regular updates and improvements
- **Community**: Active contributors and maintainers

---

This comprehensive documentation provides a complete overview of the SearXNG project structure, architecture, and capabilities. The project represents a sophisticated privacy-focused metasearch engine with extensive customization options and robust architecture suitable for both personal and public deployments.