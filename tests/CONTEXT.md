# TESTS/ - Comprehensive Testing Suite Directory

## 📁 Directory Overview
This directory contains SearXNG's comprehensive testing infrastructure including unit tests, integration tests, and automated testing tools. The test suite ensures code quality, functionality validation, and regression prevention across all components of the metasearch engine.

## 📂 Directory Structure
```
tests/
├── unit/                     # Unit test suite
│   ├── __init__.py          # Unit test package initialization
│   ├── engines/             # Search engine specific tests
│   │   ├── test_command.py  # Command engine testing
│   │   └── ...              # Individual engine test files
│   ├── network/             # Network layer testing
│   │   ├── __init__.py      # Network test package
│   │   └── test_network.py  # Network utilities testing
│   ├── processors/          # Search processor testing
│   │   ├── __init__.py      # Processor test package
│   │   └── test_online.py   # Online processor testing
│   ├── settings/            # Configuration testing
│   ├── test_*.py           # Core functionality tests
│   └── __pycache__/        # Compiled Python bytecode
├── robot/                   # Robot Framework integration tests
│   └── __pycache__/        # Compiled Python bytecode
└── __pycache__/            # Compiled Python bytecode
```

## 🧪 Unit Testing Suite (`unit/`)

### Core Application Tests
**Testing Framework:** Python unittest module with pytest compatibility
**Coverage:** Comprehensive testing of all core components

#### 📄 Main Component Tests

**`test_webadapter.py`** - Web Request/Response Adapters
- Request parameter parsing and validation
- Form data handling and processing
- URL generation and routing
- Query string manipulation
- HTTP header processing

**`test_webutils.py`** - Web Utility Functions  
- HMAC generation and validation
- Result templating and formatting
- Theme management functions
- Content highlighting utilities
- Security token handling

**`test_utils.py`** - Core Utility Functions
- Text processing and extraction
- HTML parsing and manipulation
- URL validation and cleaning
- Date/time formatting
- File operation utilities

**`test_results.py`** - Search Result Processing
- Result container functionality
- Result aggregation and merging
- Deduplication algorithms
- Result ranking and scoring
- Format conversion (HTML, JSON, CSV)

**`test_search.py`** - Search Pipeline Testing
- Search query processing
- Engine coordination
- Parallel search execution
- Result collection and processing
- Error handling and recovery

**`test_preferences.py`** - User Preferences Management
- Preference validation and storage
- Cookie handling and security
- Settings serialization/deserialization
- User session management
- Configuration inheritance

**`test_locales.py`** - Localization and Internationalization
- Language detection algorithms
- Locale parsing and validation
- Regional preference handling
- Translation system integration
- Multi-language search support

**`test_exceptions.py`** - Error Handling System
- Custom exception classes
- Error message formatting
- Exception propagation
- Recovery mechanisms
- Logging integration

### 🔌 Plugin Testing

**`test_plugins.py`** - Plugin System Core
- Plugin loading and initialization
- Plugin lifecycle management
- Hook execution and coordination
- Plugin configuration validation
- Error isolation and recovery

**`test_plugin_calculator.py`** - Calculator Plugin
- Mathematical expression parsing
- Scientific function calculations
- Unit-aware computations
- Security validation (safe eval)
- Error handling for invalid expressions

**`test_plugin_hash.py`** - Hash Generation Plugin
- Hash algorithm implementations
- Input validation and sanitization
- Multiple hash format support
- Performance testing
- Security considerations

**`test_plugin_self_info.py`** - Self Information Plugin
- Instance information gathering
- Statistics collection and formatting
- Configuration exposure control
- Performance metrics display
- Privacy considerations

### 🔍 Engine Testing (`engines/`)

**Engine Test Structure:**
Each search engine has dedicated test coverage including:

**`test_command.py`** - Command Engine Testing
- Command execution security
- Input sanitization
- Output processing
- Error handling
- Performance monitoring

**Individual Engine Tests:**
- **Request Generation** - Verify proper search request formatting
- **Response Parsing** - Test result extraction from engine responses
- **Error Handling** - Handle network failures and invalid responses
- **Rate Limiting** - Test compliance with engine rate limits
- **Authentication** - API key and OAuth token handling

**Common Engine Test Patterns:**
```python
def test_engine_request():
    # Test search request generation
    
def test_engine_response():
    # Test result parsing
    
def test_engine_error_handling():
    # Test error scenarios
    
def test_engine_pagination():
    # Test multi-page results
```

### 🌐 Network Testing (`network/`)

**`test_network.py`** - Network Layer Testing
- HTTP client configuration
- Connection pooling efficiency
- Timeout handling
- SSL/TLS certificate validation
- Proxy configuration testing
- Network error recovery
- Performance optimization validation

