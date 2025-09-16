# 🤖 Telegram Group Creation Bot

A sophisticated automation bot for bulk Telegram group creation and management. This professional-grade tool enables authorized users to manage multiple Telegram accounts and create groups at scale with advanced security features and real-time monitoring.

## 🌟 Overview

This bot is designed for users who need to create multiple Telegram groups efficiently. It supports multi-account operations, provides secure session management, and offers a comprehensive admin panel for managing the entire process. Perfect for community managers, marketers, and developers who need to scale their Telegram presence.

## ✨ Key Highlights

- 🔐 **Enterprise Security**: Role-based access control with owner/admin permissions
- 🚀 **High Performance**: Parallel processing across multiple accounts
- 📊 **Advanced Analytics**: Comprehensive statistics and progress tracking
- 🛡️ **Account Safety**: Built-in flood protection and safety delays
- 💾 **Reliable Backup**: Automatic session backups and recovery
- 🎯 **User-Friendly**: Intuitive interface with real-time updates

## 🚀 Features

### Core Functionality
- **Multi-Account Support**: Login and manage multiple Telegram accounts
- **Bulk Group Creation**: Create multiple groups simultaneously across accounts
- **Automated Messaging**: Send predefined messages to created groups
- **Session Management**: Secure storage and validation of Telegram sessions
- **Progress Tracking**: Real-time progress updates during group creation
- **Link Generation**: Automatic invite link generation for all created groups

### Security & Access Control
- **Role-Based Access**: Owner and Admin roles with different permissions
- **Authorized Users Only**: Restricted access to prevent unauthorized usage
- **Session Backup**: Automatic backup of session files for recovery
- **Admin Management**: Owner can add/remove admins dynamically

### Account Management
- **Manual Login**: Phone number + OTP verification
- **ZIP File Import**: Bulk account import from ZIP files
- **Session Validation**: Health checks for all stored sessions
- **Account Statistics**: Detailed statistics for each account
- **Multi-Selection**: Choose specific accounts for group creation

## 📋 Requirements

### System Requirements
- Python 3.8 or higher
- Windows/Linux/macOS support
- Stable internet connection
- Telegram API credentials

### Dependencies
```bash
pip install python-telegram-bot==20.7
pip install telethon==1.34.0
pip install asyncio
```

### Hardware Recommendations
- **RAM**: Minimum 2GB (4GB+ recommended for multiple accounts)
- **Storage**: 1GB free space for sessions and logs
- **CPU**: Multi-core processor for parallel processing

### Configuration Files
- `bot_config.json` - Bot token and user permissions
- Session files stored in `sessions/` directory
- Account statistics in `*_stats.json` files
- Group links in `*_links.txt` files

## ⚙️ Configuration

### Bot Configuration (`bot_config.json`)
```json
{
    "BOT_TOKEN": "YOUR_BOT_TOKEN_HERE",
    "OWNER_IDS": [123456789],
    "ADMIN_IDS": [987654321]
}
```

### API Configuration
- **API_ID**: `22566208` (Built-in)
- **API_HASH**: `fa18dcf886c0d78f20e849f54be62940` (Built-in)
- **Fixed Settings**:
  - Delay between groups: 20 seconds
  - Messages per group: 10
  - Promotional messages: Pre-configured (@OldGcHub branding)

### Environment Setup
```bash
# Clone or download the bot files
# Install dependencies
pip install -r requirements.txt

# Configure bot token
# Edit bot_config.json with your bot token and admin IDs

# Run the bot
python telegram_bot.py
```

## 🎯 How It Works

### 1. Authentication & Authorization
- Bot checks user ID against OWNER_IDS and ADMIN_IDS
- Only authorized users can access bot features
- Owners have full access including admin management
- Admins can use all group creation features

### 2. Account Login Process
#### Manual Login:
1. User provides phone number
2. Bot sends OTP via Telegram API
3. User enters verification code
4. If 2FA enabled, user provides password
5. Session file created and stored securely

