<p align="center">
  <img src="https://github.com/Amhage-Technology-Group.png" width="112" alt="NeuryxIQ">
</p>
<h1 align="center">NeuryxIQ</h1>
<p align="center"><b>The Autonomous Security Platform for medical and dental practices.</b><br>
Security operations, detection and HIPAA posture in one console. Answers, not alerts.</p>

<p align="center">
  <a href="https://github.com/Amhage-Technology-Group/neuryxiq-releases/releases/latest/download/NeuryxIQ-Setup.exe"><img src="https://img.shields.io/badge/Download-Windows%20Installer-2b6cff?style=for-the-badge&logo=windows&logoColor=white" alt="Download the Windows installer"></a>
  <a href="https://github.com/Amhage-Technology-Group/neuryxiq-releases/releases/latest/download/NeuryxIQ-Appliance-1.0.3.ova"><img src="https://img.shields.io/badge/Download-Virtual%20Appliance%20(OVA)-0b2447?style=for-the-badge" alt="Download the virtual appliance"></a>
</p>
<p align="center">
  <a href="https://github.com/Amhage-Technology-Group/neuryxiq-releases/releases/latest"><img src="https://img.shields.io/github/v/release/Amhage-Technology-Group/neuryxiq-releases?label=release&color=2b6cff" alt="Latest release"></a>
  <img src="https://img.shields.io/github/downloads/Amhage-Technology-Group/neuryxiq-releases/total?color=2b6cff&label=downloads" alt="Downloads">
  <img src="https://img.shields.io/badge/license-GPLv2-1f6feb" alt="License GPLv2">
  <img src="https://img.shields.io/badge/platform-Windows%2011%20%7C%20Linux%20%7C%20VM-0078d4" alt="Platforms">
  <a href="https://sourceforge.net/projects/neuryxiq/"><img src="https://img.shields.io/badge/mirror-SourceForge-ff6600" alt="SourceForge mirror"></a>
</p>

---

## Overview

NeuryxIQ is a security operations platform built for small and mid-sized healthcare practices: medical offices, dental groups, imaging centers and the managed service providers who serve them. It combines endpoint detection, device inventory, benchmark-based compliance scoring, HIPAA policy management and an AI-assisted security operations center in a single console that reads in plain language.

This repository is the official distribution channel for the **NeuryxIQ On-Premises Edition**, published and maintained by Amhage Technology Group LLC. Every release carries SHA-256 checksums and release notes.

## Editions

| Edition | Deployment | Operated by | Commercial terms |
|---|---|---|---|
| **On-Premises** | Windows installer, virtual appliance (OVA) or Docker Compose, on hardware you control | Your practice or your IT provider | Free. GPLv2. No registration. |
| **On-Premises with Support Plan** | As above | Your team, with NeuryxIQ engineering support | $199 per month, cancel any time |
| **Professional Install** | As above, installed and configured by NeuryxIQ | Handover to your team | $499 one-time |
| **Managed Cloud** | Dedicated instance operated by NeuryxIQ | NeuryxIQ, with AI SOC and human oversight | $500 per month |

Pricing and terms: https://neuryxiq.com/services/ and https://neuryxiq.com/upgrade/.

## What is included

- **Command Center**: security posture, protected devices, open threats, items to review and compliance status at a glance.
- **Detection and response**: every device event evaluated against the detection library; findings ranked by real risk and mapped to MITRE ATT&CK.
- **Asset intelligence**: operating system, software inventory, open ports, services and hotfixes for every enrolled device, refreshed automatically.
- **Compliance**: benchmark checks scored against HIPAA Security Rule, PCI DSS, NIST and ISO; an automated Security Risk Assessment; 22 HIPAA policy templates ready to adopt.
- **AI SOC** (optional): three analyst tiers (monitoring and triage, investigation and response, threat hunting and forensics) operating on your own Anthropic API key, with an auditable decision log. The platform runs fully without it.
- **Reporting**: board-ready, branded reports generated from live data.
- **Device enrollment**: a per-install enrollment key and a one-command installer for Windows and Linux, served from your own server.

## System requirements

| Component | Requirement |
|---|---|
| Windows server | Windows 11 (64-bit), 8 GB RAM (16 GB recommended), 20 GB free disk, 2 cores. Docker Desktop is installed automatically when absent. |
| Virtual appliance | VirtualBox 7, VMware Workstation/ESXi, or Proxmox. 2 vCPU, 8 GB RAM, 60 GB disk. Outbound internet on first boot. |
| Linux (Compose) | Docker Engine with Compose v2. Sizing as for the appliance. |
| Protected devices | Windows 11 workstations and servers; Linux servers (Debian/Ubuntu and RHEL families). TCP 1514 and 1515 to the server. |
| Browser | Any current browser. |

