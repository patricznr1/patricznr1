## patricznr1

Solo-Entwickler, Sembach bei Kaiserslautern. Baue KI-Systeme für den Bereich menschlicher Interaktion — Therapie, Coaching, Bildung. Im Zentrum steht nicht das Sprachmodell, sondern die Architektur darum herum: wie ein Agent Erkenntnisse über Sitzungen hinweg speichert, zwischen situativer Beobachtung und validiertem Muster unterscheidet, gegen Halluzination und Manipulation gehärtet ist und eine Krise nicht übersieht.

DSGVO-Konformität und EU-AI-Act-Reife sind Architekturprinzip, keine nachträgliche Schicht.

### Stack

**Backend** — Python 3.11+ (FastAPI, SQLAlchemy 2.x async, Pydantic V2), Node.js / TypeScript
**Frontend Web** — Next.js, React, Tailwind
**Frontend Mobile** — Flutter 3.38, Dart 3.10, Riverpod, Dio
**Daten** — PostgreSQL 16 mit pgvector, QuestDB (Zeitreihen), Redis, Alembic
**AI** — Anthropic (Claude Opus/Sonnet/Haiku 4.5/4.7), OpenAI (GPT-5 + embeddings), Perplexity (Sonar)
**Infra** — Railway, Vercel, GitHub Actions
**IAP** — RevenueCat

### Aktive Projekte

**NEXUS** — Cross-Tool-Memory-System für LLM-Agents. Drei-Schichten-Gedächtnis mit automatischer Konsolidierung über die Tiers hinweg. Hybrid-Retrieval auf PostgreSQL/pgvector mit Reranking-Layer. Drift-Monitoring auf Embedding-Ebene. Exponiert als MCP-Server (stdio + HTTP), gehärtet gegen Memory-Hijack auf Tool-Output-Ebene. Strukturiertes Wissen über separate Ontologie-Schicht.

**PairGuide** — DSGVO-konforme Paar-Mediations- und Coaching-App. FastAPI-Backend mit 165 Endpoints, Flutter-Frontend. Mehrstufige Verifikations-Pipeline für therapeutische KI-Antworten mit Multi-Provider-Fallback, Streaming-Output und Audit-Logger. Pseudonymisierung vor jedem LLM-Call, encryption-at-rest, vollständige DSGVO-Endpoint-Coverage (Art. 7, 15, 17, 20). mypy --strict, 200+ Tests inkl. Property-Based.

**Lerncoach** — KI-Lernassistent für strukturiertes Lernen. Node.js/TypeScript-Backend, Next.js-Frontend. SM-2 Spaced-Repetition-Algorithmus, Lerntyp-Profil-Adaption, mehrere Themen-Räume. 7-Schichten Defense-in-Depth (Rate-Limiting, Prompt-Injection-Detection, Output-Guard, Security-Event-Logging). Aktuell im Schultest-Betrieb.

**KI-Karriere-Assistent** — Multi-Agent-System für HR-/Karriere-Beratung. Fünf spezialisierte Agenten, Provider-agnostische LLM-Abstraktion, Output-Klassifikation und -Ranking.

**GoldPilot** — Entscheidungsunterstützung für Daytrading mit Knock-Out-Derivaten auf Gold. FastAPI-Backend, Next.js-Frontend, duale Datenbank-Strategie (Zeitreihen + relational), Event-Bus über Redis Streams. Multi-Timeframe-Analyse mit Voting über mehrere technische Indikatoren, separater Risiko-Layer mit Veto-Recht, eigene Derivate-Übersetzungsschicht inklusive KO-Puffer-Logik. Phase 1 MVP in Entwicklung. Keine autonomen Handelsentscheidungen, keine Anlageberatung.

**prompt-build-engine** — Meta-Werkzeug für mehrstufiges Prompt-Engineering und Projekt-Setup-Generierung. Next.js + TypeScript-Backend mit Drizzle ORM. Bundles für Boilerplate-Erzeugung (Agent-/Skill-Konfigurationen pro Sprache) und für Compliance-/Security-Templates (OWASP, DSGVO, EU AI Act, NIST CSF). Aktiv in Entwicklung.

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
