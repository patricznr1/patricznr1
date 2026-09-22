Patric Zeller — AI Architect & Developer

Gedächtnisarchitektur für KI-Systeme. Foundation Models bringen Fachwissen. Ich baue das, was Erfahrung daraus macht.

Im Zentrum steht nicht das Sprachmodell, sondern die Schicht daneben: wie ein System Entscheidungen, Begründungen und verworfene Wege über Sitzungen und über Modellwechsel hinweg hält, wie es verdichtet, zurückstellt und mit Grund vergisst. Siebzehn Jahre Steuerungs- und Sicherheitstechnik davor — DSGVO- und EU-AI-Act-Anforderungen sind bei mir Architekturentscheidung vor dem ersten Commit, keine nachträgliche Schicht.

patric-zeller.de · LinkedIn · info@patric-zeller.de

NEXUS — Gedächtnis als Dienst

Eine vom Modell getrennte Identitäts- und Gedächtnisschicht für KI-Assistenten. Eine neue Sitzung beginnt nicht mit „Was kann ich für dich tun?", sondern mit „Wo waren wir?". Anbindung über MCP (stdio + HTTP), API oder SDK; eigene Instanz je Mandant, Betrieb in der EU, im Haus oder ohne Netzanbindung. Pilotphase seit August 2026.

Architektur — Drei Ebenen mit unterschiedlicher Haltbarkeit (Kurzzeit, Mittelschicht, Langzeit) und automatischer Konsolidierung in Hintergrundläufen, nicht beim Schreiben. Hybrid-Retrieval auf PostgreSQL/pgvector mit Reranking. Nach außen liefert das System keinen Trefferstapel, sondern einen fertigen Kontextblock: Zeitkopf, wörtlicher Gesprächsverlauf, verdichtete Vorgeschichte, einschlägiges Langzeitwissen — vorausschauend bereits nach dem vorigen Gesprächszug gebaut.

Was im Gedächtnismodell selbst steckt, nicht als Anbau daneben:

Zustände je Eintrag — Ebene, Gewicht, Reifebedingung; ändern sich mit der Zeit von selbst
Ablösung — eine Korrektur entwertet den älteren Eintrag, der als Beleg lesbar bleibt
Zwei Zeitachsen mit Stichtag (Gültigkeit und Erfassung) — beantwortbar ist, was an einem beliebigen Tag gegolten hätte
Vergessen mit vermerktem Grund, kein Aufräumskript
Formales Wissensnetz nach W3C-Standard, lesend abfragbar; Abgeleitetes bleibt als abgeleitet erkennbar und wird nie erneut als Quelle eingespeist
Erinnerungen sind Daten, nie Anweisungen — jeder Rückgabeinhalt ist als Datenblock ausgezeichnet und strukturell von Steuerinformation getrennt

Bewusster Verzicht: Widersprüche erkennt das System nicht selbsttätig. Ähnlichkeit ist kein Widerspruch, und ein falscher Treffer würde echtes Wissen entwerten.

Messung (08/2026, 150 Fragen, Bewerter vorab kalibriert, κ 0,937): richtige Stelle in 96,0 % gefunden, davon 77,3 % auf Rang 1 · Beschaffung 0,4 s je Abfrage (Vergleichsarm 4,8 s) · fertiger Kontextblock 112 ms · 0 Fremdtreffer über 80 geprüfte Mandantenpaare. Antwortgüte daraus 44,7 % gegen 46,7 % im mitgemessenen Vergleichsarm — Unterschied nicht belegbar, Obergrenze des Aufbaus bei 64,7 %. Verloren wird nach dem Finden, und das steht so auf der Seite. Messaufbau, Grenzen und zwölf als überholt gekennzeichnete frühere Werte: patric-zeller.de

MBRC — Memory Benchmark Reporting Checklist, Fassung 1.0, CC BY 4.0. Berichtsstandard nach dem Vorbild medizinischer Reporting-Guidelines: nicht wie man misst, sondern was dabeistehen muss, damit eine Zahl etwas bedeutet. Zehn Regeln, vier Urteile, maschinenlesbares Ergebnisformular. Offen für Kommentare.

Plattformen — drei Domänen, ein Substrat
		
FOREMAN	Industrielle Produktion	Ereignisketten vor einem Ausfall, Prozessdrift, Komponentenlebensdauer, Wirksamkeit von Eingriffen. Erklärt, greift nie ein. AI-Act-Einstufung lag vor dem ersten Commit. in Entwicklung, öffentliches Repository
LEDGER	Finanz- und Geschäftsvorgänge	Die Schicht über dem ERP: warum eine Position so entschieden wurde, Frühwarnung mit benanntem Treiber, Stichtagsfragen zum Abschluss. Kein System of Record; Vergessen abschaltbar. in Konzeption
DOSSIER	Auftragsbezogene Fertigung	Projektgedächtnis als zeitlich geschichtete Kette aus Vorgaben, Klärungen, Freigaben und Änderungen — für Reklamation, Requalifikation, Audit und nach jedem Personalwechsel. Betrieb im Haus als Standardannahme, keine Bewertung von Personen. in Konzeption, erster Anwender im Gespräch

