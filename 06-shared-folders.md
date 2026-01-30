# Access Control Model

This NAS uses a role-based access control (RBAC) model. Permissions are assigned
to groups instead of individual users to keep management simple and scalable.

## Group Types

Two group categories are used:

- data_* groups control access to shared folders
- app_* groups control access to NAS application-related documents

## Data Access Group Examples

| Group | Purpose |
|-------|---------|
| data_family | Access to family childhood photos |
| data_shared | Access to general shared files |
| data_docker | Access to collaborative Docker project storage |

## Application Access Group Examples

| Group | Application |
|-------|-------------|
| app_docker | Docker container management |
| app_jellyfin | Jellyfin media server |
| app_[Application] | Other application |

## Design Principles

- Least privilege access
- Separation of data storage and application permissions
- Scalable structure for future apps and shared resources

