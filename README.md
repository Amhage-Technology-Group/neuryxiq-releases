# NeuryxIQ Downloads

**Answers, not alerts.** AI-ready security operations and HIPAA posture for small medical and dental practices, running on your own hardware.

This repository holds the official NeuryxIQ installers and deployment files. Download, install, and you are protected in minutes. No account required.

## Download

**Windows (recommended):** grab `NeuryxIQ-Setup.exe` from the [latest release](../../releases/latest).

Requirements: Windows 10/11 64-bit, 8 GB RAM (16 GB recommended), 20 GB free disk. The installer installs Docker Desktop for you if it is not already present.

## Install

1. Run `NeuryxIQ-Setup.exe`. Windows may show an "unknown publisher" notice for this release: choose **More info → Run anyway**.
2. Accept the license and click through. If Docker Desktop is being installed for the first time, Windows may ask to restart; restart, then start NeuryxIQ from the desktop shortcut.
3. When asked, optionally paste your Claude (Anthropic) API key to turn on the AI SOC. Leave it blank for human-only monitoring; you can add it later by running "Start NeuryxIQ" again.
4. The console opens at **https://localhost/** (a one-time certificate warning on localhost is expected).

**First login:** `admin` / `admin`. Change the password immediately after signing in.

Add your first device from the Command Center: pick the Windows workstation or server, copy the one-line installer, and it appears in the console protected.

## What gets installed

A single-node NeuryxIQ stack in Docker: the NeuryxIQ console, the NeuryxIQ indexer, the NeuryxIQ manager, and a TLS front end on ports 80 and 443. Each install generates its own certificate authority; nothing is shared between installs.

## Linux / manual deployment

`neuryxiq-deploy-v1.0.1.zip` on the [latest release](../../releases/latest) contains the same `docker-compose.yml`, `Caddyfile`, `env.example` and certificate config the installer uses, for teams that prefer to run it by hand (Docker Engine + Compose v2 required):

```bash
cp env.example .env
docker compose up -d
# then open https://<your-host>/
```

## Verify your download

SHA-256 of `NeuryxIQ-Setup.exe` (v1.0.1): `73eea1ee78825c4c6a844e3868522d847265fb9cc7b696a5d47f9401c5752ef5`

## Support and commercial services

The on-premises edition is free to download and use. Amhage Technology Group offers paid installation, support contracts, and a fully managed cloud edition at [neuryxiq.cloud](https://neuryxiq.cloud). Questions: hello@neuryxiq.cloud

## License and trademarks

The NeuryxIQ platform images are derived from open-source components and are distributed under their respective licenses (the detection and indexing stack under GPLv2 and Apache-2.0). The deployment files in this repository are provided under GPLv2 (see `LICENSE`; summary in `TERMS.md`). **NeuryxIQ**, the NeuryxIQ logo, and "Answers, not alerts." are trademarks of Amhage Technology Group LLC and are not covered by the open-source licenses; see `TRADEMARKS.md`.

© Amhage Technology Group LLC
