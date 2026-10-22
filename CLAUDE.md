# Claude Code Project Context
This is an Express.js REST API with in-memory storage. It provides user management and health check endpoints.

## Commands
- `npm run dev` — start the API server (listens on http://localhost:3000)
- `npm test` — run the test suite
- `npm run lint` — check code style

## Conventions
- One route file per resource in `routes/` directory
- Use Express Router for all route definitions
- All data access goes through `db/store.js`

## Architecture
- `server.js` — entry point, sets up Express app and middleware
- `routes/` — contains `users.js` and `health.js`, one file per resource
- `db/store.js` — in-memory data helper used by routes
- `tests/` — test files using the built-in test runner
