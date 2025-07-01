
# RedPhish: Professional Security Toolkit

![RedPhish Banner](<a href="https://ibb.co/993s2gpW"><img src="https://i.ibb.co/bgRzLm6X/diagram-1.png" alt="diagram-1" border="0"></a>)

RedPhish is an advanced, modular framework designed for penetration testers and security researchers. It streamlines website cloning, credential harvesting, and secure public exposure through industry-standard tunneling services.

## Key Features

- 🕸️ **Website Cloning**: Automated resource downloading for accurate site replication.  
- 🎣 **Credential Harvesting**: Real-time dashboard to monitor and collect user credentials.  
- 🌐 **Secure Tunneling**: Integrations with Cloudflared, Ngrok, and LocalTunnel for public exposure.  
- 🎨 **User-Friendly Interface**: Color-coded, professional terminal output.  
- 📦 **Modular Architecture**: Easily extend functionality with custom modules.

## Table of Contents

1. [Installation](#installation)  
2. [Usage](#usage)  
3. [Configuration](#configuration)  
4. [Project Structure](#project-structure)  
5. [Contributing](#contributing)  
6. [License](#license)  

## Installation

### System Requirements

- Python 3.8 or higher  
- `pip` package manager  
- Terminal with ANSI color support  
- At least 100MB of free disk space  

### Clone the Repository

```bash
git clone https://github.com/zerosocialcode/RedPhish.git
cd RedPhish
```

### Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Install Tunneling Tools (Recommended)

#### Cloudflared
```bash
curl -L https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-arm -o cloudflared
chmod +x cloudflared
sudo mv cloudflared /usr/local/bin/
```

#### Ngrok (Alternative)
```bash
curl -L https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-arm.zip -o ngrok.zip
unzip ngrok.zip
chmod +x ngrok
sudo mv ngrok /usr/local/bin/
```

### Platform-Specific Notes

#### Termux (Android)
```bash
pkg update && pkg install python git wget
pip install --upgrade pip
pip install -r requirements.txt
```

#### Windows (Command Prompt)
1. Install Python from [python.org](https://python.org)  
2. Install Git from [git-scm.com](https://git-scm.com)  
3. Run:
   ```cmd
   git clone https://github.com/zerosocialcode/RedPhish.git
   cd RedPhish
   pip install -r requirements.txt
   ```

### Verify Installation

```bash
./RedPhish.sh
```

---

## Usage

Launch the toolkit:
```bash
./RedPhish.sh
```

### Main Menu

```
Professional Security Toolkit
Developer: zerosocialcode

1. Website Cloner
2. Credential Harvester
0. Exit
```

### 1. Website Cloning

1. Choose **Website Cloner**.  
2. Enter the target URL (e.g., `https://example.com`).  
3. Specify a site name (e.g., `ExampleSite`).  
4. The cloned site will be saved under `data/cloned_sites/ExampleSite`.

### 2. Credential Harvesting

1. Choose **Credential Harvester**.  
2. Select a cloned site.  
3. Pick an exposure method:  
   - Cloudflared  
   - Ngrok  
   - LocalTunnel  
   - Localhost  
4. Monitor incoming credentials via the dashboard.

```text
=== CREDENTIAL HARVESTER ===
Site: Facebook
Local URL: http://0.0.0.0:8080
Landing URL: https://secure-tunnel.trycloudflare.com
Waiting for credentials...
Press Ctrl+C to stop.
```

Captured credentials are stored in:
```
data/credentials/[SITE_NAME]/credentials.json
```

---

## Configuration

Edit the JSON files under `configuration/`:

- **Cloner settings**: `configuration/cloner/config.json`  
- **Harvester settings**: `configuration/harvester/config.json`

Example `configuration/cloner/config.json`:
```json
{
  "user_agent": "Mozilla/5.0 (Custom User Agent)",
  "ssl_verify": false,
  "depth": 2
}
```

---

## Project Structure

```
RedPhish/
├── RedPhish.sh              # Main launcher script
├── configuration/
│   ├── cloner/config.json
│   └── harvester/config.json
├── data/
│   ├── cloned_sites/
│   └── credentials/
├── modules/
│   ├── cloner/
│   ├── exposers/
│   └── harvester/
├── docs/
│   ├── INSTALL.md
│   └── USAGE.md
└── gateway.py               # Application entry point
```

---

## Contributing

We welcome contributions! To add new features or fix issues:

1. Fork the repo  
2. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature
   ```
3. Commit your changes:
   ```bash
   git commit -am "Add your feature"
   ```
4. Push to your branch:
   ```bash
   git push origin feature/your-feature
   ```
5. Open a Pull Request.

---

## License

Released under the MIT License. See [LICENSE](LICENSE) for details.

> **Disclaimer**: For educational and authorized penetration testing only. The authors are not liable for misuse.
