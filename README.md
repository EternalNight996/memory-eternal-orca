# Memory Atlas for Orca

Standalone Orca plugin package for [memory-eternal](https://github.com/EternalNight996/memory-eternal).

Adds a **记忆** panel in Orca's right sidebar. Clicking it sends `dsh-memory open` to the selected terminal, opening the same Memory Atlas Web UI used by DSH/web.

## Install with Orca Git URL (recommended)

Orca → Settings → Plugins → Install plugin → **Git URL**:

```text
https://github.com/EternalNight996/memory-eternal-orca#v0.13.0
```

Orca pins the install to the `v0.13.0` tag.

## Install from a local folder

Orca → Settings → Plugins → Install plugin → **Local folder**:

```text
<path-to-this-folder>
```

The folder must contain `orca-plugin.json` at its root.

## Requirements

- Orca `>= 1.4.0`
- `memory-eternal` installed on the machine
- `dsh-memory` available in the terminal used by Orca

Check:

```bash
dsh-memory --help
```

If it is missing, use the full path under your DSH profile, for example:

```text
C:\Users\<you>\.dsh\profiles\desktop\node_modules\.bin\dsh-memory.cmd open
```

## Permissions

- `workspace:read` — read the focused worktree's terminal list
- `terminal:send` — send `dsh-memory open` to the selected terminal

No card writes, no approve/reject, no agent permissions.

## Why a launcher, not an iframe

Orca plugin panels use a strict sandbox CSP:

```text
default-src 'none'
connect-src 'none'
img-src data:
```

The panel therefore cannot iframe `http://127.0.0.1:7999` or fetch the local API. The panel opens the Web UI instead; review still happens in the Web UI, with the human in control.

## License

MIT
