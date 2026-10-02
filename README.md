# IPSW URL Installer

A GitHub Pages + GitHub Codespaces-ready web app example for organizing and opening **IPSW firmware URLs**.

## Features

- 🔗 Add IPSW download URLs
- 📱 Store device and iOS version information
- 🔎 Search firmware entries
- 📋 Copy IPSW URLs
- 🌐 Open IPSW URLs in a new browser tab
- 💾 Import and export firmware data as JSON
- 🗑️ Remove saved entries
- 📱 Responsive interface for desktop, iPhone, and iPad
- 🚀 Designed for GitHub Pages
- ☁️ Ready for GitHub Codespaces development

## Project Structure

```text
ipsw-url-installer/
│
├── index.html
├── styles.css
├── script.js
├── ipsw.json
│
├── README.md
├── LICENSE
├── .gitignore
│
└── .devcontainer/
    └── devcontainer.json
```

## Example IPSW Entry

```json
{
  "device": "iPhone 1,1",
  "model": "M68AP",
  "iOSVersion": "3.0",
  "build": "7A341",
  "filename": "iPhone1,1_3.0_7A341_Restore.ipsw",
  "url": "https://example.com/firmware/iPhone1,1_3.0_7A341_Restore.ipsw"
}
```

> Replace example URLs with firmware URLs that you are authorized to distribute or access.

## How It Works

The web app treats an IPSW URL as a web resource:

1. Enter the device name.
2. Enter the iOS version.
3. Enter the build number.
4. Enter the IPSW filename.
5. Paste the IPSW URL.
6. Select **Add IPSW**.
7. Use **Open URL** to navigate to the firmware URL or **Copy URL** to copy it.

The web app does **not** install firmware directly onto an iPhone or iPad. Actual IPSW installation requires Apple's supported device-management/restore mechanisms.

## GitHub Pages

### 1. Create a repository

Create a GitHub repository named:

```text
ipsw-url-installer
```

### 2. Upload the project

Upload:

```text
index.html
styles.css
script.js
ipsw.json
README.md
LICENSE
.gitignore
.devcontainer/devcontainer.json
```

### 3. Enable GitHub Pages

Open:

```text
Repository
→ Settings
→ Pages
```

Select:

```text
Source: Deploy from a branch
Branch: main
Folder: / (root)
```

Save the settings.

Your site will be available at a URL similar to:

```text
https://YOUR-USERNAME.github.io/ipsw-url-installer/
```

## GitHub Codespaces

Open the repository and select:

```text
Code
→ Codespaces
→ Create codespace on main
```

The included `.devcontainer/devcontainer.json` can provide a consistent development environment.

A simple local server can be started with:

```bash
python3 -m http.server 8080
```

Then open the forwarded port in Codespaces.

## JSON Data Format

The `ipsw.json` file can contain multiple firmware records:

```json
[
  {
    "device": "iPhone 1,1",
    "model": "M68AP",
    "iOSVersion": "3.0",
    "build": "7A341",
    "filename": "iPhone1,1_3.0_7A341_Restore.ipsw",
    "url": "https://example.com/firmware/iPhone1,1_3.0_7A341_Restore.ipsw"
  },
  {
    "device": "iPad 1,1",
    "model": "K48AP",
    "iOSVersion": "3.2",
    "build": "7B367",
    "filename": "iPad1,1_3.2_7B367_Restore.ipsw",
    "url": "https://example.com/firmware/iPad1,1_3.2_7B367_Restore.ipsw"
  }
]
```

## URL Validation

The application should validate that a submitted address uses HTTPS:

```javascript
function isValidIPSWUrl(value) {
  try {
    const url = new URL(value);
    return url.protocol === "https:";
  } catch {
    return false;
  }
}
```

## Security Notes

This project is a URL-management interface. It should not attempt to bypass device security, activation locks, signing requirements, or Apple's firmware verification mechanisms.

For production use:

- Prefer HTTPS URLs.
- Validate user-provided URLs.
- Avoid executing downloaded files in the browser.
- Do not automatically download or execute unknown firmware files.
- Do not claim that an arbitrary IPSW is installable on a particular device.
- Use firmware sources you are authorized to access and distribute.

## Example Interface

```text
┌──────────────────────────────────────────────┐
│              IPSW URL Installer              │
├──────────────────────────────────────────────┤
│                                              │
│ Device                                        │
│ [ iPhone 1,1                              ]  │
│                                              │
│ iOS Version                                   │
│ [ 3.0                                     ]  │
│                                              │
│ Build                                         │
│ [ 7A341                                   ]  │
│                                              │
│ IPSW Filename                                 │
│ [ iPhone1,1_3.0_7A341_Restore.ipsw        ]  │
│                                              │
│ IPSW URL                                      │
│ [ https://example.com/...                  ]  │
│                                              │
│              [ Add IPSW ]                     │
│                                              │
├──────────────────────────────────────────────┤
│ iPhone 1,1 — iOS 3.0                         │
│ iPhone1,1_3.0_7A341_Restore.ipsw             │
│                                              │
│ [ Open URL ] [ Copy URL ] [ Remove ]         │
└──────────────────────────────────────────────┘
```

## Development

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/ipsw-url-installer.git
cd ipsw-url-installer
```

Start a local server:

```bash
python3 -m http.server 8080
```

Open:

```text
http://localhost:8080
```

## License

Add your preferred open-source license to `LICENSE`.

Example:

```text
MIT License
```

## Disclaimer

This is an educational web-app example for managing IPSW URLs and firmware metadata. It is not an Apple-authorized firmware installer and does not perform iOS device restoration or firmware-signing operations.