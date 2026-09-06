# Space Rocks

**Server-authoritative multiplayer arcade combat built with Godot, Go, and Rails.**

Space Rocks is an Asteroids-inspired online action game that has grown from a playable arcade prototype into a multi-service multiplayer system. The Godot client presents the game, a Go server owns authoritative realtime simulation and match state, and a Ruby/Rails API owns account, authentication, and platform services.

**[Watch the gameplay demo](https://www.youtube.com/watch?v=8UXrnRvapHQ)** · **[Download and play the v0.2.1 alpha](https://github.com/Lokee86/space-rocks/releases/tag/v0.2.1)** · **[Read the devlog](https://space-rocks.laughingskull.ca/)**

The public alpha is packaged for Windows and macOS and includes hosted multiplayer plus packaged single-player support. The project remains in active development, but it is buildable, downloadable, and playable outside the development environment.

## Overview

```text
Godot client              Go realtime game server              Rails API
presentation + input      authoritative simulation             accounts + auth
rendering + UI            match + world state                  platform services
```

The architecture is deliberately server-authoritative: clients submit player intent while the Go game server owns gameplay truth. Shared contracts and generated data keep the Godot, Go, and Rails surfaces aligned across service boundaries.

This README is the repository front door. For setup, local development workflow, tools, and handoff notes, start with [Developer onboarding](docs/developer.md).

## Repository Layout

```text
client/                 Godot client project
services/game-server/   Go realtime game server
services/api-server/    Ruby/Rails API server
shared/                 Shared source-of-truth data
tools/data_sync/        Shared data validation and generation tooling
bruno-api/              Bruno collection for local API smoke tests
docs/                   Project documentation
```

## Getting Started

Install the main local development tools:

```text
Godot 4.6.x
Go 1.26.x
Ruby / Rails
Python 3.10+
Git LFS
```

After cloning, install and pull Git LFS assets:

```bash
git lfs install
git lfs pull
```

Open the Godot project from:

```text
client/
```

Run the game server from:

```bash
cd services/game-server
go run ./cmd/game-server
```

For the full setup path, local commands, repo tools, and development cautions, use [Developer onboarding](docs/developer.md).

## Documentation

Primary documentation entry points:

* [Developer onboarding](docs/developer.md) - Setup, local workflow, development tools, verification, and handoff notes.
* [Documentation index](docs/!INDEX.md) - Browse the project documentation by area.
* [Documentation policy](docs/documentation-policy.md) - Rules for where documentation belongs.
* [Documentation procedure](docs/documentation-procedure.md) - Workflow for creating, moving, updating, graduating, and deleting docs.

Documentation areas:

* [Agent docs](docs/agent/!INDEX.md) - Agent workflow, testing expectations, MCP usage, and implementation guardrails.
* [Data docs](docs/data/!INDEX.md) - Source-of-truth files, generated outputs, schemas, and data-sync pipelines.
* [Devtools docs](docs/devtools/!INDEX.md) - Debug and development tooling.
* [Domain docs](docs/domains/!INDEX.md) - Cross-system player, platform, and technical flows.
* [Limits docs](docs/limits/!INDEX.md) - Temporary blockers, bugs, and transitional limitations.
* [Planning docs](docs/planning/!INDEX.md) - Future, unresolved, proposed, or not-yet-current work.
* [Protocol docs](docs/protocol/!INDEX.md) - HTTP, WebSocket, packet, and message-flow contracts.
* [Service docs](docs/services/!INDEX.md) - Runtime implementation docs for client, game-server, API server, player-data, and web.
* [Systems-design docs](docs/systems-design/!INDEX.md) - Conceptual mechanics, authority boundaries, invariants, and durable design rules.

## Development Entry Points

Use these docs instead of expanding this README with detailed workflow instructions:

* [Developer onboarding](docs/developer.md) for setup, tools, and handoff.
* [Testing](docs/agent/testing.md) for verification expectations.
* [MCP servers](docs/agent/mcp-servers.md) for Info MCP, Write MCP, and EngineForge/Godot bridge usage.
* [Source-of-truth map](docs/data/source-of-truth-map.md) for ownership questions.
* [Data sync and source-of-truth pipeline](docs/data/data-sync-and-ssot-pipeline.md) for generated outputs and shared data workflows.
* [API-server Bruno smoke tests](docs/devtools/api-server/bruno-smoke-tests.md) for Bruno usage.

## Assets And Git LFS

Source assets and binary game assets are part of the repo workflow. Git LFS is required for asset patterns such as images and audio.

Generated recordings, local editor state, caches, and build artifacts should not be committed.

## License

All rights reserved.
