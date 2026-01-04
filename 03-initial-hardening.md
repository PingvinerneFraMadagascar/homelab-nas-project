# Initial System Hardening

## Administrative Access
#### Admin account strategy

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

#### Password policies

Administrative and user account passwords were configured to follow a defined
password policy intended to reduce the risk of credential compromise.

The policy includes:
- Minimum password length requirements
- Use of mixed character classes (upper case, lower case, numbers, symbols)

Temporary account lockout after a certain amount of failed login attempts was also enabled to reduce the risk of brute-force attacks.

This policy prioritizes password strength and uniqueness over frequent forced rotation.

#### Two-factor authentication

Multi-factor authentication was enabled to protect privileged access.

## Network Configuration
- Static IP assignment
- DNS configuration

## Service Exposure
- Disabled unused services
- Rationale for minimal attack surface

## Time and Logging
- NTP configuration
- Log review considerations
