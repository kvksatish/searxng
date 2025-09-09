# SEARX/ENGINES/ - Search Engine Implementations Directory

## 📁 Directory Overview
This directory contains **214 individual search engine implementations**, each as a Python module. These engines form the backbone of SearXNG's metasearch capabilities, covering virtually every category of online search from general web search to specialized academic databases.

## 📊 Engine Statistics
- **Total Engines**: 214 implemented
- **Engine Types**: Online search, API-based, XML feeds, JSON APIs, HTML scraping
- **Categories**: 12+ categories (general, images, videos, news, maps, music, science, files, etc.)
- **Languages**: Multi-language support with localization
- **Protocols**: HTTP/HTTPS, REST APIs, GraphQL, RSS/XML feeds

## 🔧 Core Engine Architecture Files
- **`__init__.py`** - Engine loader, initialization, and registry management
- **`__builtins__.pyi`** - Type definitions for engine development
- **`base.py`** - Base engine class and common functionality

## 🗂️ Engine Categories & Examples

### 🌐 General Web Search Engines
- **`google.py`** - Google web search with advanced features
- **`bing.py`** - Microsoft Bing search engine
- **`duckduckgo.py`** - Privacy-focused DuckDuckGo search
- **`startpage.py`** - Startpage proxy search
- **`qwant.py`** - French privacy-focused search
- **`yahoo.py`** - Yahoo search integration
- **`yandex.py`** - Russian Yandex search engine
- **`searx.py`** - Other SearXNG instances
- **`ask.py`** - Ask.com search engine
- **`mojeek.py`** - Independent UK search engine

### 🖼️ Image Search Engines  
- **`google_images.py`** - Google Images search
- **`bing_images.py`** - Bing Images search
- **`duckduckgo_images.py`** - DuckDuckGo Images
- **`flickr.py`** - Flickr photo search
- **`unsplash.py`** - Unsplash stock photos
- **`pixabay.py`** - Pixabay image search
- **`deviantart.py`** - DeviantArt artwork
- **`adobe_stock.py`** - Adobe Stock images
- **`tineye.py`** - Reverse image search
- **`wallhaven.py`** - Wallpaper search

### 🎬 Video Search Engines
- **`youtube_noapi.py`** - YouTube search (HTML scraping)
- **`youtube_api.py`** - YouTube search (API-based)
- **`vimeo.py`** - Vimeo video search
- **`dailymotion.py`** - Dailymotion videos
- **`google_videos.py`** - Google Videos search
- **`bing_videos.py`** - Bing Videos search
- **`peertube.py`** - PeerTube federated videos
- **`bitchute.py`** - BitChute video platform
- **`bilibili.py`** - Chinese Bilibili videos

### 📰 News & Media Engines
- **`google_news.py`** - Google News aggregation
- **`bing_news.py`** - Bing News search  
- **`yahoo_news.py`** - Yahoo News search
- **`reddit.py`** - Reddit post search
- **`hackernews.py`** - Hacker News search
- **`lobste.rs.py`** - Lobste.rs tech news
- **`lemmy.py`** - Lemmy federated posts
- **`ansa.py`** - ANSA Italian news
- **`wikinews.py`** - Wikinews articles

### 🎵 Music & Audio Engines
- **`soundcloud.py`** - SoundCloud audio search
- **`bandcamp.py`** - Bandcamp music search
- **`genius.py`** - Genius lyrics search
- **`musicbrainz.py`** - MusicBrainz database
- **`yandex_music.py`** - Yandex Music search
- **`radio_browser.py`** - Internet radio stations
- **`spotify.py`** - Spotify music search
- **`lastfm.py`** - Last.fm music database

### 🗺️ Maps & Location Engines
- **`openstreetmap.py`** - OpenStreetMap search
- **`apple_maps.py`** - Apple Maps integration
- **`google_maps.py`** - Google Maps search
- **`photon.py`** - Photon geocoding service
- **`nominatim.py`** - Nominatim address search

### 🔬 Academic & Research Engines
- **`arxiv.py`** - arXiv preprint repository
- **`pubmed.py`** - PubMed medical literature
- **`semantic_scholar.py`** - Semantic Scholar papers
- **`crossref.py`** - Crossref DOI database
- **`google_scholar.py`** - Google Scholar search
- **`microsoft_academic.py`** - Microsoft Academic
- **`astrophysics_data_system.py`** - NASA ADS
- **`core.py`** - CORE academic papers
- **`researchgate.py`** - ResearchGate papers
- **`pdbe.py`** - Protein Data Bank Europe

### 💻 Technology & Development
- **`github.py`** - GitHub repository search
- **`gitlab.py`** - GitLab project search  
- **`bitbucket.py`** - Bitbucket repositories
- **`codeberg.py`** - Codeberg Git hosting
- **`sourcehut.py`** - SourceHut project search
- **`stackoverflow.py`** - Stack Overflow Q&A
- **`searchcode.py`** - Source code search
- **`dockerhub.py`** - Docker Hub images
- **`npm.py`** - NPM package registry
- **`pypi.py`** - Python Package Index

