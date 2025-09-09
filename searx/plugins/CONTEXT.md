# SEARX/PLUGINS/ - Plugin System Directory

## 📁 Directory Overview
This directory contains SearXNG's extensible plugin system that allows adding custom functionality to search processing, result filtering, and user interface enhancement. Plugins can hook into different phases of the search pipeline to modify behavior without changing core code.

## 📂 Plugin Architecture Files
```
searx/plugins/
├── __init__.py              # Plugin system documentation and examples
├── _core.py                 # Plugin framework core classes and interfaces
├── ahmia_filter.py          # Filter Ahmia onion results
├── calculator.py            # Inline calculator for mathematical expressions
├── hash_plugin.py           # Generate hashes (MD5, SHA, etc.) for strings
├── hostnames.py             # Display result hostnames for transparency
├── oa_doi_rewrite.py        # Open Access DOI resolver
├── self_info.py             # Display SearXNG instance information
├── time_zone.py             # Time zone converter and world clock
├── tor_check.py             # Check if connection uses Tor network
├── tracker_url_remover.py   # Remove tracking parameters from URLs
└── unit_converter.py        # Convert between units (metric, imperial, etc.)
```

## 🏗️ Plugin Framework (`_core.py` - 10,389 bytes)

### Core Classes & Components

#### `PluginInfo` Class
**Purpose:** Metadata container for plugin information displayed in preferences
```python
@dataclass
class PluginInfo:
    id: str                    # Unique plugin identifier
    name: str                  # Display name for users
    description: str           # Plugin description
    preference_section: str    # UI section (general, ui, privacy, query)
    examples: list[str]        # Usage examples for documentation
```

#### `Plugin` Abstract Base Class
**Purpose:** Base class for all plugins with standardized hooks
```python
class Plugin:
    def pre_search(self, request, search):     # Before search execution
        pass
    
    def post_search(self, request, search):    # After search completion
        pass
        
    def on_result(self, request, search, result):  # Per result processing
        pass
```

#### `PluginStorage` Class
**Purpose:** Persistent storage system for plugin data
- **Configuration Management** - Plugin-specific settings storage
- **Data Persistence** - Store plugin state between searches
- **Thread Safety** - Safe concurrent access to plugin data

### Plugin Lifecycle Hooks
1. **`pre_search`** - Execute before search engines are called
2. **`post_search`** - Execute after all search results are collected
3. **`on_result`** - Execute for each individual search result

## 🔌 Built-in Plugins

### 🧮 Calculator Plugin (`calculator.py` - 7,323 bytes)
**Purpose:** Inline mathematical expression evaluation

**Features:**
- **Mathematical Expressions** - Basic arithmetic (+, -, *, /)
- **Scientific Functions** - sin, cos, tan, log, sqrt, etc.
- **Constants** - pi, e, mathematical constants
- **Unit-Aware Calculations** - Handle units in expressions
- **Safe Evaluation** - Sandboxed math evaluation

**Usage Examples:**
- `2 + 2` → Direct answer: 4
- `sin(pi/2)` → Direct answer: 1.0  
- `sqrt(144)` → Direct answer: 12.0
- `convert 100 USD to EUR` → Currency conversion

**Implementation:**
- Uses `eval()` with restricted namespace for safety
- Supports complex mathematical expressions
- Integrates with unit conversion system
- Returns direct answers in SearXNG interface

### 🔒 Hash Plugin (`hash_plugin.py` - 2,151 bytes)  
**Purpose:** Generate cryptographic hashes for input strings

**Supported Hash Types:**
- **MD5** - Legacy hash function
- **SHA1** - Older secure hash
- **SHA256** - Modern secure hash  
- **SHA512** - High-security hash
- **Blake2b** - Modern fast hash

**Usage Examples:**
- `md5 hello world` → Generate MD5 hash
- `sha256 password123` → Generate SHA256 hash
- `hash searxng` → Generate multiple hashes

**Security Features:**
- **Safe Input Handling** - Prevent injection attacks
- **Multiple Algorithms** - Support various hash types
- **Direct Answers** - Display hashes immediately

### 🌐 Hostname Display (`hostnames.py` - 6,620 bytes)
**Purpose:** Display source hostnames for search results transparency

**Functionality:**
- **Hostname Extraction** - Extract domain from result URLs
- **Visual Integration** - Add hostname badges to results
- **Privacy Enhancement** - Show result sources clearly
- **User Trust** - Increase transparency about result origins

**Implementation:**
- Hooks into `on_result` to modify each search result
- Parses URLs to extract clean hostnames  
- Adds hostname information to result metadata
- Integrates with result templates for display

### 🧹 Tracker URL Remover (`tracker_url_remover.py` - 1,830 bytes)
**Purpose:** Remove tracking parameters from search result URLs

**Tracked Parameters Removed:**
- **Google Analytics** - utm_source, utm_medium, utm_campaign
- **Facebook** - fbclid parameters
- **Amazon** - ref, tag parameters
- **Generic Tracking** - Various common tracking parameters

