# UTILS/ - Development and Deployment Utilities Directory

## 📁 Directory Overview
This directory contains shell scripts, Python utilities, and configuration helpers for developing, testing, building, and deploying SearXNG. These tools automate common development tasks, system administration, and deployment processes across different Linux distributions.

## 📂 Directory Structure
```
utils/
├── lib.sh                    # Core utility library with common functions
├── searxng.sh                # Main SearXNG installation and management script
├── get_setting.py            # Python script to extract configuration values
├── searxng_check.py          # Health check and validation script
├── makefile.include          # Makefile utilities and common targets
├── brand.sh                  # Branding and URL configuration
├── lib_*.sh                  # Specialized utility libraries:
│   ├── lib_govm.sh           # Go version management
│   ├── lib_nvm.sh            # Node.js version management  
│   ├── lib_redis.sh          # Redis server utilities
│   ├── lib_valkey.sh         # Valkey server utilities
│   ├── lib_sxng_container.sh # Container/Docker utilities
│   ├── lib_sxng_data.sh      # Data management utilities
│   ├── lib_sxng_node.sh      # Node.js build utilities
│   ├── lib_sxng_static.sh    # Static asset management
│   ├── lib_sxng_test.sh      # Testing utilities
│   ├── lib_sxng_themes.sh    # Theme development utilities
│   ├── lib_sxng_vite.sh      # Vite build system integration
│   └── lib_sxng_weblate.sh   # Translation management
└── templates/                # Configuration templates
```

## 🛠️ Core Utilities

### 📜 Main Management Script (`searxng.sh` - 32,826 bytes)
**Purpose:** Primary installation, configuration, and management script for SearXNG

**Key Features:**
- **Multi-Distribution Support** - Ubuntu, Debian, Arch Linux, Fedora
- **Service Management** - systemd service installation and control
- **Web Server Integration** - Apache and nginx configuration
- **Python Environment** - Virtual environment setup and management
- **Security Configuration** - User permissions and service isolation
- **Package Management** - Distribution-specific package installation

**Service Configuration:**
```bash
SERVICE_NAME="searxng"
SERVICE_USER="searxng" 
SERVICE_HOME="/usr/local/searxng"
SEARXNG_SETTINGS_PATH="/etc/searxng/settings.yml"
SEARXNG_UWSGI_APP="searxng.ini"
```

**Package Dependencies by Distribution:**
- **Debian/Ubuntu:** python3-dev, python3-babel, uwsgi, git, build-essential
- **Arch Linux:** python, python-pip, python-lxml, uwsgi, base-devel  
- **Fedora:** python3-devel, uwsgi-plugin-python3, @development-tools

**Functions:**
- `searxng_install()` - Complete SearXNG installation
- `searxng_update()` - Update existing installation
- `searxng_settings()` - Configuration management
- `searxng_service()` - systemd service operations

### 📚 Core Library (`lib.sh` - 44,885 bytes)
**Purpose:** Foundation library providing common functions for all other scripts

**Key Functionality:**
- **System Detection** - Identify Linux distribution and version
- **Package Management** - Distribution-agnostic package operations
- **Service Operations** - systemd service management
- **File Operations** - Safe file manipulation and templating
- **Network Utilities** - Port checking and URL validation
- **Logging System** - Structured logging with colors and levels
- **Error Handling** - Robust error checking and recovery

**System Detection:**
```bash
DIST_ID       # Distribution identifier (ubuntu, debian, arch, fedora)
DIST_VERS     # Distribution version
DIST_ARCH     # System architecture
KERNEL        # Kernel version
```

**Common Functions:**
- `pkg_install()` - Install packages across distributions
- `systemd_*()` - systemd service management functions
- `backup_file()` - Safe file backup before modification
- `template_*()` - Configuration file templating
- `wait_key()` - Interactive user prompts

### 🔧 Configuration Management (`get_setting.py` - 3,642 bytes)
**Purpose:** Extract and validate configuration values from settings files

**Features:**
- **YAML Parsing** - Read SearXNG settings.yml configuration
- **Environment Variable Support** - Override settings via environment
- **Validation** - Check configuration validity
- **Default Handling** - Provide sensible defaults for missing settings

**Usage:**
```python
# Extract specific settings
python utils/get_setting.py server.port
python utils/get_setting.py general.instance_name
```

### 🏥 Health Check (`searxng_check.py` - 1,392 bytes)
**Purpose:** System health validation and problem diagnosis

**Health Checks:**
- **Service Status** - Verify SearXNG service is running
- **Configuration Validation** - Check settings.yml syntax
- **Network Connectivity** - Test engine connectivity
- **Resource Usage** - Monitor memory and CPU usage
- **Database Access** - Verify cache database connectivity

## 📦 Specialized Libraries

### 🐳 Container Utilities (`lib_sxng_container.sh` - 8,722 bytes)
**Purpose:** Docker and container management functions

**Container Operations:**
- **Image Building** - Build SearXNG Docker images
- **Container Management** - Start, stop, update containers
- **Volume Management** - Handle persistent data volumes
- **Network Configuration** - Container networking setup
- **Health Monitoring** - Container health checks

**Key Functions:**
- `build_container()` - Build SearXNG container image
- `run_container()` - Start SearXNG container
- `update_container()` - Update running container
- `container_logs()` - Access container logs

