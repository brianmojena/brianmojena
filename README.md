# Brian Mojena

Full-stack, mobile and AI automation. I build complete systems — backend, web, native apps, and the pipelines that connect them.

**Portfolio:** [brianmojena.vercel.app](https://brianmojena.vercel.app)

## Featured projects

### [Al Día · POS](https://github.com/brianmojena/al-dia-pos) — Full-stack, offline-first
Point-of-sale and inventory for small businesses on unreliable networks. A sale can't be lost because the connection drops: the sale and its sync job are written in a single SQLite transaction (transactional outbox), idempotency is enforced by a partial UNIQUE index rather than application logic, and the overselling race is resolved with a conditional UPDATE that lets the database arbitrate. The same React UI serves two transports — HTTP in the browser, IPC against local SQLite in Electron — with no offline branching in the interface.

`React` · `Electron` · `Express` · `Turso/libSQL` · [Live](https://al-dia-pos.vercel.app)

### [Al Día · Dashboard](https://github.com/brianmojena/al-dia-dashboard) — Kotlin Multiplatform
Owner-facing dashboard for Android and iOS from a single codebase. The entire UI — screens, navigation and state — lives in `commonMain` with Compose Multiplatform; only token storage drops to native code via `expect/actual`. Ktor client with typed error handling that distinguishes network failure, unparseable response and server error. Consumes the same API as the POS.

`Kotlin` · `KMP` · `Compose Multiplatform` · `Ktor`

### [SpaceCommander](https://github.com/brianmojena/space-commander) — Python, async systems
macOS storage analyzer built on a producer/consumer queue with a fixed worker pool over `asyncio.Queue` — recursive `asyncio.gather()` saturates the event loop and freezes the UI on real 150K+ file trees. Two-phase duplicate detection (group by size, SHA-256 only on collisions) and safe deletion via macOS Trash. 56 tests on CI across Python 3.11–3.13.

`Python` · `asyncio` · `Textual` · `pytest`

### [emu-launcher](https://github.com/brianmojena/emu-launcher) — Developer tooling
Terminal dashboard to launch and manage Android AVDs and iOS simulators. Process-based state detection (the macOS `emulator` binary re-execs into a `qemu-system-*` child, so the spawned PID isn't the real one) and genuine boot readiness via `adb getprop sys.boot_completed` rather than a fixed sleep.

`Python` · `Textual` · `Click`

## Stack

**Mobile** — Swift, SwiftUI, Kotlin, Jetpack Compose, Kotlin Multiplatform
**Web** — TypeScript, React, Next.js, Node.js, Express
**Data** — PostgreSQL, SQLite, Turso/libSQL, Supabase
**Other** — Python, Electron, AI/LLM integration

---

Open to roles and projects — remote or on-site.