Jede Plattform auf demselben Gedächtnis, mit eigenem Fachmodell und eigenem Rechtsrahmen. Was je Domäne wirklich neu entsteht, ist das Fachmodell, die Anbindung an Bestandssysteme und die Zuordnung der Aufbewahrungsfristen.

Systeme

Anwendungen, aus denen die Architektur hervorgegangen ist. Reifegrad steht dran.

KI-Karriere-Assistent — Profilanalyse, Stellenabgleich, Gesprächstraining mit Audio-Auswertung. Multi-Agent-System, provider-agnostische LLM-Abstraktion. Externes Sicherheitsaudit bestanden, DSGVO-konform ausgelegt. Next.js · Express · PostgreSQL — in Produktion

Lerncoach — Adaptive Lernplattform mit gestreckten Wiederholungsintervallen (SM-2). Der Lerntyp wird im Gespräch erhoben, nicht per Fragebogen. Siebenschichtige Defense-in-Depth: Rate-Limiting, Prompt-Injection-Erkennung, Output-Guard, Security-Event-Logging. Next.js · Node/TypeScript · Python — in Produktion

Prompt Build Engine — Optimierungspipeline für Modell-Prompts über mehrere Anbieter hinweg, dazu Bundles für Boilerplate-Erzeugung und Compliance-Templates (OWASP, DSGVO, EU AI Act, NIST CSF). Next.js · TypeScript · Drizzle — in Produktion

PairGuide — Mediation und Co-Parenting mit Gesprächsgedächtnis über Monate. Mehrstufige Agenten-Pipeline mit getrenntem Krisenerkennungs-Pfad, Multi-Provider-Fallback, Pseudonymisierung vor jedem LLM-Call, Encryption-at-Rest, vollständige DSGVO-Endpoint-Coverage (Art. 7, 15, 17, 20). Flutter · Python · FastAPI — Beta

GoldPilot — Signalsystem für Gold-Derivate. Vier voneinander unabhängige Säulen mit Voting, separater Risiko-Layer mit Veto-Recht, walk-forward-validiert. Keine autonomen Handelsentscheidungen, keine Anlageberatung. Python · Zeitreihen — Prototyp

PLANWERK & AEOS — der Rahmen, in dem gebaut wird

Ein Agent baut die Software. AEOS hält den Rahmen. Zweck ist das Entstehen von Software, nicht das Prüfen fremder Repositories.

PLANWERK ist die Projektierung davor — der Weg P0–P5 mit Toren G0–G4, die ich selbst passiere:

Absicht und Schadensklasse zuerst. K0–K3 wird vor dem Entwurf festgelegt und bestimmt Prüftiefe und Aufwand, nicht umgekehrt. ABSICHT.md mit Read-back gegen das, was ich gemeint habe.
Anforderungen als EARS-Sätze in requirements.yaml, klassifiziert nach F/C/Q/S/D, mit STPA-Kette und automatischen Validierungssonden.
GROUND_TRUTH.md als Verzeichnis des tatsächlichen Zustands, nicht als Absichtserklärung.
Blindprüfung in einer Sitzung, die den Entstehungsweg nicht kennt — mit gesäten Fehlern und Befund-Register. Eine Person kann nicht blind gegen sich selbst prüfen; deshalb kennt der Prüfer die Autor-Begründung nicht.
Rechts- und Normenbetrachtung in sechs Stufen mit Eskalationsliste, vor dem Entwurf.

AEOS ist der Rahmen, in dem der Agent danach baut — und er begrenzt das Modell hart:

Die Verfahren liegen als Ontologie vor: welcher Aufgabentyp welche Schritte hat, welche Regel und welche Prüfung je Schritt gilt. Der Agent bekommt sie vor dem Schreiben, nicht danach.
Anforderungen, Spezifikation und Tests sind schreibgeschützt. Widerspricht ein Test der Spezifikation, hält der Agent an und meldet. Das ist die eine Regel ohne Ausweg — Frontier-Modelle schreiben bei Spec/Test-Konflikt in 49–54 % der Fälle den Test um (ImpossibleBench), und keine Prompt-Formulierung stellt das ab.
Gesperrt statt empfohlen: Pfade, Befehle und Geheimnisse, die der Agent nicht anfassen darf, sind blockiert. Blockieren statt warnen, mit Warnbudget — eine Warnung, die man wegklicken kann, ist keine.
Ein Befund zählt erst, wenn er reproduziert ist — Test rot vor dem Fix. Ein Test zählt erst, wenn er einen absichtlich eingebauten Fehler findet. Zwei-Status je Anforderung: implementiert und verifiziert, und verifiziert wird nur, wozu ein Test existiert, der rot würde.
Belegstatus je Aussage — gemessen / belegt / geschätzt / konzipiert. Keine Aussage ohne Etikett.
Rückführbarkeit über aeos trace: Matrix aus Anforderung, Datei und Test, meldet Waisen in beide Richtungen als Fehler.
Aktualitätsregister für Fremdbibliotheken — das Bibliothekswissen eines Modells ist im Zweifel ein Jahr alt (GitChameleon: 48–51 %).
Jede Sitzung hat Kontrollpunkte und ein Kontextbudget. Was sich nicht prüfen lässt, wird nicht durchgelassen.
Drei Dinge entscheidet der Agent nie: was gebaut wird, welche Schadensklasse gilt und wann ein Tor bestanden ist.

