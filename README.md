```markdown
# RedPhish: Professional Security Toolkit

![RedPhish Banner](https://i.imgur.com/redphish-banner.png)

RedPhish is an advanced security toolkit designed for penetration testers and security researchers. It provides a modular framework for website cloning and credential harvesting with secure tunneling capabilities.

**Key Features**:
- 🕸️ Website cloning with automatic resource downloading
- 🎣 Credential harvesting with real-time dashboard
- 🌐 Public exposure via secure tunnels (Cloudflared, Ngrok, LocalTunnel)
- 🎨 Professional terminal interface with color-coded output
- 📦 Modular architecture for easy expansion

```terminal
 ____          _ ____  _     _     _
|  _ \ ___  __| |  _ \| |__ (_)___| |__
| |_) / _ \/ _` | |_) | '_ \| / __| '_ \
|  _ <  __/ (_| |  __/| | | | \__ \ | | |
|_| \_\___|\__,_|_|   |_| |_|_|___/_| |_|
```

## Table of Contents
1. [Installation](/docs/INSTALL.md)
2. [Usage Guide](/docs/USAGE.md)
3. [Project Structure](#project-structure)
4. [Contributing](#contributing)
5. [License](#license)

## Project Structure
```
RedPhish/
├── RedPhish.sh              # Main launcher script
├── configuration/           # Configuration files
│   ├── cloner/
│   │   └── config.json      # Cloner configuration
│   └── harvester/
│       └── config.json      # Harvester configuration
├── data/                    # Data storage
│   ├── cloned_sites/        # Cloned websites
│   └── credentials/         # Captured credentials
├── modules/                 # Functional modules
│   ├── cloner/              # Website cloning
│   ├── exposers/            # Tunnel services
│   └── harvester/           # Credential harvesting
├── docs/                    # Documentation
│   ├── README.md
│   ├── INSTALL.md
│   └── USAGE.md
└── gateway.py               # Main application gateway
```

## Contributing
We welcome contributions! Please follow these steps:
1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -am 'Add new feature'`
4. Push to branch: `git push origin feature/your-feature`
5. Submit a pull request

## License
RedPhish is released under the MIT License. See [LICENSE](LICENSE) for details.

> **Disclaimer**: This tool is for educational and authorized penetration testing purposes only. The developers assume no liability for any misuse of this software.
```

### 2. `docs/INSTALL.md` (Installation Guide)
```markdown
# RedPhish Installation Guide

## System Requirements
- Python 3.8+
- pip package manager
- Terminal with color support
- 100MB disk space

## Installation Steps

### 1. Clone Repository
```bash
git clone https://github.com/zerosocialcode/RedPhish.git
cd RedPhish
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Install External Tools (Recommended)
```bash
# Cloudflared (Required for tunneling)
curl -L https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm -o cloudflared
chmod +x cloudflared
mv cloudflared /usr/local/bin/

# Ngrok (Alternative tunneling)
curl -L https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-arm.zip -o ngrok.zip
unzip ngrok.zip
mv ngrok /usr/local/bin/
```

### 4. Verify Installation
```bash
./RedPhish.sh
```

### Platform-Specific Notes

#### Termux (Android)
```bash
pkg update
pkg install python git wget
python -m pip install --upgrade pip
pip install -r requirements.txt
```

#### Windows
1. Install Python from [python.org](https://python.org)
2. Install Git from [git-scm.com](https://git-scm.com)
3. Run in Command Prompt:
```cmd
git clone https://github.com/zerosocialcode/RedPhish.git
cd RedPhish
pip install -r requirements.txt
```

### Configuration
Edit configuration files in `configuration/` directory:
- `cloner/config.json`: Website cloning settings
- `harvester/config.json`: Server and harvesting settings

## First Run
After installation, launch RedPhish:
```bash
./RedPhish.sh
```

You should see the main menu with available modules.
```

### 3. `docs/USAGE.md` (Usage Guide)
```markdown
# RedPhish Usage Guide

## Launching the Toolkit
```bash
./RedPhish.sh
```

## Main Menu
```
 ____          _ ____  _     _     _
|  _ \ ___  __| |  _ \| |__ (_)___| |__
| |_) / _ \/ _` | |_) | '_ \| / __| '_ \
|  _ <  __/ (_| |  __/| | | | \__ \ | | |
|_| \_\___|\__,_|_|   |_| |_|_|___/_| |_|

Professional Security Toolkit
developer: zerosocialcode

Available Modules:
  1. Website Cloner
  2. Credential Harvester
  0. Exit
```

## Website Cloning Module
1. Select "Website Cloner" from main menu
2. Enter target URL (e.g., `https://example.com`)
3. Enter site name (e.g., `ExampleSite`)
4. The site will be cloned to `data/cloned_sites/ExampleSite`

## Credential Harvester Module
1. Select "Credential Harvester" from main menu
2. Choose a cloned site from the list
3. Select exposure method:
   - Cloudflared (Recommended)
   - Ngrok
   - LocalTunnel
   - Localhost only
4. The dashboard will appear with:
   - Local URL
   - Public Landing URL (if using tunnel)
   - Credential capture status

## Dashboard Interface
```
=== CREDENTIAL HARVESTER ===
Site: Facebook
Local URL: http://0.0.0.0:8080

🌐 Landing URL: https://secure-tunnel.trycloudflare.com
Share this URL with your target

👀 Waiting for credentials...

Press Ctrl+C to stop
```

## Captured Credentials
- Credentials are saved to `data/credentials/[SITE_NAME]/credentials.json`
- Format:
```json
[
  {
    "timestamp": "2025-07-01 12:34:56",
    "data": {
      "username": "testuser",
      "password": "test123"
    }
  }
]
```

## Keyboard Shortcuts
- `Ctrl+C` - Exit current module
- `0` - Exit from main menu
- `Enter` - Confirm selections

## Advanced Usage

### Custom Cloning Configuration
Edit `configuration/cloner/config.json`:
```json
{
  "user_agent": "Mozilla/5.0 (Custom User Agent)",
  "ssl_verify": false,
  "depth": 2
}
```

### Custom Server Configuration
Edit `configuration/harvester/config.json`:
```json
{
  "port": 9090,
  "host": "127.0.0.1",
  "injection_script": "custom.js"
}
```

### Creating New Modules
1. Create a new directory in `modules/`
2. Add `main.py` with your module logic
3. Update `configuration/modules.json`:
```json
{
  "modules": [
    ...,
    {
      "id": "new_module",
      "name": "New Module"
    }
  ]
}
```

## Troubleshooting
- **Cloning fails**: Check internet connection and target URL accessibility
- **Tunnel not working**: Verify cloudflared/ngrok installation
- **No modules shown**: Check `configuration/modules.json` format
```
