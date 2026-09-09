# Brian Mojena

Full-stack, mobile and AI automation. I build complete systems — backend, web, native apps, and the pipelines that connect them.

**Portfolio:** [brianmojena.vercel.app](https://brianmojena.vercel.app)

## Featured projects

### [Iris](https://github.com/brianmojena/iris) — WebGL2 image editing, open source
A photo editor that runs entirely in the browser: no server, no accounts, and no image ever leaves the device. The whole edit is a single serialisable object — no tool touches pixels, they only write into it — so non-destructive editing, navigable history and presets all fall out of that for free. Preview and export go through the same renderer at different sizes, so there is no second render path that could drift from what you see. The four tone curves collapse into one 256-entry RGBA texture, interpolated with monotone cubic (Fritsch–Carlson) because the usual splines overshoot and draw banding the user never asked for. Colour-managed in Display P3. 90 render-regression tests in a headless Chromium, validated by reintroducing the real bugs found during development — an exercise that caught two grading tests which proved nothing at all.

`TypeScript` · `WebGL2/GLSL` · `React 19` · `Vitest` · [Live](https://brianmojena.github.io/iris/)

### [Al Día · POS](https://github.com/brianmojena/al-dia-pos) — Full-stack, offline-first
Point-of-sale and inventory for small businesses on unreliable networks. A sale can't be lost because the connection drops: the sale and its sync job are written in a single SQLite transaction (transactional outbox), idempotency is enforced by a partial UNIQUE index rather than application logic, and the overselling race is resolved with a conditional UPDATE that lets the database arbitrate. The same React UI serves two transports — HTTP in the browser, IPC against local SQLite in Electron — with no offline branching in the interface, and an installable PWA extends the same guarantee to the web with a queue in IndexedDB. Six tests cover the money-critical paths on CI across Node 20 and 22, including eight concurrent sales against five units of stock asserting five `201`s, three `409`s and a final stock of exactly zero.

`React` · `Electron` · `Express` · `Turso/libSQL` · [Live](https://al-dia-pos.vercel.app)

### [Al Día · Dashboard](https://github.com/brianmojena/al-dia-dashboard) — Kotlin Multiplatform
Owner-facing dashboard for Android and iOS from a single codebase. The entire UI — screens, navigation and state — lives in `commonMain` with Compose Multiplatform; the only thing that drops to native is session storage, through a single `expect/actual` pair, and it goes in encrypted: AES/GCM under a non-exportable Android Keystore key, Keychain on iOS. The Ktor client returns a sealed result that separates the three failures that actually matter — no network, unparseable response, and server error with its status code — because confusing the first with the third is how an app tells you your password is wrong when the wifi dropped. Consumes the same API as the POS. Thirteen tests on CI.

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
**Graphics** — WebGL2, GLSL, colour management (Display P3)
**Data** — PostgreSQL, SQLite, Turso/libSQL, Supabase
**Other** — Python, Electron, AI/LLM integration

---

Open to roles and projects — remote or on-site.
