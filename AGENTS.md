# AGENTS.md

Go-Native is the multi-client Go foundation. The API is Go and follows [CONTRACT.md](../../../CONTRACT.md). The only installable client today is the Svelte web client.

`__ctrl__/clients.json` is the single client registry. `web use` reads the `web` section and installs an enabled client into `frontend/web`. `android` and `windows` are reserved. Do not add a second registry, and do not invent WinUI or Compose apps until a client is enabled.

Do not reshape the Go API as FastAPI, Hono, or Elysia. Backend layout: `backend/internal/modules/{apps,base,system}`, `backend/internal/core`, `backend/cmd/{api,worker}`. Layers: Route (`net/http` handler) -> Service -> Repository (interface, pgx) -> PostgreSQL. SQL stays explicit: queries in `backend/sql/queries`, migrations in `backend/migrations`. Jobs use the Redis list protocol in the contract; there is no queue library. Go handler tests live in `tests/backend/` (a separate Go module whose path is under the backend module's, with `replace => ../../backend`, so it may import `backend/internal/...`; shared harness in `tests/backend/testkit`). Run `__ctrl__\go-native-ctrl.bat test backend` before calling a stage done, and `__ctrl__\go-native-ctrl.bat test contract` against a running API after a route change.
