[![](./FoxG-Kit.png)](./FoxG-Kit.png)

# Go-Native

**A multi-client application foundation with a Go backend.**

The API in `backend/` is the source of truth and follows the [FoxG wire contract](../../../CONTRACT.md). `web use svelte` installs the Go-Svelte frontend into `frontend/web`. Android and Windows folders exist so the layout is ready; they are not implemented. Go is the scale tier of the family: the starter tier is Fast, Elysia, and Hono; the enterprise tier is Rust and DotNet.

**Docs:** [AGENTS.md](AGENTS.md) · [ROADMAP.md](ROADMAP.md) · [docs/](docs/) · [plans](__plans__/PROGRESS.md) · [`__ctrl__`](__ctrl__/README.md)

```text
backend/               Go API and worker (`backend/internal/modules/{apps,base,system}`, `backend/internal/core`, `backend/cmd/{api,worker}`)
frontend/web           filled by web use svelte
frontend/android       reserved
frontend/windows       reserved
__ctrl__/kits.json     web catalog
__ctrl__/clients.json  client registry
```

```bat
__ctrl__\go-native-ctrl.bat web list
__ctrl__\go-native-ctrl.bat web use svelte
__ctrl__\go-native-ctrl.bat setup-local
__ctrl__\go-native-ctrl.bat dev run all
```

`web use svelte` copies the `frontend/` of the sibling [Go-Svelte](../go-svelte/README.md) into `frontend/web` (the `source` in `__ctrl__/kits.json`; remove `source` to download from GitHub instead), rewrites its Dockerfiles for the `frontend/web` build context, and pins it in a lock file. Run it before `setup-local`.

Scalar: http://api.localhost/sdoc · Swagger: http://api.localhost/docs · Direct API: http://localhost:8000/docs · Superuser `admin@example.com` / `Admin@1234`.

Changing backend works as in every FoxG kit: keep `frontend/`, the module names, and the contract, then reimplement `backend/`. Index: [foxg-kit](../../../README.md).
