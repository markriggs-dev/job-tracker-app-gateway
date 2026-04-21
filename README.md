# job-tracker-app-gateway

API Gateway for the Job Tracker application. Handles request routing, JWT validation via Auth0, and rate limiting. All client traffic enters the system through this gateway.

## Technology
- .NET 8 / YARP (Yet Another Reverse Proxy)
- Auth0 JWT validation
- Docker

## Getting started

```bash
dotnet restore
dotnet run --project src/Gateway.Api
```

## Routes

| Path prefix        | Upstream service           |
|--------------------|----------------------------|
| `/api/jobs`        | job-tracker-app-job-service        |
| `/api/contacts`    | job-tracker-app-contact-service    |
| `/api/journal`     | job-tracker-app-journal-service    |
| `/api/resumes`     | job-tracker-app-resume-service     |
| `/api/users`       | job-tracker-app-user-service       |
| `/api/ai`          | job-tracker-app-ai-service         |

## Environment variables

| Variable | Description |
|----------|-------------|
| `Auth0__Domain` | Auth0 domain for JWT validation |
| `Auth0__Audience` | Auth0 API audience |
| `ReverseProxy__*` | YARP upstream service URLs |
