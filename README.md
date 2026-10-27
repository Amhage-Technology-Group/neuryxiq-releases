<p align="center">
  <img src="https://github.com/Amhage-Technology-Group.png" width="128" alt="NeuryxIQ">
</p>
<h1 align="center">NeuryxIQ</h1>
<p align="center"><b>The Autonomous Security Platform.</b><br>
Powered by AI superintelligence. Answers, not alerts.<br>
Security operations and HIPAA posture for small medical and dental practices, on your own hardware.</p>

<p align="center">
  <a href="https://github.com/Amhage-Technology-Group/neuryxiq-releases/releases/latest/download/NeuryxIQ-Setup.exe"><img src="https://img.shields.io/badge/Download-NeuryxIQ--Setup.exe-2b6cff?style=for-the-badge&logo=windows&logoColor=white" alt="Download for Windows"></a>
</p>
<p align="center">
  <a href="https://github.com/Amhage-Technology-Group/neuryxiq-releases/releases/latest"><img src="https://img.shields.io/github/v/release/Amhage-Technology-Group/neuryxiq-releases?label=latest&color=2b6cff" alt="Latest release"></a>
  <img src="https://img.shields.io/github/downloads/Amhage-Technology-Group/neuryxiq-releases/total?color=2b6cff&label=downloads" alt="Downloads">
  <img src="https://img.shields.io/badge/license-GPLv2-1f6feb" alt="License GPLv2">
  <img src="https://img.shields.io/badge/platform-Windows%2011-0078d4" alt="Windows 11">
  <a href="https://neuryxiq.com"><img src="https://img.shields.io/badge/managed%20cloud-neuryxiq.com-0b2447" alt="Managed cloud"></a>
</p>

---

This repository holds the official NeuryxIQ installers and deployment files. Download, install, and you are protected in minutes. No account required.

## Download

**Windows (recommended):** grab `NeuryxIQ-Setup.exe` from the [latest release](../../releases/latest). Also on [SourceForge](https://sourceforge.net/projects/neuryxiq/).

Requirements: Windows 11 64-bit, 8 GB RAM (16 GB recommended), 20 GB free disk. The installer installs Docker Desktop for you if it is not already present.

## Install

1. Run `NeuryxIQ-Setup.exe`. Windows may show an "unknown publisher" notice for this release: choose **More info → Run anyway**.
2. Accept the license and click through. If Docker Desktop is being installed for the first time, Windows may ask to restart; restart, then start NeuryxIQ from the desktop shortcut.
3. When asked, optionally paste your Claude (Anthropic) API key to turn on the AI SOC. Leave it blank for human-only monitoring; you can add it later by running "Start NeuryxIQ" again.
4. Windows asks once for permission to trust the install's own certificate (click Yes). The console then opens at **https://neuryxiq.localhost/** with a padlock, no warning. (`https://localhost/` works too.)

**First login:** `admin` / `admin`. Change the password immediately after signing in.

Add your first device: open **https://&lt;this-pc-name&gt;/enroll/** from any computer in the practice (Windows or Linux) and run the one command shown, or use the Command Center's *Add a device* sheet. It appears in the console within a minute or two.

## What gets installed

A single-node NeuryxIQ stack in Docker: the NeuryxIQ console, the NeuryxIQ indexer, the NeuryxIQ manager (devices report to it on ports 1514/1515), the enrollment service, the adapter that feeds the console, and a TLS front end on ports 80 and 443. Each install generates its own certificate authority; nothing is shared between installs.

## Linux / manual deployment

`neuryxiq-deploy-v1.0.3.zip` on the [latest release](../../releases/latest) contains the same `docker-compose.yml`, `Caddyfile`, `env.example`, enrollment service, adapter and certificate config the installer uses, for teams that prefer to run it by hand (Docker Engine + Compose v2 required):

```bash
cp env.example .env
docker compose up -d
# then open https://<your-host>/  (trust the CA Caddy generates, or use your own cert)
```

## Verify your download

SHA-256 of `NeuryxIQ-Setup.exe` (v1.0.3): `9b5ec055ccbfe2760d841dad92caf728cb842de77f5a5dd8117792b7fe801489`

SHA-256 of `neuryxiq-deploy-v1.0.3.zip`: `ee36ed109e40e579f8fcf9d66dcaa019100d0f0c834ec220e34afd1e4c19e97f`

## Support and commercial services

The on-premises edition is free to download and use. Want a team behind it? **[Support Plan, $199/mo, and Professional Install, $499](https://neuryxiq.com/services/)**, card checkout, no contract. Would rather we ran it? **[Upgrade to the managed cloud](https://neuryxiq.com/upgrade/)**, live in about 30 minutes. Questions: hello@neuryxiq.com

## License and trademarks

The NeuryxIQ platform images are derived from open-source components and are distributed under their respective licenses (the detection and indexing stack under GPLv2 and Apache-2.0). The deployment files in this repository are provided under GPLv2 (see `LICENSE`; summary in `TERMS.md`). **NeuryxIQ**, the NeuryxIQ logo, and "Answers, not alerts." are trademarks of Amhage Technology Group LLC and are not covered by the open-source licenses; see `TRADEMARKS.md`.

© Amhage Technology Group LLC
