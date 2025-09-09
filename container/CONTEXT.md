# CONTAINER/ - Docker Containerization Directory

## 📁 Directory Overview
This directory contains all Docker-related files for containerizing SearXNG. It provides a complete containerization strategy with multi-stage builds, optimized base images, and production-ready deployment configurations. The setup enables easy deployment, scaling, and management of SearXNG instances.

## 📂 Directory Structure
```
container/
├── dist.dockerfile           # Production distribution image
├── builder.dockerfile        # Build stage image
├── base.yml                 # Base image configuration
├── base-builder.yml         # Builder base image configuration  
└── entrypoint.sh            # Container startup script
```

## 🐳 Docker Architecture

### Multi-Stage Build Process
**Strategy:** Optimized multi-stage build for minimal production image size
**Stages:** 
1. **Builder Stage** - Compile and build application
2. **Distribution Stage** - Lean production runtime

### 🏗️ Build Stage (`builder.dockerfile` - 800 bytes)
**Purpose:** Compile SearXNG and build all dependencies in isolated environment

**Build Operations:**
- **Dependencies Installation** - Install build-time dependencies
- **Python Environment** - Create virtual environment with production packages
- **Frontend Assets** - Compile CSS, JavaScript, and optimize images
- **Asset Compilation** - Generate optimized static assets
- **Version Freezing** - Lock dependency versions for reproducible builds

**Base Image:** Uses multi-architecture builder base
**Build Tools:** Python, Node.js, build-essential, development libraries
**Output:** Compiled application with virtual environment

### 📦 Distribution Image (`dist.dockerfile` - 1,738 bytes)
**Purpose:** Lean production image with only runtime dependencies

**Key Features:**
- **Minimal Runtime** - Only production dependencies included
- **Security Hardening** - Non-root user execution
- **Optimized Size** - Minimal layer count and file system
- **Health Monitoring** - Built-in health check capabilities
- **Configuration Management** - External configuration support

**Base Image:** `ghcr.io/searxng/base:searxng`
**WSGI Server:** Granian high-performance WSGI server
**User:** `searxng:searxng` (non-root execution)
**Ports:** Exposes port 8080

**Container Labels (OCI Specification):**
```dockerfile
LABEL org.opencontainers.image.created="$CREATED"
LABEL org.opencontainers.image.description="SearXNG is a metasearch engine. Users are neither tracked nor profiled."
LABEL org.opencontainers.image.documentation="https://docs.searxng.org/admin/installation-docker"
LABEL org.opencontainers.image.licenses="AGPL-3.0-or-later"
LABEL org.opencontainers.image.source="$VCS_URL"
LABEL org.opencontainers.image.title="SearXNG"
LABEL org.opencontainers.image.url="https://searxng.org"
LABEL org.opencontainers.image.version="$VERSION"
```

## ⚙️ Runtime Configuration

### Environment Variables
**Production Server (Granian):**
- `GRANIAN_PROCESS_NAME="searxng"` - Process identification
- `GRANIAN_INTERFACE="wsgi"` - WSGI interface mode
- `GRANIAN_HOST="::"` - Listen on all interfaces (IPv4/IPv6)
- `GRANIAN_PORT="8080"` - HTTP port
- `GRANIAN_WEBSOCKETS="false"` - WebSocket support disabled
- `GRANIAN_LOOP="uvloop"` - High-performance event loop
- `GRANIAN_BLOCKING_THREADS="32"` - Thread pool size
- `GRANIAN_WORKERS_KILL_TIMEOUT="30s"` - Graceful shutdown timeout
- `GRANIAN_BLOCKING_THREADS_IDLE_TIMEOUT="5m"` - Thread idle timeout

**SearXNG Configuration:**
- `SEARXNG_VERSION="$VERSION"` - Version identification
- `SEARXNG_SETTINGS_PATH="$CONFIG_PATH/settings.yml"` - Configuration file path

### Volume Mounts
**Configuration Volume:** `$CONFIG_PATH`
- **Purpose:** External configuration management
- **Contents:** settings.yml, custom configurations
- **Persistence:** Configuration survives container updates

**Data Volume:** `$DATA_PATH` 
- **Purpose:** Persistent data storage
- **Contents:** Cache data, logs, temporary files
- **Persistence:** Data survives container restarts

## 🚀 Container Startup (`entrypoint.sh` - 2,560 bytes)

### Startup Process
**Smart Initialization:** Comprehensive startup validation and configuration

#### 🔍 Validation Functions
**`check_file()`** - File existence validation
- Verify required files are present
- Exit gracefully with error messages if files missing
- Prevent startup with incomplete configuration

