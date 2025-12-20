# Architecture Overview

## Hardware

**Previous**
- CPU: i5-13400
- Motherboard: MSI MPG Z790 EDGE
- RAM: G.Skill Trident Z5 RGB 96 GB (2 x 48 GB) DDR5-6800 CL34
- Storage:
  - 1× 1TB NVMe (Proxmox boot)
  - 2× 512GB SATA SSD
  - 2× 6TB HDD

**Current**
- CPU: i9-14900K
- Motherboard: ASUS Z790 Hero
- RAM: G.Skill Trident Z5 RGB 96 GB (2 x 48 GB) DDR5-6800 CL34
- Storage:
  - 1× 1TB NVMe (Proxmox boot)
  - 2x 2TB NVMe
  - 2× 512GB SATA SSD
  - 2× 6TB HDD
  - 4x 4TB HDD

**Reason for Upgrade**
- Higher core count for VM density
- Better power delivery and BIOS feature set
- Long-term homelab scalability
- Running AI interfernce and fine-tuning with the extra PCIe x16 slot

## Hypervisor
- Proxmox VE

## Networking
- vmbr0 bridged to physical NIC
- Internal VMs on LAN
- VPN used for remote administration

## Services (current)
- Docker host VM
- Mailcow (local-only, no public domain yet)
