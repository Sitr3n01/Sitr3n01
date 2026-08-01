<div align="center">

# José Gilberto | Sitr3n01

**Desenvolvedor Full-Stack · Backend & Jogos · Brasília, DF**

[![GitHub](https://img.shields.io/badge/GitHub-Sitr3n01-181717?style=for-the-badge&logo=github)](https://github.com/Sitr3n01)
[![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://go.dev/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Unity](https://img.shields.io/badge/Unity-000000?style=for-the-badge&logo=unity&logoColor=white)](https://unity.com/)

<br>

**[Português](#português)** · **[English](#english)**

</div>

---

## Contato rápido / Quick Contact

- GitHub: [Sitr3n01](https://github.com/Sitr3n01)
- Discord: `sitr3n`
- Email: [zegilfarias@outlook.com](mailto:zegilfarias@outlook.com)

---

<a id="português"></a>

## Português

Desenvolvedor full-stack em Brasília. Mantenho um portal Django em produção para cliente real, publico uma aplicação desktop Windows em release Alpha e desenvolvo a camada de multiplayer de um jogo Unity incubado no Brasília Game Hub.

Meu trabalho se concentra em três frentes: sistemas web com Django e FastAPI, arquitetura de multiplayer em tempo real, e infraestrutura de IA local — servidores de inferência e ferramentas de desenvolvimento com integração de LLMs.

### Como eu trabalho

Prefiro construir sistemas completos a componentes isolados — da modelagem de dados ao deploy, passando por CI, testes e operação em produção. Os projetos abaixo cobrem deliberadamente problemas técnicos distintos: sincronização em tempo real, arquitetura de segurança e *threat modeling*, orquestração de múltiplos provedores de LLM, arquitetura local-first e deploy sob restrição de cliente real.

---

## Projetos

### [News Portal](https://github.com/Sitr3n01/news_portal) &nbsp; ![status](https://img.shields.io/badge/status-em%20produção-2ea44f)

Portal Django 5 **em produção para cliente real**, em manutenção evolutiva. Serve dois portais públicos e um painel administrativo a partir do mesmo codebase: site institucional e portal de notícias com artigos, categorias, tags, RSS, comentários e newsletter.

Arquitetura modular em **oito apps Django** — contas e papéis, institucional, vagas e candidaturas, contato, notícias, biblioteca de mídia, integrações sociais e utilitários compartilhados — sobre PostgreSQL 16.

Operação e segurança: sanitização de HTML enviado por usuários, validação de extensão e MIME em uploads, CI com Ruff e pytest, e deploy de produção aprovado por *environment* via tag.

**Tecnologias:** Python · Django 5 · PostgreSQL 16 · HTMX · Alpine.js · Django Unfold · Docker Compose · Nginx · Let's Encrypt · GitHub Actions

---

### [Local AI Server](https://github.com/Sitr3n01/IA_local_server) &nbsp; ![status](https://img.shields.io/badge/status-v2%20canary-orange)

Servidor de inferência **local-only** compatível com a API da OpenAI, escrito em Go. Permite que agentes de código como Codex, Claude Code e OpenCode rodem contra um modelo local sem que código-fonte, prompts ou credenciais saiam da máquina.

O projeto é fundamentalmente sobre superfície de segurança: todos os *listeners* são loopback literal, o *edge* remove o header `Authorization` do cliente antes de fazer proxy, três credenciais independentes vivem no Windows Credential Manager, e **não existe fallback para nuvem** — rota, modelo ou *encoding* desconhecido falha localmente em vez de buscar uma segunda opinião.

Nove binários Go: *data* e *control plane*, supervisor com contenção em Windows Job Object e *backoff* exponencial, painel de operador nativo Win32, e três servidores MCP — sendo o administrativo deliberadamente não registrado por padrão. **Razão teste/código de ~40%** (103 funções de teste sobre 8,7k linhas de Go), *threat model* completo, oito ADRs, e CI com Staticcheck, govulncheck, Gitleaks e geração de SBOM CycloneDX.

A promoção para produção está **intencionalmente bloqueada** por dois gates medidos — qualificação do modelo e envelope de memória — documentados abertamente no README em vez de contornados.

**Tecnologias:** Go 1.26 · llama.cpp · Model Context Protocol · PowerShell · Windows API (Job Objects, Credential Manager, ACLs, Win32) · AMD ROCm · GitHub Actions · CycloneDX

---

### [LUMINA](https://github.com/Sitr3n01/apartment_rental_manager) &nbsp; ![status](https://img.shields.io/badge/status-release%20Alpha-blue)

Aplicação desktop Windows *local-first* para gestão de aluguéis de curta temporada no Airbnb e Booking.com. Distribuída como instalador, roda inteiramente na máquina do usuário, sem servidores externos.

Sincronização automática de calendários iCal, detecção de conflitos entre plataformas, geração de documentos em DOCX, notificações por e-mail e Telegram, e dashboard de ocupação e receita.

Arquitetura em três camadas: shell Electron, frontend React 18 com Vite, e backend FastAPI com **cerca de 45 endpoints REST em 11 routers** sobre SQLAlchemy e SQLite.

Segurança implementada: JWT HS256 com *blacklist*, bcrypt, bloqueio de conta por tentativas, *rate limiting*, proteção CSRF, *security headers* e validação de entrada contra XSS, *path traversal* e SSTI. **35 testes** em pytest.

**Tecnologias:** Python · FastAPI · SQLAlchemy · React 18 · Vite · Electron 29 · SQLite · JWT · PyInstaller · electron-builder

---

### [ExoBeast](https://github.com/Matt040205/ExoBeast) &nbsp; ![status](https://img.shields.io/badge/status-em%20desenvolvimento-orange)

Tower-defense cooperativo em Unity 6 com multiplayer online para até 4 jogadores. Projeto incubado no Brasília Game Hub.

Atuo na arquitetura de multiplayer: integração com Epic Online Services, fluxo de lobby e sessão, sincronização via Unity Netcode, gerenciamento de credenciais de build e depuração de host/client.

**Tecnologias:** Unity 6 · C# · Netcode for GameObjects · Unity Transport · Epic Online Services · FMOD

---

### [Quality Review](https://github.com/Sitr3n01/quality_review) &nbsp; ![status](https://img.shields.io/badge/status-ferramenta-informational)

Quality gate determinístico de CI/CD para codebases desenvolvidas com assistência de IA.

Fluxos de *baseline/ratchet* para bloquear regressão de qualidade, checks determinísticos, análise estática e design de pipeline de revisão assistida.

**Tecnologias:** JavaScript · Node.js · GitHub Actions · análise estática · integração com Claude/Codex

---

## Stack

| Área | Tecnologias |
|---|---|
| **Backend** | Go, Python, Django 5, FastAPI, SQLAlchemy, Pydantic, REST API |
| **Sistemas** | Windows API (Job Objects, Credential Manager, ACLs, Win32), PowerShell, supervisão de processos |
| **Frontend** | React 18, Vite, TypeScript, JavaScript, HTMX, Alpine.js, HTML, CSS |
| **Desktop** | Electron, PyInstaller, electron-builder |
| **Jogos** | Unity 6, C#, Netcode for GameObjects, Unity Transport, Epic Online Services, FMOD |
| **Dados** | PostgreSQL, SQLite, ChromaDB |
| **DevOps** | Docker, Docker Compose, Nginx, GitHub Actions, Let's Encrypt, Linux, VPS, Git |
| **Qualidade** | pytest, Ruff, ESLint, Staticcheck, govulncheck, Gitleaks, SBOM, quality gates, CI/CD |
| **IA** | APIs de LLM, inferência local (llama.cpp), Model Context Protocol, orquestração multi-provedor, sistemas de memória, RAG |
| **Segurança** | Threat modeling, gestão de credenciais, hardening de ACL e firewall, menor privilégio |

---

## Frentes ativas

- Qualificação de modelo e soak de 72 h para promover o Local AI Server a produção
- Padrões avançados de sincronização multiplayer em Unity
- Elevação do LUMINA a Beta: cobertura de testes e CI/CD
- Manutenção evolutiva do portal em produção

---

## Formação

**Bacharelado em Jogos Digitais** — IESB, Brasília · conclusão prevista 2027

---

<div align="center">

**[⬆ Voltar ao topo](#josé-gilberto--sitr3n01)** · **[English ⬇](#english)**

</div>

---

<a id="english"></a>

## English

Full-stack developer based in Brasília, Brazil. I maintain a Django portal **running in production for a real client**, ship a Windows desktop application in Alpha release, and build the multiplayer layer of a Unity game incubated at Brasília Game Hub.

My work centres on three fronts: web systems with Django and FastAPI, real-time multiplayer architecture, and local AI infrastructure — inference servers and developer tooling with LLM integration.

### How I work

I prefer building complete systems over isolated components — from data modelling to deployment, including CI, testing and production operation. The projects below deliberately cover distinct technical problems: real-time synchronisation, security architecture and threat modelling, multi-provider LLM orchestration, local-first architecture, and deployment under real-client constraints.

---

## Projects

### [News Portal](https://github.com/Sitr3n01/news_portal) &nbsp; ![status](https://img.shields.io/badge/status-in%20production-2ea44f)

Django 5 portal **running in production for a real client**, under evolutionary maintenance. Serves two public portals and an admin panel from a single codebase: an institutional site and a news portal with articles, categories, tags, RSS, comments and newsletter.

Modular architecture across **eight Django apps** — accounts and roles, institutional, jobs and applications, contact, news, media library, social integrations and shared utilities — on PostgreSQL 16.

Operations and security: sanitisation of user-submitted HTML, extension and MIME validation on uploads, CI with Ruff and pytest, and production deployment approved via environment gate and tag.

**Technologies:** Python · Django 5 · PostgreSQL 16 · HTMX · Alpine.js · Django Unfold · Docker Compose · Nginx · Let's Encrypt · GitHub Actions

---

### [Local AI Server](https://github.com/Sitr3n01/IA_local_server) &nbsp; ![status](https://img.shields.io/badge/status-v2%20canary-orange)

Loopback-only, OpenAI-compatible inference server written in Go. It lets coding agents such as Codex, Claude Code and OpenCode run against a local model without source code, prompts or credentials ever leaving the machine.

The project is fundamentally about security surface: every listener is literal loopback, the edge strips the client `Authorization` header before proxying, three independent credentials live in Windows Credential Manager, and **there is no cloud fallback** — an unknown route, model or encoding fails locally rather than seeking a second opinion.

Nine Go binaries: data and control plane, a supervisor with Windows Job Object containment and exponential restart backoff, a native Win32 operator panel, and three MCP servers — the administrative one deliberately unregistered by default. **~40% test-to-source ratio** (103 test functions over 8.7k lines of Go), a full threat model, eight ADRs, and CI running Staticcheck, govulncheck, Gitleaks and CycloneDX SBOM generation.

Production promotion is **intentionally blocked** by two measured gates — model qualification and memory envelope — documented openly in the README rather than worked around.

**Technologies:** Go 1.26 · llama.cpp · Model Context Protocol · PowerShell · Windows API (Job Objects, Credential Manager, ACLs, Win32) · AMD ROCm · GitHub Actions · CycloneDX

---

### [LUMINA](https://github.com/Sitr3n01/apartment_rental_manager) &nbsp; ![status](https://img.shields.io/badge/status-Alpha%20release-blue)

Local-first Windows desktop application for managing short-term rentals across Airbnb and Booking.com. Shipped as an installer, runs entirely on the user's machine with no external servers.

Automatic iCal calendar synchronisation, cross-platform conflict detection, DOCX document generation, email and Telegram notifications, and an occupancy and revenue dashboard.

Three-layer architecture: Electron shell, React 18 frontend with Vite, and a FastAPI backend with **roughly 45 REST endpoints across 11 routers** over SQLAlchemy and SQLite.

Implemented security: JWT HS256 with server-side blacklist, bcrypt, account lockout, rate limiting, CSRF protection, security headers, and input validation against XSS, path traversal and SSTI. **35 tests** in pytest.

**Technologies:** Python · FastAPI · SQLAlchemy · React 18 · Vite · Electron 29 · SQLite · JWT · PyInstaller · electron-builder

---

### [ExoBeast](https://github.com/Matt040205/ExoBeast) &nbsp; ![status](https://img.shields.io/badge/status-in%20development-orange)

Cooperative tower-defense built in Unity 6 with online multiplayer for up to 4 players. Incubated at Brasília Game Hub.

I work on the multiplayer architecture: Epic Online Services integration, lobby and session flow, Unity Netcode synchronisation, build credential handling, and host/client debugging.

**Technologies:** Unity 6 · C# · Netcode for GameObjects · Unity Transport · Epic Online Services · FMOD

---

### [Quality Review](https://github.com/Sitr3n01/quality_review) &nbsp; ![status](https://img.shields.io/badge/status-tooling-informational)

Deterministic CI/CD quality gate for AI-assisted codebases.

Baseline/ratchet workflows to block quality regression, deterministic checks, static analysis, and assisted review pipeline design.

**Technologies:** JavaScript · Node.js · GitHub Actions · static analysis · Claude/Codex integration

---

## Stack

| Area | Technologies |
|---|---|
| **Backend** | Go, Python, Django 5, FastAPI, SQLAlchemy, Pydantic, REST API |
| **Systems** | Windows API (Job Objects, Credential Manager, ACLs, Win32), PowerShell, process supervision |
| **Frontend** | React 18, Vite, TypeScript, JavaScript, HTMX, Alpine.js, HTML, CSS |
| **Desktop** | Electron, PyInstaller, electron-builder |
| **Games** | Unity 6, C#, Netcode for GameObjects, Unity Transport, Epic Online Services, FMOD |
| **Data** | PostgreSQL, SQLite, ChromaDB |
| **DevOps** | Docker, Docker Compose, Nginx, GitHub Actions, Let's Encrypt, Linux, VPS, Git |
| **Quality** | pytest, Ruff, ESLint, Staticcheck, govulncheck, Gitleaks, SBOM, quality gates, CI/CD |
| **AI** | LLM APIs, local inference (llama.cpp), Model Context Protocol, multi-provider orchestration, memory systems, RAG |
| **Security** | Threat modelling, credential management, ACL and firewall hardening, least privilege |

---

## Active fronts

- Model qualification and 72-hour soak to promote the Local AI Server to production
- Advanced multiplayer synchronisation patterns in Unity
- Taking LUMINA to Beta: test coverage and CI/CD
- Evolutionary maintenance of the production portal

---

## Education

**BSc in Digital Games** — IESB, Brasília · expected 2027

---

<div align="center">

**[⬆ Back to top](#josé-gilberto--sitr3n01)** · **[Português ⬆](#português)**

</div>
