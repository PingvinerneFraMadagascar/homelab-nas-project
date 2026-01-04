# Hardware Selection

## Platform Overview
- Model: UGREEN DXP 4800 Plus
- Form factor: 4-bay NAS
- Intended use: Homelab, media server, learning environment

## Storage Devices

### Hard Disk Drives
- 4 × 8 TB Western Digital Red Pro
- Intended configuration: RAID 6
- Rationale:
  - Redundancy for multiple drive failures
  - Suitable for always-on workloads
  - Designed for NAS environments

### Solid State Drives
- 1 × 2 TB Samsung 990 Pro NVMe
  - Role: Docker and virtual machine storage
- 1 × 1 TB Samsung 990 pro NVMe
  - Role: Read/write cache

### Rationale for SSD Roles
- Separation of cache and application workloads
- High endurance and performance for VM and container I/O
- Acceptable risk profile for homelab environment

## Memory
- Default: 8 GB
- Planned upgrade: 16–32 GB
- Rationale:
  - Support for containers and virtualization
  - Flexibility for future expansion

## Networking
- Onboard Ethernet (details TBD)
- Intended use: Local services and controlled external access

## Design Constraints
- Noise and power suitable for home environment
- Limited physical expansion
- Emphasis on reliability over maximum performance
