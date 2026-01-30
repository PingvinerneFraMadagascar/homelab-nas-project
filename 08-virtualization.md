# Virtualization Environment

The NAS is configured to run virtual machines for cybersecurity lab and
learning purposes.

## Storage Strategy

Virtual machine disks are stored on the SSD pool to provide low latency and
high I/O performance. This prevents virtual workloads from impacting bulk data
storage on the HDD RAID array.

## Network Configuration

Virtual machines use bridged networking to obtain IP addresses on the local
network. This allows them to behave like independent systems for realistic lab
scenarios.

## Use Cases

- Cybersecurity lab environments
- Testing and learning new operating systems
- Safe experimentation without affecting the host system