#### ZIP File Import:
1. User uploads ZIP containing session files and JSON configs
2. Bot extracts and validates each account
3. Sessions tested for authorization
4. Valid accounts added to user's account pool

### 3. Group Creation Workflow
1. **Account Selection**: Choose from available accounts
2. **Group Count**: Specify number of groups per account
3. **Safety Delay**: 20-second initialization delay
4. **Parallel Processing**: Multiple accounts work simultaneously
5. **Group Creation**: Each account creates specified number of groups
6. **Message Sending**: Predefined messages sent to each group
7. **Link Generation**: Invite links created and saved
8. **Progress Updates**: Real-time status updates with cancel option

### 4. Session Management
- Sessions stored in user-specific directories: `sessions/{user_id}/`
- Automatic backup creation in `sessions/{user_id}/backups/`
- Session validation before each use
- Invalid sessions automatically removed
- Recovery from backups when possible

### 5. Statistics & Tracking
- **Account Statistics**: Groups created, links generated, last activity
- **Links Files**: All group invite links saved per account
- **JSON Stats**: Detailed statistics in structured format
- **Real-time Updates**: Statistics updated after each group creation

## 🤖 Bot Commands & Interface

### Primary Commands
- `/start` - 🏠 Main menu with all options and features

### Interactive Menu Options
1. **🔐 Login Your Accounts**
   - Manual login with phone + OTP
   - ZIP file bulk import
   - Session validation and backup

2. **🚀 Start Group Creation**
   - Multi-account selection
   - Bulk group creation
   - Real-time progress tracking

3. **📊 Bot Statistics**
   - Account counts and status
   - Performance metrics
   - System information

4. **ℹ️ Help & Features**
   - Comprehensive feature guide
   - Usage instructions
   - Safety guidelines

5. **⚙️ Admin Management** (Owner Only)
   - Add/remove admins
   - Permission management
   - User access control

## 📱 User Interface

### Main Menu Options
1. **🔐 Login Your Accounts** - Add new accounts or manage existing
2. **🚀 Start Group Creation** - Begin group creation process
3. **📊 Bot Statistics** - View usage statistics
4. **ℹ️ Help & Features** - Access help information
5. **⚙️ Admin Management** (Owner only) - Manage admins

### Group Creation Flow
1. **Account Selection** - Multi-select interface for choosing accounts
2. **Group Count Input** - Specify groups per account
3. **Progress Tracking** - Real-time progress with cancel option
4. **Results Display** - Summary with download links

## 🔧 Technical Implementation

### Core Components

#### `telegram_bot.py` - Main Bot Logic
- Bot initialization and command handlers
- User authentication and authorization
- Conversation flow management
- Session validation and backup
- Progress tracking and updates

#### `BigBotFinal.py` - Group Creation Engine
- Telegram client management
- Group creation with random titles
- Message sending with delays
- Statistics tracking and file management
- Error handling and flood protection

### Key Features Implementation

#### Multi-Account Processing
```python
# Parallel processing across multiple accounts
for account in selected_accounts:
    threading.Thread(
        target=lambda: asyncio.run(
            run_group_creation_process(account, count, ...)
        ), 
        daemon=True
    ).start()
```

#### Session Security
- User-specific session directories
- Automatic backup creation
- Session validation before use
- Secure file permissions

#### Progress Tracking
- Queue-based progress updates
- Real-time UI updates
- Cancellation support
- Partial results on interruption

## 📊 File Structure

```
Nexogrp/
├── telegram_bot.py          # Main bot logic
├── BigBotFinal.py          # Group creation engine
├── bot_config.json         # Bot configuration
├── sessions/               # Session storage
│   ├── {user_id}/         # User-specific sessions
│   │   ├── backups/       # Session backups
│   │   └── *.session      # Session files
├── *_stats.json           # Account statistics
└── *_links.txt           # Group invite links
```

## 🛡️ Security Features

### Access Control
- Whitelist-based user authorization
- Role-based permission system
- Admin management by owner only
- Session isolation per user

### Session Protection
- Encrypted session storage
- Automatic backup creation
- Session validation checks
- Invalid session cleanup

