# Architecture Overview

## Hardware
- CPU: i5-13400
- RAM: 96 GB
- Storage:
  - 1× 1TB NVMe (Proxmox boot)
  - 2x 2TB NVMe
  - 2× 512GB SATA SSD
  - 2× 6TB HDD
  - 4x 4TB HDD

## Hypervisor
- Proxmox VE

## Networking
- vmbr0 bridged to physical NIC
- Internal VMs on LAN
- VPN used for remote administration

## Services (current)
- Docker host VM
- Mailcow (local-only, no public domain yet)
