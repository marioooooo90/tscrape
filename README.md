# Telegram Channel Scraper 📱

A powerful Python script for scraping messages and media from Telegram channels using the Telethon library.

```
___________________  _________
\__    ___/  _____/ /   _____/
  |    | /   \  ___ \_____  \ 
  |    | \    \_\  \/        \
  |____|  \______  /_______  /
                 \/        \/
```

## Table of Contents
1. Features
2. Requirements
3. Installation
4. Configuration
5. Usage
6. Technical Details
7. Troubleshooting
8. Contributing
9. License

## 1. Features 🚀

### Core Functionality
- Multi-channel message scraping with concurrent processing
- Comprehensive media downloading (photos, videos, documents)
- Real-time continuous monitoring with background processing
- Multiple export formats (Excel, JSON, Google Sheets)
- Session persistence and state management
- Progress tracking and logging

### Data Collection
- Message Content
  - Text and formatting
  - Media attachments
  - Reply chains
  - Message IDs
  - Timestamps
- Engagement Data
  - View counts
  - Forward counts
  - Reply counts
  - Reactions
  - Pinned status
- Sender Information
  - User IDs
  - Names
  - Usernames
- Message Entities
  - URLs
  - Mentions
  - Hashtags
  - Formatted text

## 2. Requirements 📋

### System Requirements
- Python 3.7+
- 500MB+ storage space
- 2GB+ RAM recommended
- Stable internet connection

### Dependencies
```
telethon>=1.28.0,<2.0.0
aiohttp>=3.9.0
openpyxl>=3.1.2
Pillow>=10.0.0
google-api-python-client>=2.108.0
google-auth-httplib2>=0.1.1
google-auth-oauthlib>=1.1.0
```

### Required Credentials
1. **Telegram API Credentials**
   - API ID
   - API Hash
   - Phone number
   - Get from: https://my.telegram.org/auth

2. **Google Cloud (Optional, for Sheets export)**
   - Google Cloud Project
   - Enabled APIs:
     - Google Sheets API
     - Google Drive API
   - OAuth 2.0 credentials

## 3. Installation

### Prerequisites
- Python 3.7+
- Telegram account
- API credentials
- (Optional) Google Cloud Project
- 500MB+ free disk space
- Stable internet connection

### Installation
```bash
# Clone repository
git clone https://github.com/unnohwn/telegram-scraper.git
cd telegram-scraper

# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt
```

### Working Directory Structure
```
telegram-scraper/
├── telegram-scraper.py     # Main script
├── requirements.txt        # Dependencies
├── credentials.pkl         # API credentials
├── google_token.pickle    # Google API tokens
├── channels.pkl           # Channel state
└── channel_data/          # Scraped data
    └── channel_name_id/   # Per-channel directory
        ├── media/         # Downloaded media
        ├── exports/       # Export files
        └── channel.db     # SQLite database
```

### Initial Configuration
1. **Telegram API Setup**
   ```python
   # First run configuration
   API_ID = "your_api_id"
   API_HASH = "your_api_hash"
   PHONE = "your_phone_number"
   ```

2. **Working Directory**
   ```python
   # Default: script location
   # Can be modified in script:
   BASE_DIR = os.path.dirname(os.path.abspath(__file__))
   ```

3. **State Management**
   ```python
   # Stored in channels.pkl
   state = {
       'api_id': API_ID,
       'api_hash': API_HASH,
       'phone': PHONE,
       'channels': {},
       'scrape_media': True
   }
   ```

## 4. Usage

The script provides an interactive menu with the following options:

- **[A]** Add new channel
  - Enter the channel ID or channelname
- **[R]** Remove channel
  - Remove a channel from scraping list
- **[S]** Scrape all channels
  - One-time scraping of all configured channels
- **[M]** Toggle media scraping
  - Enable/disable downloading of media files
- **[C]** Continuous scraping
  - Real-time monitoring of channels for new messages
- **[E]** Export data
  - Export to JSON and CSV formats
- **[V]** View saved channels
  - List all saved channels
- **[L]** List account channels
  - List all channels with ID:s for account
- **[Q]** Quit

### Channel IDs 📢

You can use either:
- Channel username (e.g., `channelname`)
- Channel ID (e.g., `-1001234567890`)

## 5. Technical Details

### Media Handling
- Supported formats:
  - Photos (JPEG, PNG, GIF)
  - Videos (MP4, MOV)
  - Documents (PDF, DOC, etc.)
  - Other Telegram-supported formats
- Features:
  - Automatic retry on failed downloads
  - Progress tracking
  - Size optimization
  - Format validation
  - Duplicate detection
  - Organized storage

## 6. Troubleshooting

## 7. Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 8. License

This project is licensed under the MIT License - see the LICENSE file for details.

## 9. Disclaimer

This tool is for educational purposes only. Make sure to:
- Respect Telegram's Terms of Service
- Obtain necessary permissions before scraping
- Use responsibly and ethically
- Comply with data protection regulations
- Follow Google Cloud Platform terms of service

## Enhanced Features in Detail 🔍

### Scraping Options

1. **Full Rescrape [S]**
   - Complete channel history
   - Overwrites existing data
   - Downloads all media

2. **New Messages Only [N]**
   - Scrapes only new content
   - Preserves existing data
   - Efficient updates

3. **Continuous Scraping [C]**
   - Real-time monitoring
   - Background processing
   - Activity logging
   - Can run alongside other functions

### Export Capabilities

1. **Local Export**
   - Excel files with embedded media
   - JSON format for full data
   - Organized folder structure

