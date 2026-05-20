## patricznr1

Solo-Entwickler, Sembach bei Kaiserslautern.

### Stack

**Backend** — Python 3.11+ (FastAPI, SQLAlchemy 2.x async, Pydantic V2), Node.js / TypeScript
**Frontend Web** — Next.js, React, Tailwind
**Frontend Mobile** — Flutter 3.38, Dart 3.10, Riverpod, Dio
**Daten** — PostgreSQL 16 mit pgvector, Redis, Alembic
**AI** — Anthropic (Claude Opus/Sonnet/Haiku 4.5/4.7), OpenAI (GPT-5 + embeddings), Perplexity (Sonar)
**Infra** — Railway, Vercel, GitHub Actions
**IAP** — RevenueCat

### Aktive Projekte

**NEXUS** — Cross-Tool-Memory-System für LLM-Agents. Mehrstufige Memory-Hierarchie mit automatischer Konsolidierung. Hybrid-Retrieval auf PostgreSQL/pgvector mit Reranking-Layer. Drift-Monitoring auf Embedding-Ebene. Exponiert als MCP-Server (stdio + HTTP), gehärtet gegen Memory-Hijack auf Tool-Output-Ebene. Strukturiertes Wissen über separate Ontologie-Schicht.

**PairGuide** — DSGVO-konforme Paar-Mediations- und Coaching-App. FastAPI-Backend mit 165 Endpoints, Flutter-Frontend. Multi-Agent-Pipeline (Claude + GPT-5 + Sonar) mit Fallback-Router, Streaming-Output und Audit-Logger. Pseudonymisierung vor jedem LLM-Call, encryption-at-rest, vollständige DSGVO-Endpoint-Coverage (Art. 7, 15, 17, 20). mypy --strict, 200+ Tests inkl. Property-Based.

**Lerncoach** — KI-Lernassistent für strukturiertes Lernen. Node.js/TypeScript-Backend, Next.js-Frontend. SM-2 Spaced-Repetition-Algorithmus, Lerntyp-Profil-Adaption, mehrere Themen-Räume. 7-Schichten Defense-in-Depth (Rate-Limiting, Prompt-Injection-Detection, Output-Guard, Security-Event-Logging). Aktuell im Schultest-Betrieb.

**KI-Karriere-Assistent** — Multi-Agent-System für HR-/Karriere-Beratung. Fünf spezialisierte Agenten, Provider-agnostische LLM-Abstraktion, Output-Klassifikation und -Ranking.

### Arbeitsweise

Architektur und Spec werden in Claude (Desktop/Code) entworfen, Implementation delegiert an Windsurf und Claude Code via strukturierter Prompts mit Whitelist-basierten Datei-Scopes. GROUND_TRUTH.md pro Projekt als Single Source of Truth, Updates bei jeder Schema-/Endpoint-/Type-Änderung. AI-Act-Klassifizierung vor Code-Generierung.

### Konventionen

- Type-safe Python (mypy --strict, kein `any` in TS)
- Async-first im Backend
- Test-Coverage ≥80% (≥95% auf sicherheitskritischen Pfaden), pytest + Hypothesis, vitest
- snake_case in DB und Python, camelCase in TS, REST-Routen im Plural
- Konventionelle Commits, Feature-Branches, kein direkt-commit auf main

### Kontakt

[patric-zeller.de](https://patric-zeller.de) — [info@patric-zeller.de](mailto:info@patric-zeller.de)