### 📚 Reference & Knowledge
- **`wikipedia.py`** - Wikipedia encyclopedia 
- **`wikidata.py`** - Wikidata knowledge base
- **`wikicommons.py`** - Wikimedia Commons media
- **`dictzone.py`** - Dictionary lookups
- **`wordnik.py`** - Word definitions and usage
- **`currency.py`** - Currency conversion
- **`wolframalpha_noapi.py`** - Wolfram Alpha (scraping)
- **`wolframalpha_api.py`** - Wolfram Alpha (API)

### 🛒 Shopping & Commerce
- **`amazon.py`** - Amazon product search
- **`ebay.py`** - eBay marketplace search
- **`shopping.py`** - Google Shopping results
- **`pricerunner.py`** - Price comparison

### 📁 File & Document Search
- **`annas_archive.py`** - Anna's Archive book search
- **`zlibrary.py`** - Z-Library document search
- **`library_genesis.py`** - Library Genesis books
- **`openverse.py`** - Creative Commons media
- **`google_drive.py`** - Google Drive files
- **`archive_org.py`** - Internet Archive search

### 🔗 Social Media & Forums
- **`mastodon.py`** - Mastodon federated search
- **`lemmy.py`** - Lemmy federated communities  
- **`tootfinder.py`** - Mastodon toot search
- **`9gag.py`** - 9GAG meme search
- **`imgur.py`** - Imgur image hosting

### 🏴‍☠️ Torrent & P2P Engines
- **`1337x.py`** - 1337x torrent search
- **`piratebay.py`** - The Pirate Bay search
- **`torznab.py`** - Torznab API protocol
- **`tokyotoshokan.py`** - Tokyo Toshokan
- **`bt4g.py`** - BT4G torrent search
- **`www1x.py`** - WWW1X torrent search

### 🌐 Regional & Language-Specific
- **`baidu.py`** - Chinese Baidu search engine
- **`360search.py`** - Chinese 360 Search
- **`naver.py`** - Korean Naver search
- **`seznam.py`** - Czech Seznam.cz
- **`qwant.py`** - French Qwant search
- **`metager.py`** - German MetaGer search

### 🔧 System & Infrastructure
- **`valkey_server.py`** - Valkey server search
- **`mongodb.py`** - MongoDB search integration
- **`elasticsearch.py`** - Elasticsearch queries
- **`solr.py`** - Apache Solr search

### 🎨 Creative & Design
- **`deviantart.py`** - DeviantArt artwork
- **`dribbble.py`** - Dribbble design showcase  
- **`behance.py`** - Adobe Behance portfolios
- **`uxwing.py`** - UXWing icon search

## 🔧 Engine Structure & Implementation

### Standard Engine Interface
Each engine implements:
```python
# Engine metadata
about = {
    "website": "https://example.com",
    "wikidata_id": "Q123456",
    "official_api_documentation": "https://api.example.com/docs",
    "use_official_api": True/False,
    "require_api_key": True/False,
    "results": "HTML|JSON|XML"
}

# Engine configuration
categories = ['general', 'web']  # Search categories
paging = True                    # Pagination support
safesearch = True               # Safe search support
time_range_support = True       # Time range filtering
language_support = True         # Multi-language support

# Core functions
def request(query, params):     # Build search request
def response(resp):             # Parse search results
def fetch_traits():            # Get engine capabilities (optional)
```

### Engine Types
1. **HTML Scraping** - Parse search result pages directly
2. **JSON API** - Use official REST APIs with authentication
3. **XML/RSS** - Process XML feeds and responses  
4. **GraphQL** - Query GraphQL endpoints
5. **Hybrid** - Combine multiple approaches

### Result Processing
- **URL Extraction** - Clean and normalize result URLs
- **Content Processing** - Extract titles, descriptions, metadata
- **Media Handling** - Process images, videos, audio files
- **Deduplication** - Remove duplicate results across engines
- **Ranking** - Score and sort results by relevance

## 🛠️ Engine Development Features

### Configuration Options
- **Timeout Settings** - Request timeout per engine
- **Rate Limiting** - Request frequency controls
- **User-Agent Rotation** - Avoid detection and blocking
- **Proxy Support** - Route requests through proxies
- **SSL/TLS Configuration** - Certificate handling
- **Authentication** - API key and OAuth support

### Error Handling
- **Connection Errors** - Network failure handling
- **Rate Limit Detection** - Backoff and retry logic
- **CAPTCHA Handling** - Bot detection responses  
- **Invalid Response** - Malformed data handling
- **API Quota Management** - Usage limit tracking

### Performance Optimization
- **Parallel Execution** - Concurrent engine requests
- **Connection Pooling** - Reuse HTTP connections
- **Response Caching** - Cache frequent queries
- **Resource Limits** - Memory and CPU constraints

## 📈 Engine Metrics & Monitoring

### Performance Metrics
- **Response Time** - Average query response time
- **Success Rate** - Percentage of successful requests
- **Error Tracking** - Failed request categorization
- **Availability** - Engine uptime monitoring

### Quality Metrics  
- **Result Count** - Number of results returned
- **Relevance Scoring** - Result quality assessment
- **Duplicate Detection** - Cross-engine duplicate rate
- **Content Freshness** - Age of search results

This engines directory represents one of the most comprehensive metasearch implementations available, providing privacy-respecting access to virtually all major search services and specialized databases across the internet.