2. **Google Sheets Export**
   - Direct upload to Google Sheets
   - Embedded images in cells
   - Clickable media links
   - Automatic formatting
   - Public sharing options

### Data Storage Enhancements

Database now includes additional fields:
- Message reactions
- View counts
- Forward counts
- Reply counts
- Post author
- Pinned status
- Formatted message text
- Message entities (links, mentions)

### Media Handling Improvements

- Supports more media types
- Better error recovery
- Progress tracking
- Organized storage structure
- Media reprocessing capability
- Size optimization for exports

## Google Sheets Integration 📊

To use Google Sheets export:

1. **Setup Google Cloud Project**
   - Create project at console.cloud.google.com
   - Enable required APIs:
     - Google Sheets API
     - Google Drive API
   - Create OAuth 2.0 credentials
   - Download client configuration file

2. **First-time Setup**
   - Choose export option [E]
   - Select Google Sheets format
   - Follow authentication prompts
   - Grant necessary permissions

3. **Export Features**
   - Embedded images in cells
   - Clickable links for other media
   - Automatic column sizing
   - Header formatting
   - Public sharing options

## Usage Enhancements 📝

New menu options:
```
[S] Scrape selected channels (full rescrape)
[N] Scrape new messages only
[C] Start continuous scraping
[X] Stop continuous scraping
[E] Export data (Local/Google Sheets)
```

### Continuous Scraping Features

- Runs in background
- Real-time updates
- Activity logging
- Configurable check intervals
- Can be stopped/started anytime
- Shows scraping summary on stop

## Error Handling Improvements 🛠️

- Better retry mechanisms
- Detailed error messages
- Permission handling
- API rate limiting compliance
- Connection error recovery
- Export error handling

## Limitations ⚠️

- Google Sheets image size limits apply
- API rate limits still apply
- Media download size restrictions
- Google Drive storage quota limits

## Data Collection Details 📊

### Message Data
The script collects comprehensive message data including:
- Message text and formatting
- Date and time
- Sender information
- Message IDs and reply chains
- Engagement metrics:
  - View counts
  - Forward counts
  - Reply counts
  - Reactions with counts
- Message type and attributes
- Pinned status
- Post author (for channels)
- Message entities (URLs, mentions, hashtags)

### Media Handling
Supports various media types:
- Photos (with original quality)
- Documents
- Videos
- Other media types supported by Telegram
- Automatic media organization in folders
- Failed download recovery
- Size optimization for exports

## Channel Management 📱

### Adding Channels
Two methods available:
1. **Direct Channel ID [A]**
   - Enter channel ID or username
   - Automatic validation
   - Folder name generation

2. **List and Add [L]**
   - Shows all accessible channels
   - Multiple selection support
   - Bulk channel addition

### Channel Operations
- **View Channels [V]**
  - List all saved channels
  - Show last message IDs
  - Display folder names

- **Remove Channels [R]**
  - Single or multiple selection
  - 'Remove all' option
  - Safe deletion with confirmation

## Scraping Modes 🔄

### 1. Full Scrape [S]
- Complete channel history
- Resets existing data
- Full media download
- Progress tracking
- Database recreation

### 2. New Messages [N]
- Incremental updates
- Checks from last saved message
- Efficient for regular updates
- Maintains existing data

### 3. Continuous Scraping [C]
- Real-time monitoring
- 60-second check intervals
- Background operation
- Activity logging
- Summary on completion:
  - Duration
  - Messages processed
  - Channels checked
  - Last 10 activities

## Export System 📤

### Local Export
1. **Excel Export**
   - Embedded media thumbnails
   - Interactive image viewing
   - Column auto-sizing
   - Formatted headers
   - Cell value optimization

2. **JSON Export**
   - Complete data structure
   - Formatted output
   - Parsed entities
   - Timestamp preservation

### Google Sheets Export
1. **Setup Process**
   - OAuth 2.0 authentication
   - API enablement guidance
   - Credential management
   - Permission handling

2. **Features**
   - Embedded images
   - Media preview links
   - Automatic formatting
   - Column optimization
   - Public access settings

3. **Organization**
   - Timestamped files
   - Dedicated media folders
   - Structured data layout
   - Automatic file naming

## File Organization 📁

```
channel_name_channelid/
├── media/
│   └── [downloaded media files]
├── exports/
│   ├── channelid_YYYYMMDD_HHMMSS.xlsx
│   ├── channelid_YYYYMMDD_HHMMSS.json
│   └── README.txt
└── channelid.db
```

## Database Structure 💾

SQLite database with enhanced schema:
```sql
CREATE TABLE messages (
    id INTEGER PRIMARY KEY,
    message_id INTEGER,
    date TEXT,
    sender_id INTEGER,
    first_name TEXT,
    last_name TEXT,
    username TEXT,
    message TEXT,
    formatted_message TEXT,
    entities TEXT,
    media_type TEXT,
    media_path TEXT,
    reply_to INTEGER,
    views INTEGER,
    forwards INTEGER,
    replies INTEGER,
    reactions TEXT,
    post_author TEXT,
    is_pinned INTEGER
)
```

## Session Management 🔐

- Credential storage
- Session persistence
- Multi-account support
- Secure token handling
- Logout functionality [O]
- Session recovery

## Error Handling 🛠️

- API rate limit management
- Media download retry system
- Connection error recovery
- Export error handling
- Permission issue resolution
- Session error management

## Performance Optimizations ⚡

- Asynchronous operations
- Batch processing
- Progress tracking
- Memory management
- Database optimization
- Media handling efficiency
