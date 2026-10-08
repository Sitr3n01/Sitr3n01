<div align="center">

# José Gilberto

**Full-stack developer · Django & Wagtail in production · Go & local AI infrastructure · Unity multiplayer**

Brasília, Brazil · [zegilfarias@outlook.com](mailto:zegilfarias@outlook.com)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![Wagtail](https://img.shields.io/badge/Wagtail-43B1B0?style=for-the-badge&logo=wagtail&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![Unity](https://img.shields.io/badge/Unity-000000?style=for-the-badge&logo=unity&logoColor=white)

**English** · [Português](https://github.com/Sitr3n01/Sitr3n01/blob/main/README.pt-BR.md)

</div>

I build complete systems and run them in production: data model, interface, CI/CD and the server underneath. Right now that means a Django + Wagtail platform that runs two production websites for a real client, and a loopback-only inference server in Go that lets coding agents work against a local model without source code leaving the machine. I also wrote the online multiplayer of a Unity game incubated at Brasília Game Hub.

## Featured projects

<p align="center">
  <a href="https://github.com/Sitr3n01/news_portal"><img src="https://raw.githubusercontent.com/Sitr3n01/news_portal/master/docs/images/social-preview.jpg" width="48%" alt="news_portal: one Django + Wagtail codebase behind two production sites and their newsroom"></a>
  <a href="https://github.com/Sitr3n01/local-ai-provider"><img src="https://raw.githubusercontent.com/Sitr3n01/local-ai-provider/main/docs/images/social-preview.png" width="48%" alt="Local AI Provider: a loopback-only, OpenAI-compatible inference server for coding agents, next to its live monitor"></a>
</p>

### [news_portal](https://github.com/Sitr3n01/news_portal) &nbsp; ![status: in production](https://img.shields.io/badge/status-in%20production-2ea44f)

One Django 5.2 + Wagtail 7.4 codebase behind two production websites for a real client and the newsroom panel their team uses every day: [Komuniki](https://komuniki.com.br), the editorial site of a communication and arts school, and [Blog da Kelly](https://kellyfarias.com.br/news/), a news portal. I built it and operate it end to end; it has been live since June 2026.

- **Motion that respects the reader.** A WebGL hero in three.js with custom shaders and GSAP text reveals. All of it backs off under `prefers-reduced-motion`.
- **A newsroom the client's team uses daily.** The Django admin (Unfold) and the Wagtail admin merged into one panel, with an editorial workflow: reporters write, editors approve, and scheduling only publishes approved revisions.
- **Audited security.** A five-category audit found 7 issues (3 high), all fixed with regression tests. Nonce-based CSP, extension and MIME checks on uploads, Google sign-in, django-axes and Cloudflare Turnstile.
- **Operations on a small VPS.** Docker Compose behind Cloudflare on 1 vCPU and 4 GB. Deploys are pull-based: the server fetches an approved tag, so CI holds no server credentials. I found and fixed a deploy stuck retrying for two months and Docker images that grew quadratically with database dumps, which took the build cache from 23.95 GB to 442 MB.
- **Quality gates.** 823 tests, branch coverage enforced at 82% (83.5% today), CodeQL, pip-audit, secret scanning and a protected `master`.

**Technologies:** Python · Django · Wagtail · PostgreSQL · HTMX · Alpine.js · Tailwind CSS · three.js · GSAP · Docker · Nginx · GitHub Actions

### [Local AI Provider](https://github.com/Sitr3n01/local-ai-provider) &nbsp; ![status: v2 canary](https://img.shields.io/badge/status-v2%20canary-orange)

A loopback-only, OpenAI-compatible inference server in Go that lets coding agents such as Codex, Claude Code and OpenCode run against a local model, so source code, prompts and credentials never leave the machine. It is an inference and admission-control plane in front of llama.cpp, plus the Windows plumbing to run it as a supervised service.

- **Security invariants enforced by tests.** Every listener is literal loopback, the client's `Authorization` header never reaches the model, there is no cloud fallback, and logs carry metadata only. An unknown route, model or encoding fails closed.
- **Measured, with linked evidence.** 18.2 ms p95 edge overhead against a 50 ms gate, 120/120 long-context recall up to 240k tokens, 50.4 tok/s decode with 120k tokens in context, and a real Codex session that fixed a failing Go test in 114 s.
- **Engineering.** 11 Go executables (edge, a supervisor with Windows Job Object containment, a tray app, a browser monitor and MCP servers), 728 Go tests and subtests, a threat model and 22 ADRs. CI runs Staticcheck, govulncheck, the race detector, Gitleaks over the full history and CodeQL; releases ship with an SBOM and SHA-256 sums.
- **Honest status.** Models move through a promotion gate, and production stays blocked until the last evidence is in. When the v1 prototype leaked a credential into local logs, I documented it in an [open incident report](https://github.com/Sitr3n01/local-ai-provider/blob/main/incident-reports/2026-07-20-panel-zstd-credential-exposure.md) and made metadata-only logging a tested invariant.

**Technologies:** Go · llama.cpp · Model Context Protocol · Windows API · PowerShell · AMD ROCm · GitHub Actions · CodeQL

## Game development

Student team projects in Unity 6.

### [ExoBeast](https://github.com/Matt040205/ExoBeast) &nbsp; ![status: in development](https://img.shields.io/badge/status-in%20development-orange)

Co-op tower defense for 1–4 players online, incubated at Brasília Game Hub. I own the multiplayer end to end (about 9.1k lines of C#): Epic Online Services login and lobbies, Unity Relay, and the Netcode for GameObjects session flow, with the host as the authority for gameplay state. I also did the network optimizations, an eight-sprint refactor of the lobby under a ratchet quality gate, the FMOD integration, two editor tools (Exo Config and a Blender-to-Unity bridge) and about 140 NUnit tests.

### [Loopia](https://github.com/Matt040205/Loopia) &nbsp; ![status: prototype](https://img.shields.io/badge/status-prototype-orange)

A loop-based strategy prototype: the hero runs a procedurally generated hex ring on his own while the player shapes the world with island cards. I wrote all the gameplay code of the current version (`Assets/Scripts/Hex`, about 5.6k lines of C#): a ring generator that keeps a valid cycle as it gets irregular, a NavMesh baked at runtime with jump links between islands, data-driven cards that simulate a full lap before accepting a placement, auto-combat, enemy AI and a JSON save. Credits are in its [README](https://github.com/Matt040205/Loopia#team).

## Other projects

- **[Quality Review](https://github.com/Sitr3n01/quality_review):** a deterministic CI/CD quality gate for AI-assisted codebases, with skills for Claude Code and Codex. Baseline ratchets let metrics improve and block regressions; AI only explains the verdict. The same approach guided the ExoBeast lobby refactor.
- **[LUMINA](https://github.com/Sitr3n01/apartment_rental_manager):** a local-first Windows desktop app for short-term rental hosts, with iCal sync across Airbnb and Booking.com, conflict detection, documents and notifications. Electron, React and FastAPI; Alpha release.

## How I work

I work with AI coding agents (Claude Code and Codex) as pair programmers. I set the direction and own the decisions: scope, architecture, trust boundaries and what counts as done. Every change, whoever drafted it, passes the same gates: required CI checks, tests, static analysis, secret scanning and, where it matters, measured evidence. The threat model, ADRs and audit reports in these repositories are where those decisions are written down.

## Stack

| Area | Technologies |
|---|---|
| **Back end** | Python, Django, Wagtail, FastAPI, SQLAlchemy, Pydantic, Go, REST APIs |
| **Front end** | HTMX, Alpine.js, Tailwind CSS, three.js (WebGL), GSAP, React, Vite, TypeScript, JavaScript |
| **Data** | PostgreSQL, SQLite |
| **DevOps** | Docker Compose, Nginx, Gunicorn, Cloudflare, Sentry, Let's Encrypt, Linux VPS, GitHub Actions, Git |
| **Quality** | pytest, Ruff, ESLint, Staticcheck, govulncheck, CodeQL, Gitleaks, SBOM, quality gates |
| **Security** | Threat modeling, CSP, OAuth, credential management, ACL and firewall hardening, least privilege |
| **Systems** | Windows API (Job Objects, Credential Manager, ACLs, named pipes), PowerShell, process supervision |
| **AI** | Local inference (llama.cpp), OpenAI-compatible APIs, Model Context Protocol, LLM APIs, AI coding agents |
| **Games** | Unity 6, C#, Netcode for GameObjects, Epic Online Services, Unity Relay, FMOD, NUnit, Blender add-on development (Python) |
| **Desktop** | Electron, PyInstaller, electron-builder |

## Now

- Qualifying Local AI Provider for production, starting with the physical revalidation of its long-context profile.
- news_portal: running the test suite against PostgreSQL in CI and migrating to Wagtail 8.
- ExoBeast: validating online sessions over the public internet, behind NAT.

## Education

**BSc in Digital Games**, IESB, Brasília (expected 2027)

## Contact

Email: [zegilfarias@outlook.com](mailto:zegilfarias@outlook.com) · Discord: `sitr3n`
