## Jellyfin (Docker Deployment)

Jellyfin is deployed as a Docker container and serves as the internal
media streaming platform for members. The service is restricted to the local network and is not exposed
externally.

Deploying as a Docker container rather than a native UGOS
application, ensures the service configuration can be redeployed 
consistently across environments and allows for easier integration with a reverse proxy in the future.

### Storage Layout

- Config and cache stored on SSD pool
- Media stored on HDD RAID pool
- Media mounted read-only inside container

### Network Policy

- Exposed only on local network
- No port forwarding configured
- Reverse proxy planned for future secure access

---

## Deployment Model

- Containerized (Docker)
- Restart policy: `unless-stopped`
- Network mode: bridge
- Internal port: `8096`
- No WAN exposure
- No UPnP
- No port forwarding

---

## Storage Layout

Media and application data are separated.

### Media (HDD RAID)

```
/media/
 ├── movies/
 ├── series/
 ├── music/
 └── home-videos/
```

### Application Data (SSD)

```
/docker/jellyfin/
 ├── config/
 ├── cache/
 └── transcodes/
```

- Media mounted read-only
- Config and transcodes stored on SSD
- Metadata not stored inside media folders

---

## Library Standard

### Movies

```
Movie Title (Year)/
 └── Movie Title (Year).mkv
```

### Series

```
Series Name (Year)/
 └── Season 01/
      └── Series Name - S01E01.mkv
```

---

## Metadata Configuration

- Automatic metadata enabled
- Metadata language set consistently
- Artwork stored in container config
- NFO generation disabled
- Multi-genre classification enabled via metadata providers

---

## Subtitle Policy

- Only text-based subtitles allowed
- Image-based subtitles disabled
- Subtitle extraction enabled
- Embedded subtitles supported

---

## Transcoding Configuration

- Hardware decoding enabled (H264, HEVC, VP9, MPEG2)
- Hardware encoding enabled
- Low-power encoders disabled
- Tone mapping disabled
- Transcode path located on SSD
- Max simultaneous transcodes limited
- Throttling enabled
- Old segments auto-deleted

Hardware passthrough verification pending.

---

## User Access Model

- Individual Jellyfin accounts per member
- No anonymous access
- No shared credentials
- Library access configurable per user
- No filesystem access granted to members

---

## Security State

- LAN-only access
- Remote access disabled
- Automatic discovery disabled
- Container isolated from host services

---

## Status

Deployment complete.
Library structure standardized.
Transcoding optimized.
Service restricted to internal network.