**Network Test Coverage:**
- **Connection Management** - Pool creation and reuse
- **Request/Response Cycle** - End-to-end HTTP testing
- **Error Scenarios** - Network failures and timeouts
- **Security** - Certificate validation and secure connections
- **Performance** - Connection efficiency and speed

### 🔄 Processor Testing (`processors/`)

**`test_online.py`** - Online Result Processor Testing
- Result filtering logic
- Content enhancement processes
- URL processing and validation
- Metadata extraction
- Quality assessment algorithms

**Processor Test Areas:**
- **Input Validation** - Verify processor input handling
- **Processing Logic** - Test core processing algorithms
- **Output Verification** - Validate processed results
- **Error Handling** - Test processor error scenarios
- **Performance** - Benchmark processing speed

### ⚙️ Configuration Testing (`settings/`)

**Settings Test Coverage:**
- **Schema Validation** - Test configuration schema compliance
- **Default Values** - Verify proper default value handling
- **Environment Variables** - Test environment variable override
- **File Loading** - Test configuration file parsing
- **Validation Rules** - Test configuration validation logic

## 🤖 Integration Testing (`robot/`)

### Robot Framework Tests
**Purpose:** End-to-end system testing and user workflow validation

**Test Categories:**
- **Web Interface Testing** - Full browser-based testing
- **Search Workflow** - Complete search process validation
- **API Testing** - REST API endpoint validation
- **Performance Testing** - Load and stress testing
- **Cross-Browser Testing** - Multi-browser compatibility

**Robot Test Structure:**
```robot
*** Test Cases ***
Search Functionality
    Open Browser    http://localhost:8888    chrome
    Input Text      search-input    python programming
    Click Button    search-button
    Page Should Contain    Results for "python programming"
```

## 📊 Test Execution and Coverage

### Running Tests

**Unit Tests:**
```bash
# Run all unit tests
python -m pytest tests/unit/

# Run specific test module
python -m pytest tests/unit/test_search.py

# Run with coverage
python -m pytest --cov=searx tests/unit/
```

**Robot Tests:**
```bash
# Run Robot Framework tests
robot tests/robot/

# Run specific test suite
robot tests/robot/search_tests.robot
```

### Test Configuration

**pytest Configuration:**
- **Test Discovery** - Automatic test file discovery
- **Fixtures** - Shared test setup and teardown
- **Parameterized Tests** - Multiple input testing
- **Mocking** - External dependency mocking
- **Coverage Reporting** - Code coverage analysis

**Common Test Utilities:**
```python
# Mock HTTP requests
@mock.patch('searx.network.get')
def test_engine_request(mock_get):
    # Test implementation

# Parameterized testing
@pytest.mark.parametrize("query,expected", [
    ("test query", "expected result"),
    ("another query", "another result")
])
def test_multiple_inputs(query, expected):
    # Test implementation
```

## 🎯 Testing Best Practices

### Test Organization
- **One Test Per Function** - Single responsibility principle
- **Descriptive Names** - Clear test method naming
- **Setup/Teardown** - Proper test isolation
- **Mock External Dependencies** - Avoid network calls in unit tests
- **Test Data Management** - Organized test fixtures

### Coverage Goals
- **Unit Tests** - 90%+ code coverage target
- **Integration Tests** - Critical path coverage
- **Engine Tests** - All active engines tested
- **Error Scenarios** - Exception handling coverage
- **Performance Tests** - Benchmark critical operations

### Continuous Integration
- **Automated Test Runs** - Tests run on every commit
- **Multiple Python Versions** - Test across supported versions
- **Cross-Platform Testing** - Linux, macOS, Windows compatibility
- **Performance Regression** - Benchmark tracking
- **Security Testing** - Vulnerability scanning

### Test Data Management
- **Mock Data** - Realistic test data without external dependencies
- **Fixture Management** - Reusable test setup
- **Data Isolation** - Tests don't affect each other
- **Clean State** - Fresh state for each test run

## 🔧 Development Testing Tools

### Test Utilities
- **Mock Servers** - Simulate external search engines
- **Test Databases** - Temporary test data storage
- **Network Simulators** - Test network failure scenarios
- **Performance Profilers** - Identify performance bottlenecks

### Quality Assurance
- **Code Coverage** - Measure test completeness
- **Static Analysis** - Code quality checking
- **Security Scanning** - Vulnerability detection
- **Performance Monitoring** - Speed and resource usage tracking

This comprehensive testing suite ensures SearXNG maintains high quality, reliability, and performance standards while enabling confident development and deployment of new features.