## Deployment

**Windows installer.** Download `NeuryxIQ-Setup.exe` from the [latest release](../../releases/latest) and run it. The installer places the deployment files, installs Docker Desktop if required, generates the install's enrollment key and certificate authority, opens the required Windows Firewall ports (one elevation prompt), and opens the console at `https://neuryxiq.localhost/`. Windows may display an unknown-publisher notice for this release; choose *More info → Run anyway*. Silent install: `NeuryxIQ-Setup.exe /S`.

**Virtual appliance.** Import `NeuryxIQ-Appliance-<version>.ova`, set the network adapter to Bridged, and power on. The appliance configures itself on first boot (Ubuntu 24.04 LTS; approximately five minutes with internet access) and presents the console address on its screen. The appliance is currently released as a preview.

**Docker Compose.** `neuryxiq-deploy-<version>.zip` contains the deployment files used by both editions above (`docker-compose.yml`, `Caddyfile`, `env.example`, certificate configuration, enrollment service, adapter). See the Installation Guide for the procedure.

**First sign-in:** `admin` / `admin`. Change the password immediately. **Add devices:** open `https://<server>/enroll/` from any computer in the practice and run the single command shown.

## Documentation

| Document | Scope |
|---|---|
| [Quick Start Guide](../../releases/latest/download/NeuryxIQ-Quick-Start-Guide-1.0.3.pdf) | From download to the first protected device |
| [Installation Guide](../../releases/latest/download/NeuryxIQ-Installation-Guide-1.0.3.pdf) | Windows installer, appliance, Compose, networking, certificates, enrollment, upgrades, troubleshooting |
| [Administrator Guide](../../releases/latest/download/NeuryxIQ-Administrator-Guide-1.0.3.pdf) | Console operation, devices, users, AI SOC, data and backups, security practices |

## Security model

Each installation generates its own certificate authority and enrollment key; nothing is shared between installations. Device enrollment requires the key. All data remains on the server you operate; the only outbound connections are software and image downloads and, when enabled, your own AI provider. The platform supports the technical and administrative safeguards of a HIPAA security program and produces the evidence an auditor expects; it is not a medical device, and compliance remains the responsibility of the covered entity.

## Verifying downloads

Each release includes `SHA256SUMS.txt`. Current release (1.0.3):

```
SHA-256  NeuryxIQ-Setup.exe            9b5ec055ccbfe2760d841dad92caf728cb842de77f5a5dd8117792b7fe801489
SHA-256  neuryxiq-deploy-v1.0.3.zip    ee36ed109e40e579f8fcf9d66dcaa019100d0f0c834ec220e34afd1e4c19e97f
SHA-256  NeuryxIQ-Appliance-1.0.3.ova  dc7c8619d8b679c8fc6123b3f471667cf2cddc6d54e459571a54085325c49b0e
```

## Support and services

| Channel | Coverage |
|---|---|
| Community | Release notes and issues in this repository; support@neuryxiq.com on a best-effort basis |
| Support Plan | Business-hours support (US Eastern) by email and remote session, upgrade guidance, detection and policy tuning |
| Professional Install | Installation, configuration and device enrollment performed by NeuryxIQ |
| Managed Cloud | Dedicated instance operated, monitored and backed up by NeuryxIQ; AI SOC and human oversight included |

Commercial enquiries: hello@neuryxiq.com. Service descriptions and ordering: https://neuryxiq.com/services/.

## Licensing and trademarks

The NeuryxIQ platform images are derived from open-source components and are distributed under their respective licenses (the detection and indexing stack under GPLv2 and Apache-2.0). The deployment files in this repository are provided under the GNU General Public License v2 (`LICENSE`; summary of terms in `TERMS.md`). NeuryxIQ, the NeuryxIQ logo and "Answers, not alerts." are trademarks of Amhage Technology Group LLC and are not covered by the open-source licenses (`TRADEMARKS.md`).

## About Amhage Technology Group

Amhage Technology Group LLC builds AI-native security and inspection platforms, founded by practitioners with decades of experience operating regulated healthcare systems. NeuryxIQ is its security operations product for healthcare practices.

© Amhage Technology Group LLC. All rights reserved.
