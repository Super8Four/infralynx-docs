# Jobs API

The jobs API provides a baseline asynchronous execution surface for background work.

## Endpoints

- `POST /api/jobs`
- `GET /api/jobs`
- `GET /api/jobs/{jobId}`
- `GET /api/jobs/{jobId}/logs`

## Headers

- `X-InfraLynx-Actor-Id`
- `X-InfraLynx-Role-Ids`
- `X-InfraLynx-Tenant-Id`

## Permission model

- `job:write` is required to create jobs
- `job:read` is required to read job records or job logs

## Request shape

`POST /api/jobs` accepts:

- `type`: job type identifier
- `payload`: JSON object payload
- `createdBy`: optional explicit creator override
- `retryPolicy`: optional retry policy override

## Response shape

Job responses include:

- job metadata
- current status
- retry count
- current result payload
- associated job logs for detailed inspection