AEOS erfüllt keinen Sicherheitsstandard und beansprucht keinen. Es überträgt Verfahrensprinzipien aus Domänen, in denen Nachweisführung selbstverständlich ist, und macht sie an einem Agenten messbar. Der Anspruch ist Verfahrensdisziplin, nicht Zertifikat. Spezifikation steht, in Anwendung in den eigenen Projekten.

Stack

Backend — Python 3.11+ (FastAPI, SQLAlchemy 2.x async, Pydantic V2), Node.js / TypeScript Frontend — Next.js, React, Tailwind · Flutter, Dart, Riverpod, Dio Daten — PostgreSQL 16 mit pgvector, QuestDB (Zeitreihen), Redis, Alembic Wissensrepräsentation — RDF/OWL-Ontologie, SPARQL AI — Anthropic Claude, OpenAI (Completion + Embeddings), Perplexity Sonar Infra — Railway, Vercel, GitHub Actions

Arbeitsweise

Ich orchestriere. Architektur und Entscheidungen entstehen im Gespräch mit einem Modell, das mir widerspricht; Implementierung und Fehlersuche laufen über spezialisierte Werkzeuge gegen eine festgeschriebene Spezifikation.

PLANWERK ist die Projektierung davor: Absicht, Schadensklasse, Anforderungen, Entwurf, Rechts- und Sicherheitsbetrachtung — mit Toren und einer Prüfung in einer Sitzung, die den Entstehungsweg nicht kennt. AEOS ist der Rahmen, in dem ein Agent danach baut, und er begrenzt das Modell hart: Die Verfahren liegen als Ontologie vor und der Agent bekommt sie vor dem Schreiben. Anforderungen, Spezifikation und Tests sind für ihn schreibgeschützt; widerspricht ein Test der Spezifikation, hält er an und meldet. Verbotene Pfade, Befehle und Geheimnisse werden gesperrt, nicht empfohlen. Ein Befund zählt erst, wenn er reproduziert ist — Test rot vor dem Fix — und ein Test zählt erst, wenn er einen absichtlich eingebauten Fehler findet. Drei Dinge entscheidet der Agent nie: was gebaut wird, welche Schadensklasse gilt und wann ein Tor bestanden ist.

GROUND_TRUTH.md je Projekt als Single Source of Truth, Update bei jeder Schema-, Endpoint- oder Typänderung. AI-Act-Klassifizierung vor der Code-Generierung.

Konventionen
Type-safe Python (mypy --strict), kein any in TypeScript
Async-first im Backend
Testabdeckung ≥ 80 %, ≥ 95 % auf sicherheitskritischen Pfaden; pytest + Hypothesis, vitest
snake_case in DB und Python, camelCase in TS, REST-Routen im Plural
Konventionelle Commits, Feature-Branches, kein Direkt-Commit auf main
Hintergrund

Kein Informatik-Abschluss. Siebzehn Jahre Steuerungs- und Automatisierungstechnik für Anlagen, auf denen Menschen stehen: SPS-Programmierung, sicherheitsgerichtete Komponenten, Personen- und Maschinenschutz — Schwerpunkt Steuerungen, Retrofit und Energiesparsysteme für Fahrtreppen. Dazu Werkstatt- und Projektleitung im Sondermaschinenbau und die Geschäftsführung eines TGA-Betriebs mit zwölf Mitarbeitern.

In der Personenbeförderung bestimmt die Sicherheitsbetrachtung die Konstruktion, nicht umgekehrt. Die Sicherheitskette wird getrennt ausgeführt, getrennt geprüft, getrennt abgenommen — alles andere läuft nur, solange sie es erlaubt. Retrofit ist Integration in Gewachsenes mit Abnahmeprotokoll: ein System verstehen, das man nicht gebaut hat, es nicht dauerhaft anhalten dürfen, und am Ende steht eine Prüfung, die man besteht oder nicht. Das ist derselbe Job wie die Anbindung an eine gewachsene Systemlandschaft, nur mit härterem Termin.

Kontakt

patric-zeller.de — info@patric-zeller.de — LinkedIn

Fundstellen auf Anfrage, technische Tiefe nach Geheimhaltungsvereinbarung.
