# ProxMorph

A focused dark theme for Proxmox VE, based on the native Proxmox Dark theme with an AMOLED-black canvas and readable layered surfaces.

## Features

- **Proxmox Amoled** theme with a true-black background
- Preserves Proxmox Dark controls, typography, colors, and layout
- Native Color Theme selector integration
- Automatic re-application after Proxmox updates
- Optional hardware sensor monitoring on PVE node summaries

## Installation

### Manual installation

~~~bash
git clone https://github.com/SoloSaravanan/proxmorph.git
cd proxmorph
chmod +x install.sh
sudo ./install.sh install
~~~

Set Proxmox Amoled as the default theme:

~~~bash
sudo ./install.sh default-theme proxmox-amoled
sudo systemctl restart pveproxy
~~~

After installation, hard-refresh the browser with Ctrl+Shift+R.

## Commands

| Command | Description |
|---|---|
| sudo ./install.sh install | Install Proxmorph |
| sudo ./install.sh uninstall | Remove Proxmorph and restore backups |
| sudo ./install.sh update | Update from GitHub and reinstall |
| sudo ./install.sh status | Show installation status |
| sudo ./install.sh default-theme proxmox-amoled | Set the default theme |
| sudo ./install.sh default-theme none | Remove the server-side default |
| sudo ./install.sh | Open the interactive menu |

## What the installer changes

The installer:

- Copies the AMOLED theme into Proxmox's widget toolkit theme directory.
- Registers it in Proxmox's native Color Theme selector.
- Patches the product index to load the selected theme.
- Installs an update hook so the theme is restored after Proxmox upgrades.
- Creates backups before modifying system files.

To undo the changes:

~~~bash
sudo ./install.sh uninstall
~~~

## Troubleshooting

If the theme does not appear:

~~~bash
sudo ./install.sh status
sudo systemctl restart pveproxy
~~~

Then clear the browser cache or use a private/incognito window.

If the web interface is unavailable after an installation:

~~~bash
sudo systemctl status pveproxy --no-pager
sudo journalctl -u pveproxy -n 100 --no-pager
~~~

## Supported products

- Proxmox VE
- Proxmox Backup Server
- Proxmox Datacenter Manager

## License

MIT
