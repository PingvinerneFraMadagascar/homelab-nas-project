## Jellyfin (Docker Deployment)

Jellyfin is deployed as a Docker container rather than a native UGOS
application. This ensures the service configuration can be redeployed 
consistently across environments and allows for easier integration with a reverse proxy in the future.

### Storage Layout

- Config and cache stored on SSD pool
- Media stored on HDD RAID pool
- Media mounted read-only inside container

### Network Policy

- Exposed only on local network
- No port forwarding configured
- Reverse proxy planned for future secure access
