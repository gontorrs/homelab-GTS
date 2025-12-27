# Project Neuromancer

Private AI homelab designed to run a local assistant and a complete home server ecosystem without relying on cloud services. Everything runs on the local network, with full control over data and services.

## Overview

The system is built around:

- A main server with an **RTX 3090** for all AI, media, and gaming workloads.  
- An always‑on infrastructure node for networking, security, and backups.  
- Several lightweight edge nodes distributed around the house for voice and sensors.

The goal is to have an assistant that supports studying, home automation, and media management while keeping all data private.

## AI Assistant

The core of the project is a local assistant based on a **Qwen 13B** model:

- It will run on the RTX 3090; if the full model does not fit in VRAM, a quantized **int4** variant will be used to balance memory usage and performance.  
- It will use **RAG** (Retrieval‑Augmented Generation) to query locally stored notes, technical documentation, and personal data.  
- Planned capabilities:  
  - Create and modify calendar events.  
  - Edit and organize notes (Obsidian).  
  - Generate summaries, study plans, and task checklists.  
  - Execute actions through internal APIs (trigger home‑automation scenes, maintenance scripts, etc.).  
  - Access offline documentation using Kiwix.

Interaction will be available via both voice and text, using:

- **Whisper** for local speech‑to‑text.  
- **Piper** or **Chatterbox** for local text‑to‑speech.  
- Wake‑word detection running on small devices placed in multiple rooms.

## Server and Services

The homelab will be organized into service layers.

### Main server (AI + Media)

Planned services:

- Qwen 13B LLM and the RAG engine.  
- Media server using **Jellyfin** to manage a personal and legal media library.  
- Game streaming with **Sunshine/Moonlight** to play PC games from other devices in the house.  
- Camera processing and object detection with **Frigate**.

### Infrastructure node

The always‑on node will handle:

- **Pi‑hole** as DNS and network‑wide ad blocker.  
- **WireGuard** VPN for secure remote access.  
- **Nginx Proxy Manager** for SSL certificates and reverse proxy.  
- **Authentik** for Single Sign‑On (SSO) across internal services.  
- **Vaultwarden** as self‑hosted password manager.  
- Automated backups with **BorgBackup** following a 3‑2‑1 style strategy.  
- Unified dashboard with **Homepage** and container management with **Portainer**.

### Edge nodes (voice and sensors)

Lightweight devices around the house will provide:

- Local wake‑word detection and microphone input.  
- Audio streaming to the main server for processing.  
- Integration with **Home Assistant** to control lights, plugs, scenes, and other smart‑home automations.

## Containers already running

On a Raspberry Pi 5, the following Docker containers are already deployed and in use:

- **WireGuard (wg-easy)** for simplified VPN management.  
- **Pi-hole** as DNS server and network‑wide ad blocker.  
- **Filebrowser** for web-based file management on the homelab storage.

## Implementation Roadmap

1. Bring up the infrastructure node (DNS, VPN, backups, SSO).  
2. Deploy the media stack (Jellyfin and automation services).  
3. Set up the AI server with Qwen 13B and the RAG pipeline.  
4. Add cameras, voice satellites, and advanced home‑automation integration.  
5. Refine the assistant experience with contextual responses, personalized summaries, and unified control over the entire homelab.

This repository will host the design documentation, configuration files, and progressively the code and scripts required to deploy the system.

---

Author: **Gonzalo Torras Serrano**  
© 2025 Gonzalo Torras Serrano. All rights reserved.
