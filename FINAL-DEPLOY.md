# KDN v1.0 — Final Deployment Runbook

## Preferred first launch: Render Blueprint
1. Put this project in a private Git repository.
2. In Render, create a Blueprint from the repository root `render.yaml`.
3. Supply `CORS_ORIGIN`, `PUBLIC_BASE_URL`, and `KDN_AI_API_KEY` in the dashboard; never commit them.
4. The API uses the managed Postgres connection and runs migrations before deploy.
5. Keep external agent connectors empty until separately authorized/tested.
6. After deployment, verify `/api/v1/live`, `/api/v1/ready`, `/api/v1/health`, login, Khatri AI, Constitution, Creator Studio and research worker logs.

## Railway alternative
1. Create a project and add PostgreSQL (pgvector template if vector retrieval is enabled).
2. Deploy the repository and set `RAILWAY_DOCKERFILE_PATH=server/Dockerfile` or use `deploy/railway/railway.json` as a configuration reference.
3. Set `DATABASE_URL`, `JWT_SECRET`, production CORS/base URL and optional AI key as private variables.
4. Run `npm run db:migrate` from the server working directory before public beta.

## Boundary
This pack is deployment-ready configuration, not a claim that a public server already exists. DNS/account ownership and secret credentials must be supplied by the infrastructure owner.