### 🌐 Frontend Build (`lib_sxng_vite.sh` - 1,892 bytes)
**Purpose:** Frontend asset building with Vite

**Build Operations:**
- **Development Server** - Start Vite dev server
- **Production Build** - Generate optimized assets
- **Watch Mode** - Continuous building during development
- **Asset Optimization** - Minification and compression

**Functions:**
- `vite_dev()` - Start development server
- `vite_build()` - Production build
- `vite_clean()` - Clean build artifacts

### 🎨 Theme Development (`lib_sxng_themes.sh` - 1,161 bytes)
**Purpose:** Theme development and customization utilities

**Theme Operations:**
- **Theme Installation** - Install custom themes
- **Asset Compilation** - Compile theme assets
- **Theme Switching** - Change active theme
- **Development Mode** - Live theme development

### 📊 Testing Utilities (`lib_sxng_test.sh` - 4,063 bytes)
**Purpose:** Automated testing and quality assurance

**Testing Features:**
- **Unit Tests** - Run Python unit test suite
- **Integration Tests** - Full system integration testing
- **Engine Tests** - Individual search engine validation
- **Performance Tests** - Load and performance testing
- **Code Quality** - Linting and style checking

**Test Functions:**
- `test_unit()` - Run unit test suite
- `test_integration()` - Run integration tests
- `test_engines()` - Test search engines
- `test_performance()` - Performance benchmarks

### 💾 Data Management (`lib_sxng_data.sh` - 2,176 bytes)
**Purpose:** Data update and maintenance utilities

**Data Operations:**
- **Engine Data Updates** - Update search engine configurations
- **Currency Data** - Update exchange rates
- **Wikidata Updates** - Refresh Wikidata information
- **Locale Updates** - Update language and locale data

**Update Functions:**
- `update_engine_data()` - Refresh engine configurations
- `update_currency_data()` - Update currency exchange rates
- `update_wikidata()` - Refresh Wikidata information

### 🌍 Translation Management (`lib_sxng_weblate.sh` - 7,485 bytes)
**Purpose:** Internationalization and translation utilities

**Translation Features:**
- **Weblate Integration** - Sync with translation service
- **Message Extraction** - Extract translatable strings
- **Translation Compilation** - Compile translation catalogs
- **Locale Management** - Manage supported locales

**Translation Functions:**
- `extract_messages()` - Extract strings for translation
- `compile_translations()` - Compile translation files
- `sync_weblate()` - Synchronize with Weblate service
- `validate_translations()` - Check translation completeness

### 🚀 Static Assets (`lib_sxng_static.sh` - 3,828 bytes)
**Purpose:** Static asset management and optimization

**Asset Operations:**
- **Asset Compilation** - Compile CSS, JavaScript
- **Image Processing** - Optimize images and icons
- **Cache Busting** - Generate versioned asset names
- **CDN Preparation** - Prepare assets for CDN deployment

### 🗄️ Database Utilities (`lib_redis.sh`, `lib_valkey.sh`)
**Purpose:** Redis and Valkey cache database management

**Database Operations:**
- **Server Installation** - Install database servers
- **Configuration** - Configure database settings
- **Monitoring** - Monitor database performance
- **Backup/Restore** - Database backup operations

### 🔧 Version Management (`lib_nvm.sh`, `lib_govm.sh`)
**Purpose:** Node.js and Go version management

**Version Features:**
- **Multiple Versions** - Install and manage multiple versions
- **Project Settings** - Per-project version configuration
- **Automatic Switching** - Auto-switch versions based on project
- **Build Integration** - Integration with build processes

## ⚙️ Configuration Templates (`templates/`)

### Template System
- **Apache Configuration** - Virtual host templates
- **nginx Configuration** - Server block templates  
- **systemd Services** - Service unit file templates
- **Environment Files** - Environment configuration templates

### Makefile Integration (`makefile.include`)
**Purpose:** Provide common Makefile targets and utilities

**Common Targets:**
- `install` - Install development dependencies
- `test` - Run test suites
- `lint` - Code quality checking
- `build` - Build production assets
- `docs` - Generate documentation

**Usage in Main Makefile:**
```makefile
include utils/makefile.include
```

## 🎯 Key Features

### Multi-Distribution Support
- **Package Management** - Handles apt, pacman, dnf package managers
- **Service Integration** - systemd service configuration
- **Path Conventions** - Respects distribution-specific paths
- **Dependency Resolution** - Distribution-specific dependencies

### Development Workflow
- **Live Reloading** - Development server with hot reload
- **Asset Pipeline** - Modern frontend build system
- **Testing Integration** - Automated test execution
- **Code Quality** - Linting and formatting tools

### Production Deployment
- **Service Management** - systemd service creation
- **Web Server Config** - Apache and nginx integration
- **Security Hardening** - Proper user permissions and isolation
- **Monitoring** - Health checks and logging

### Maintenance Operations
- **Updates** - Automated update procedures
- **Backups** - Configuration and data backup
- **Migration** - Version migration utilities
- **Monitoring** - System health monitoring

This utils directory provides a comprehensive toolkit for managing SearXNG across the entire development and deployment lifecycle, from initial development through production deployment and ongoing maintenance.