### Rate Limiting & Safety
- Configurable delays between operations
- Flood protection handling
- Random delays to avoid detection
- Safety delays after login

## 🚨 Safety Measures

### Account Protection
- 20-second delay after login
- Random delays between group creation
- Safety delays every 5 groups
- Flood wait error handling

### Pattern Avoidance
- Random group titles generation
- Variable message sending delays
- Randomized operation timing
- Natural-looking activity patterns

## 📈 Statistics & Monitoring

### Account Statistics
- Total groups created (all time)
- Groups created today
- Total links in file
- Last activity timestamp
- Account information

### Bot Statistics
- Total admins count
- Logged accounts count
- Active processes count
- Configuration settings

## 🔄 Process Flow

### Login Process
```
User Input → Phone Validation → OTP Request → Code Verification → 2FA (if needed) → Session Creation → Backup → Success
```

### Group Creation Process
```
Account Selection → Count Input → Safety Delay → Parallel Processing → Group Creation → Message Sending → Link Generation → Statistics Update → Results Display
```

## 💡 Usage Tips

1. **Account Safety**: Wait 2-3 minutes between login and group creation
2. **Batch Processing**: Use multiple accounts for faster group creation
3. **Regular Backups**: Session backups are created automatically
4. **Health Checks**: Use `/health` command to verify session status
5. **Statistics Monitoring**: Track account performance with `/accountstats`

## 🛠️ Maintenance

### Regular Tasks
- Monitor session health
- Clean up invalid sessions
- Review account statistics
- Update admin permissions
- Backup important data

### Troubleshooting
- Check session validity with `/health`
- Review error logs for issues
- Restore from backups if needed
- Re-login accounts with expired sessions

## 🎯 Getting Started

### Quick Setup Guide
1. **Get Bot Access**: Contact @OldGcHub for authorization
2. **Install Dependencies**: Run `pip install -r requirements.txt`
3. **Configure Bot**: Edit `bot_config.json` with your bot token
4. **Add Admin**: Owner adds your user ID to admin list
5. **Start Bot**: Run `python telegram_bot.py`
6. **Login Accounts**: Use `/start` → "🔐 Login Your Accounts"
7. **Create Groups**: Use "🚀 Start Group Creation" option

### First-Time Usage
1. Send `/start` to the bot
2. Choose "🔐 Login Your Accounts"
3. Select login method (Manual or ZIP)
4. Complete authentication process
5. Wait 2-3 minutes for safety
6. Start creating groups!

## 🔧 Advanced Configuration

### Custom Message Templates
Edit the `FIXED_MESSAGES` array in `telegram_bot.py` to customize promotional messages:
```python
FIXED_MESSAGES = [
    "💻 Your custom message here",
    "🖥️ Another promotional message",
    # Add more messages...
]
```

### Safety Settings
Adjust timing and safety parameters:
```python
FIXED_DELAY = 20  # Seconds between groups
FIXED_MESSAGES_PER_GROUP = 10  # Messages per group
```

## 📞 Support & Contact

### Getting Access
- **Developer**: [@OldGcHub](https://t.me/OldGcHub)
- **Bot Authorization**: Contact owner for admin access
- **Technical Support**: Available for authorized users

### Community
- **Updates Channel**: [@NexoUnion](https://t.me/NexoUnion)
- **Support Group**: Contact @OldGcHub for invite

## ⚠️ Important Disclaimers

### Usage Guidelines
- This bot is for **authorized users only**
- Follow Telegram's Terms of Service
- Use responsibly and ethically
- Respect rate limits and safety delays
- Keep your sessions secure and private

### Account Safety
- Always wait 2-3 minutes after login before creating groups
- Don't exceed recommended group creation limits
- Monitor your accounts for any unusual activity
- Keep session backups in a secure location

### Legal Notice
This tool is provided for legitimate use cases only. Users are responsible for complying with all applicable laws and Telegram's terms of service. The developer is not responsible for misuse of this software.

---

**© 2024 Nexo Group Creation Bot | Developed by @OldGcHub**
