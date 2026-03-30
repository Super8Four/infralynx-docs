# Backup API

The backup API manages backup creation, restore preview, restore execution, and backup scheduling.

## Endpoints

### `GET /api/backup`

Returns:

- known backups
- backup logs
- supported backup sections
- engine strategy descriptions

Requires:

- `backup:read`

### `POST /api/backup/create`

Creates a backup immediately.

Payload:

```json
{
  "mode": "partial",
  "sections": ["inventory", "audit"],
  "engine": "bootstrap-file-store",
  "label": "pre-change-window"
}
```

Requires:

- `backup:write`

### `GET /api/backup/{backupId}`

Returns the selected backup plus restore preview data.

Requires:

- `backup:read`

### `DELETE /api/backup/{backupId}`

Deletes backup metadata and the stored archive.

Requires:

- `backup:write`

### `POST /api/backup/restore/validate`

Preview and validate a restore.

Payload:

```json
{
  "backupId": "backup-123"
}
```

Requires:

- `backup:read`

### `POST /api/backup/restore`

Executes a restore after validation succeeds.

Payload:

```json
{
  "backupId": "backup-123"
}
```

Requires:

- `backup:restore`

### `POST /api/backup/schedules`

Creates a scheduler entry that enqueues `backup.create` jobs.

Payload:

```json
{
  "name": "nightly backup",
  "cronExpression": "0 2 * * *",
  "mode": "full",
  "label": "nightly"
}
```

Requires:

- `schedule:write`