**Privacy Benefits:**
- **Prevent Tracking** - Remove cross-site tracking
- **Clean URLs** - Simplify result URLs
- **User Privacy** - Reduce data collection

### 📏 Unit Converter (`unit_converter.py` - 5,051 bytes)
**Purpose:** Convert between different units of measurement

**Supported Conversions:**
- **Length** - meters, feet, inches, kilometers, miles
- **Weight** - grams, pounds, ounces, kilograms  
- **Temperature** - Celsius, Fahrenheit, Kelvin
- **Volume** - liters, gallons, cups, milliliters
- **Speed** - mph, km/h, m/s, knots
- **Energy** - joules, calories, BTU, kWh

**Usage Examples:**
- `convert 100 km to miles` → 62.14 miles
- `32 fahrenheit to celsius` → 0°C
- `5 feet to meters` → 1.524 meters

### 🕒 Time Zone Converter (`time_zone.py` - 2,457 bytes)
**Purpose:** Convert times between different time zones

**Features:**
- **World Clock** - Display current time in major cities
- **Time Conversion** - Convert between any time zones
- **DST Awareness** - Handle daylight saving time
- **Multiple Formats** - Support various time formats

**Usage Examples:**
- `time in tokyo` → Current time in Tokyo
- `convert 3pm EST to PST` → 12pm PST
- `world clock` → Times in major world cities

### 🔍 Self Information (`self_info.py` - 1,916 bytes)
**Purpose:** Display information about the SearXNG instance

**Information Displayed:**
- **Instance Version** - SearXNG version number
- **Engine Count** - Number of active search engines
- **Configuration** - Basic instance settings
- **Statistics** - Usage and performance metrics

**Usage:**
- `searxng info` → Display instance information
- Helps users understand the search instance they're using

### 🧅 Ahmia Filter (`ahmia_filter.py` - 1,822 bytes)
**Purpose:** Filter .onion results from Ahmia dark web search engine

**Functionality:**
- **Content Filtering** - Remove inappropriate .onion results
- **Safety Enhancement** - Improve dark web search safety
- **Configurable Rules** - Adjustable filtering criteria

### 🔗 Open Access DOI Rewriter (`oa_doi_rewrite.py` - 2,699 bytes)
**Purpose:** Rewrite DOI links to point to open access versions

**Features:**
- **DOI Detection** - Identify DOI links in search results
- **Open Access Lookup** - Find freely accessible versions
- **Link Rewriting** - Replace paywalled links with open access
- **Academic Access** - Improve access to scientific papers

### 🔒 Tor Connection Check (`tor_check.py` - 2,788 bytes)
**Purpose:** Detect and display Tor network usage status

**Functionality:**
- **Tor Detection** - Check if connection uses Tor network
- **Privacy Indicator** - Show Tor status to users
- **Network Information** - Display connection privacy level
- **User Awareness** - Inform users about their privacy status

**Note:** Currently disabled in this SearXNG instance based on recent commits.

## 🔧 Plugin Development

### Plugin Creation Process
1. **Inherit from Plugin** - Extend the base Plugin class
2. **Implement Hooks** - Add pre_search, post_search, or on_result methods
3. **Define PluginInfo** - Provide metadata for user interface
4. **Register Plugin** - Add to plugin registry
5. **Test Integration** - Verify plugin works with search pipeline

### Hook Usage Patterns

#### Pre-Search Hook
```python
def pre_search(self, request, search):
    # Modify search query or parameters
    # Add custom engines or filters
    # Set up plugin state
    return []  # Return empty list or direct answers
```

#### Post-Search Hook  
```python
def post_search(self, request, search):
    # Process complete search results
    # Add answer boxes or additional information
    # Aggregate data from multiple engines
    return [Answer(...)]  # Return direct answers
```

#### On-Result Hook
```python
def on_result(self, request, search, result):
    # Modify individual search results
    # Filter out unwanted results
    # Add metadata or enhancements
    return result  # Return modified result
```

### Plugin Configuration
```python
class MyPlugin(Plugin):
    def __init__(self, plg_cfg):
        super().__init__(plg_cfg)
        self.info = PluginInfo(
            id="my_plugin",
            name="My Plugin", 
            description="Plugin description",
            preference_section="general"
        )
```

## 🎯 Plugin System Features

### Configuration Management
- **User Preferences** - Plugins can be enabled/disabled per user
- **Instance Settings** - Admin can configure plugin behavior
- **Dynamic Loading** - Plugins loaded based on configuration
- **Dependency Management** - Handle plugin dependencies

### Performance Optimization
- **Lazy Loading** - Load plugins only when needed
- **Efficient Hooks** - Minimize performance impact
- **Error Isolation** - Plugin failures don't break search
- **Resource Management** - Control plugin resource usage

### User Interface Integration
- **Preferences Panel** - Plugin settings in user preferences
- **Visual Integration** - Plugins enhance search interface
- **Help Documentation** - Built-in usage examples
- **Internationalization** - Multi-language plugin support

This plugin system demonstrates SearXNG's extensibility and customization capabilities, allowing users and administrators to tailor the search experience to specific needs while maintaining system stability and performance.