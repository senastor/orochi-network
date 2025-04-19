# Orochi-Network Node Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Ubuntu Version](https://img.shields.io/badge/Ubuntu-22.04-LTS-blue.svg)](https://releases.ubuntu.com/22.04/)

> **A step-by-step guide to deploy and manage an Orochi-Network node on Ubuntu 22.04 LTS with GUI and remote desktop access.**

---

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [1. System Update](#1-system-update)
  - [2. GNOME Desktop & Display Manager](#2-gnome-desktop--display-manager)
  - [3. xRDP Setup](#3-xrdp-setup)
  - [4. User Creation](#4-user-creation)
- [Configuration](#configuration)
  - [Disable Screen Blanking](#disable-screen-blanking)
- [Usage](#usage)
- [Screenshots](#screenshots)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## Overview
This repository provides all necessary instructions to configure an Ubuntu server with a GNOME desktop environment and xRDP, enabling you to connect via Remote Desktop and run an Orochi-Network node.

---

## Prerequisites

- **OS:** Ubuntu 22.04 LTS (Server)
- **CPU:** 4 cores (8 cores recommended)
- **RAM:** 8 GB (16 GB recommended)
- **Storage:** 100 GB SSD (250 GB SSD recommended)
- **Network:** Public IP address or port forwarding to port `9944`

---

## Installation

### 1. System Update

```bash
sudo apt update && sudo apt upgrade -y
```

### 2. GNOME Desktop & Display Manager

1. Install the GNOME desktop environment:
   ```bash
   sudo apt install ubuntu-gnome-desktop -y
   ```
2. Install core GNOME packages:
   ```bash
   sudo apt install gnome-core -y
   ```
3. When prompted, select **gdm3** as your display manager.
4. Reboot the server:
   ```bash
   sudo reboot
   ```

### 3. xRDP Setup

```bash
sudo apt install xrdp -y
sudo systemctl enable xrdp
sudo systemctl start xrdp
```

### 4. User Creation

Create a non-root user to handle your remote sessions:

```bash
sudo adduser <your-username>
```

Follow the prompts to set a password and accept defaults.

---

## Configuration

### Disable Screen Blanking

1. Connect via xRDP to your GNOME session.
2. On the GNOME desktop, open **Settings** → **Power**.
3. Set **Blank screen** to **Never**.

---

## Usage

1. From your local machine, launch **Remote Desktop Connection** (Windows) or your preferred RDP client.
2. Enter your server’s IP and the user credentials you created.
3. Once connected, open **Google Chrome** (or any browser) on the server.
4. Navigate to your Orochi-Network node dashboard or use the CLI to start syncing:

   ```bash
   orochi-node start --chain=mainnet
   ```

5. Monitor logs:

   ```bash
   journalctl -u orochi-node -f
   ```

---

## Screenshots

| Description                             | File                                 |
|-----------------------------------------|--------------------------------------|
| xRDP login prompt                       | `screenshots/2025-04-19_015101.png`  |
| Remote session security warning         | `screenshots/2025-04-19_015228.png`  |
| GNOME Power settings: disable blanking  | `screenshots/2025-04-19_020236.png`  |

---

## Troubleshooting

- **Cannot connect via RDP**: Ensure port `3389` is open in your firewall.
- **Black screen after login**: Confirm `gdm3` is selected and the GNOME session is installed.
- **Node fails to sync**: Verify your network port `9944` is forwarded and reachable.

---

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to fork the repository and submit a pull request.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

<p align="center">_Happy nodding on the Orochi-Network!_</p>
