# AI Factory Control Sheet Schema

## DATA_CATALOG
| Column | Description |
|------|------------|
| id | Unique file identifier |
| source | Data source (gmail, upload, api) |
| filename | Original filename |
| mime | MIME type |
| raw_path | Drive path in RAW |
| clean_path | Drive path in CLEAN |
| gold_path | Drive path in GOLD |
| status | processed / failed |
| added_at | Timestamp |

## EVENT_LOG
| Column | Description |
|------|------------|
| ts | Event timestamp |
| agent | ingest / clean / analyze / report |
| action | Action performed |
| status | success / error |
| notes | Debug info |

## TASKS_INBOX
| Column | Description |
|------|------------|
| ts | Created timestamp |
| task | Task description |
| priority | low / medium / high |
| status | open / done |
