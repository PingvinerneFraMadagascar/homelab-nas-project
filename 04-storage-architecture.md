# Storage Architecture

## Overview

The NAS uses a tiered storage layout to match different types of workloads.
Hard drives provide large, reliable storage for files and media, while solid-
state drives are used for applications that benefit from faster access.

This separation improves performance, simplifies maintenance, and makes it
easier to expand or change the system in the future.

## Hard Drive Storage

The primary storage pool consists of four hard drives configured in RAID 6.
This pool is used for general file storage, media libraries, and backups.

RAID 6 was selected to allow the system to tolerate multiple drive failures
while maintaining data availability, which is important for an always-on NAS.

## Solid-State Storage

Two NVMe SSDs are used, each with a specific role.

### Application and Virtual Machine Storage

One NVMe SSD is dedicated to Docker containers and virtual machines. These
workloads generate frequent read and write operations and benefit from low
latency storage.

Placing applications and VMs on a dedicated SSD helps ensure smooth performance
and keeps application activity from impacting file storage.

### SSD Cache

A dedicated NVMe solid-state drive was configured as a read-only cache for the
hard disk RAID pool. This cache layer improves responsiveness for frequently
accessed data and reduces latency associated with repeated read operations.

Cached data can be rebuilt if needed, and the cache does not replace the need
for regular backups.

## Design Considerations

- Performance-sensitive workloads are isolated from bulk storage
- Storage roles are clearly defined and easy to reason about
- The layout supports future upgrades without major reconfiguration
- Failure of the cache device does not affect data integrity