**`check_directory()`** - Directory existence validation  
- Ensure required directories exist
- Create informative error messages
- Prevent startup with invalid volume mounts

**`setup_ownership()`** - File ownership management
- Ensure proper file ownership (searxng:searxng)
- Automatic ownership correction when running as root
- Warning messages for ownership issues
- Security hardening through proper permissions

#### 📁 Volume Management
**`volume_handler()`** - Volume mount validation
- Check mounted volumes exist and are accessible
- Validate directory structure
- Set proper ownership and permissions
- Log volume status for debugging

#### ⚙️ Configuration Management  
**`config_handler()`** - Dynamic configuration management
- **First Run:** Create configuration from template
- **Secret Generation:** Auto-generate secure secret keys
- **Updates:** Detect configuration template updates
- **Backup:** Preserve existing configurations during updates
- **Merge Assistance:** Provide new config versions alongside existing

**Configuration Update Process:**
1. Check if configuration file exists
2. Compare template modification times
3. Create `.new` version if template is newer
4. Generate secure random secrets
5. Preserve user customizations

#### 🔑 Security Features
**Secret Key Generation:**
```bash
sed -i "s/ultrasecretkey/$(head -c 24 /dev/urandom | base64 | tr -dc 'a-zA-Z0-9')/g" "$target"
```
- **Automatic:** Generate unique secret keys on first run
- **Secure:** Use cryptographically secure random generation
- **Safe Characters:** Alphanumeric characters only
- **Sufficient Length:** 24 characters base64 encoded

**User Security:**
- **Non-root Execution:** Run as searxng user
- **Ownership Validation:** Ensure proper file ownership
- **Permission Management:** Set appropriate file permissions

### Application Execution
**Final Command:**
```bash
exec /usr/local/searxng/.venv/bin/granian searx.webapp:app
```

**Granian WSGI Server Benefits:**
- **High Performance** - Fast request processing
- **Async Support** - Non-blocking I/O operations
- **Resource Efficiency** - Low memory footprint
- **Production Ready** - Robust error handling
- **HTTP/2 Support** - Modern protocol support

## 📋 Base Image Configuration

### Base Image Specification (`base.yml` - 1,004 bytes)
**Multi-Architecture Support:** AMD64, ARM64, ARM/v7
**Base OS:** Alpine Linux (minimal, security-focused)
**Runtime Dependencies:** Python runtime, system libraries
**User Management:** Pre-configured searxng user and group

### Builder Base (`base-builder.yml` - 495 bytes)  
**Build Environment:** Complete development toolchain
**Compilers:** GCC, Make, development headers
**Languages:** Python, Node.js build environments
**Tools:** git, curl, build utilities

## 🎯 Container Features

### Production Readiness
- **Health Checks** - Built-in application health monitoring
- **Graceful Shutdown** - Proper SIGTERM handling
- **Resource Limits** - Configurable CPU and memory limits
- **Logging** - Structured logging to stdout/stderr
- **Monitoring** - Prometheus metrics support

### Security Hardening
- **Non-root User** - Execute as dedicated user account
- **Minimal Attack Surface** - Only essential packages included
- **Regular Updates** - Base image security updates
- **Secret Management** - Secure handling of sensitive data

### Operational Benefits
- **Fast Startup** - Optimized initialization process
- **Small Image Size** - Efficient layer usage and minimal dependencies
- **Version Consistency** - Reproducible builds with locked dependencies
- **Easy Updates** - Configuration preservation during updates
- **Backup Friendly** - Clear separation of configuration and data

### Development Support
- **Volume Mounting** - External configuration and data mounting
- **Environment Overrides** - Flexible configuration via environment variables
- **Debug Support** - Detailed logging and error reporting
- **Hot Configuration** - Configuration updates without rebuilds

## 🚀 Deployment Scenarios

### Single Instance
```bash
docker run -d \
  -p 8080:8080 \
  -v searxng-config:/etc/searxng \
  -v searxng-data:/var/lib/searxng \
  ghcr.io/searxng/searxng
```

### High Availability
- **Load Balancing** - Multiple container instances
- **Shared Storage** - Common configuration and data volumes
- **Health Monitoring** - Container orchestration integration
- **Rolling Updates** - Zero-downtime deployments

### Development Environment
- **Local Builds** - Custom image building support
- **Configuration Testing** - Easy configuration experimentation
- **Debugging** - Development-friendly logging and access

This container directory provides a complete, production-ready containerization solution for SearXNG with emphasis on security, performance, and operational simplicity.