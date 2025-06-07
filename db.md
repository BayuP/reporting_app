# DB Schema


![db_schema](https://github.com/user-attachments/assets/c139d2fc-615e-4223-a2af-e3181b67183c)


# Database Schema Documentation

## Tables

### users
| Column | Type | Constraints |
|--------|------|-------------|
| id | uuid | PRIMARY KEY |
| name | varchar | |
| username | varchar | |
| password | varchar | |
| email | varchar | |
| role | varchar | |
| category | varchar | |
| company_id | uuid | |

### reports
| Column | Type | Constraints |
|--------|------|-------------|
| id | uuid | PRIMARY KEY |
| photo_url | text | |
| uploaded_by | uuid | |
| description | text | |
| category | varchar | |
| created_at | timestamp | |

### annotations
| Column | Type | Constraints |
|--------|------|-------------|
| id | uuid | PRIMARY KEY |
| report_id | uuid | |
| created_by | uuid | |
| shape | jsonb | |
| label | text | |
| created_at | timestamp | |

### threads
| Column | Type | Constraints |
|--------|------|-------------|
| id | uuid | PRIMARY KEY |
| report_id | uuid | |
| created_by | uuid | |
| status | varchar | |
| created_at | timestamp | |

### messages
| Column | Type | Constraints |
|--------|------|-------------|
| id | uuid | PRIMARY KEY |
| thread_id | uuid | |
| sender_id | uuid | |
| content | text | |
| created_at | timestamp | |

### notification
| Column | Type | Constraints |
|--------|------|-------------|
| id | uuid | PRIMARY KEY |
| user_id | uuid | |
| type | varchar | |
| source_id | uuid | |
| created_at | timestamp | |

## Relationships

### Foreign Key References
- **reports.id** → **annotations.report_id** (One-to-Many)
- **threads.id** → **messages.thread_id** (One-to-Many)
- **users.id** → **messages.sender_id** (One-to-Many)
- **users.id** → **reports.uploaded_by** (One-to-Many)
- **users.id** → **annotations.created_by** (One-to-Many)
- **users.id** → **threads.created_by** (One-to-Many)
- **reports.id** → **threads.report_id** (One-to-One)
- **threads.id** → **notification.source_id** (One-to-Many)
- **messages.id** → **notification.source_id** (One-to-Many)
