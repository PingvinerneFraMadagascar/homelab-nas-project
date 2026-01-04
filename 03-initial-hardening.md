# Initial System Hardening

## Administrative Access
### Admin account strategy

Administrative access was restructured to reduce reliance on default system
accounts. A dedicated administrator account was created for day-to-day
management, following the principle of least privilege.

Default administrative accounts represent a security risk due to their
predictable identity and widespread. These accounts
are commonly targeted by automated attacks, including brute-force attacks.

To reduce this risk, administrative access was migrated to a custom
administrator account, and default accounts were removed.
This approach increases authentication entropy and aligns with industry
security best practices.

### Password policies

Administrative and user account passwords were configured to follow a defined
password policy intended to reduce the risk of credential compromise.

The policy includes:
- Minimum password length requirements
- Use of mixed character classes (upper case, lower case, numbers, symbols)

Temporary account lockout after a certain amount of failed login attempts was also enabled to reduce the risk of brute-force attacks.

This policy prioritizes password strength and uniqueness over frequent forced rotation.

### Two-factor authentication

Multi-factor authentication was enabled to protect privileged access.

## Network Configuration
### Static IP assignment

A static internal IP address was assigned to the NAS using a DHCP reservation
on the local router. The device's unique MAC address was used to ensure that
the router always allocates the same IP whenever the NAS connects.  

#### Benefits of a static internal IP

- *Stability:* Services hosted on the NAS (Docker containers, Jellyfin, Minecraft, etc.) always have a consistent network location.  
- *Reliability:* Avoids disruption in service due to dynamic IP changes.  
- *Simplified configuration:* Port forwarding, container networking, and VM access work without frequent updates.  
- *Easier monitoring and troubleshooting:* Logs and network monitoring can reliably track the device.  
- *Security and access control:* Firewalls, user permissions, and internal access policies can target a known device rather than a changing address.  

### DNS configuration

The NAS was configured to use the local network router as its primary DNS server. 
The router handles internal host resolution for LAN devices and forwards external 
queries to trusted public DNS providers. 

Internal resolution ensures that VMs, containers, and local devices can communicate 
reliably by hostname without relying on external services. External resolution 
enables the NAS to fetch updates, pull Docker images, access Plex metadata, 
and communicate with other online services securely and reliably.

For external queries, the router is configured with trusted public DNS servers: 
Cloudflare DNS (1.1.1.1 as primary and 1.0.0.1 as secondary) to ensure fast, 
reliable, and privacy-respecting resolution.

### Service Exposure

Unused and legacy services were disabled to minimize the system's attack
surface. Only services required for administration and planned workloads were
left enabled.

This approach aligns with best practices for reducing unnecessary network
exposure in always-on systems and thereby minimizing the systems attack surface.

### Time and Logging

The operating system was updated to the latest stable release prior to service
deployment. System logging and time synchronization were verified to ensure
accurate event tracking and log correlation.

These controls are essential for troubleshooting, auditing, and future
security analysis.
