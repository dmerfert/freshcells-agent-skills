---
name: marketing-hub-mcp
description: >
  Nutzungsanweisungen für den freshcells Marketing Hub MCP.
  Trigger: freshcells, TravelSandbox, freshMS, Fusion, Quickstart, mightyC,
  CampaignMS, Booking Engine, IBE, MACH, CoDe,
  Marketing-Content erstellen, Copy schreiben, texten, formulieren,
  recherchieren, Content prüfen, Content Check,
  Brand Voice, Tonalität, Terminologie, Ansprache, Brand Guidelines,
  LinkedIn Post, Social Media, Newsletter, Blogpost, Pressemeldung,
  E-Mail, Cold Email, Follow-up, Angebot, Präsentation,
  Pitch-Deck, Pitch, Demo, Erstgespräch,
  Sales-Material, Sales-Argumente, Einwand, ROI, TCO, Referenzen,
  Case Study, Whitepaper, Landing Page,
  Kundenreferenzen, Kundenstimmen, USPs, Wettbewerber,
  Design-Briefing, Design Tokens, Design Guidelines,
  Logo, Asset, Farben, Schriftart, Font, Typografie, Banner,
  Reiseveranstalter, Touristik
---

# freshcells Marketing Hub MCP

Der Marketing Hub MCP bietet 15 Tools für den Zugriff auf die freshcells Wissensbasis: 120+ Dokumente (Glossar, Whitepaper, Playbook, Design Guidelines, Skills, Website-Content), Brand Voice (DE/EN), Design-Tokens, 68 Brand-Assets. Verbunden über OAuth 2.1 (nur @freshcells.de).

## Installation

| Was | Befehl | Inhalt |
|-----|--------|--------|
| **freshcells MCP + Skills** | `claude plugin add dmerfert/freshcells-agent-skills` | MCP-Verbindung + dieser Skill. MCP-Tools heißen `freshcells-marketing`. |
| **Marketing Skills** | `claude install-plugin github:coreyhaines31/marketingskills` | 32 Marketing-Skills (`/copywriting`, `/cold-email`, `/social-content` etc.) |
| **Figma** | `claude plugin install figma@claude-plugins-official` | Offizieller Figma MCP für Design-Umsetzung |

Wenn `freshcells-marketing` MCP-Tools nicht verfügbar sind → Plugin noch nicht installiert. Das freshcells Plugin liefert automatisch die MCP-Verbindung.

## Globale Regeln

Diese Regeln gelten bei **jedem** Content-Output:

1. **`get_brand_voice("de")` IMMER laden** bevor Marketing-Content erstellt wird
2. **TravelSandbox®** und **freshMS®** immer mit ® — bei jeder Nennung
3. **freshcells** immer kleingeschrieben, auch am Satzanfang
4. **Plural-Ihr** als Anrede (nicht Du, nicht Sie) — außer in Angeboten/Verträgen
5. **Jede Behauptung belegen** — Kundenzitat, KPI oder Referenz aus dem Glossar
6. **Evidenz-Kadenz** in Langform-Content: max. 2 Absätze ohne Beleg
7. **Nach Content-Erstellung:** Brand Voice Checkliste prüfen (Abschnitt 10 in der Brand Voice)
8. **Verbotene Begriffe:** „billig", „Marktführer" (für freshcells), „garantiert", „state-of-the-art", „cutting-edge", „disruptiv"

## Workflows

### 1. LinkedIn Post

→ Kombiniere mit: `/social-content`

1. `get_brand_voice("de")` — Tonalität laden
2. `search_vault("[Thema]")` — relevante Inhalte finden
3. `get_file("[get_file_path aus Schritt 2]")` — Dateien mit Belegen laden
4. `get_glossar_overview(task: "linkedin-post")` — empfohlene Dateien + Workflow

MCP liefert Fakten, Zitate, KPIs → `/social-content` formatiert als LinkedIn-Post.

### 2. Sales-E-Mail / Cold Outreach

→ Kombiniere mit: `/cold-email`

1. `get_brand_voice("de")` — Tonalität (Cold E-Mail: Mittel Formalität, Hoch Energie)
2. `get_glossar_overview(task: "cold-email")` — empfohlene Dateien
3. `get_file("Glossar/10-sales-snippets.md")` — Copy-Paste-Bausteine
4. `get_file("Glossar/07-kundenreferenzen.md")` — Referenz für Hook
5. Optional: `search_vault("[Branche des Prospects]")` — branchenspezifische Referenzen

### 3. Pitch-Deck vorbereiten

→ Kombiniere mit: `/sales-enablement`

1. `get_brand_voice("de")` — Terminologie
2. `get_glossar_overview(task: "pitch-deck")` — empfohlene Dateien
3. `get_file("Glossar/15-pitch-deck-textbausteine.md")` — 13 Slides + Speaker Notes
4. `get_file("Glossar/09-sales-argumente.md")` — 11 belegte Argumente
5. `get_design_guide()` + `get_design_tokens("colors")` — Brand-Farben für Slides

### 4. Pressemeldung

→ Kombiniere mit: `/copywriting`

1. `get_brand_voice("de")` — Tonalität (Pressemeldung: Hoch/Mittel/Mittel)
2. `search_vault("[Kundenname oder Thema]")` — Referenzdaten
3. `get_file("Glossar/08-kundenstimmen.md")` — Kundenzitat für die PM
4. `get_file("Glossar/07-kundenreferenzen.md")` — Projektdetails, KPIs
5. Optional: `get_asset("[Kundenlogo]")` — Logo-URL für die PM

### 5. Design-Briefing / UI-Arbeit

→ Kombiniere mit: `/frontend-design`, `/ui-ux-pro-max`
→ Plugin: Figma (`figma@claude-plugins-official`)

1. `get_design_guide()` — Index mit Core-Tokens + AI Agent Rules
2. Parallel: `get_design_guide(page: "colors-extended")` + `get_design_guide(page: "typography")`
3. `get_design_tokens("all")` — maschinenlesbare Token-Werte für Code
4. `list_assets(type: "svg")` — verfügbare SVGs
5. `get_asset("[Name]")` — spezifisches Logo/Asset laden

Regel: Alle Farben aus Brand-Palette. Keine Hex-Werte erfinden. Tailwind-Token-Klassen nutzen (`bg-primary-100` statt `bg-[#04589a]`).

### 6. Case Study

→ Kombiniere mit: `/copywriting`

1. `get_brand_voice("de")` — Tonalität (Website/Case Study)
2. `get_glossar_overview(task: "case-study")` — empfohlene Dateien
3. `get_file("Glossar/07-kundenreferenzen.md")` — Projektdetails zum Kunden
4. `get_file("Glossar/08-kundenstimmen.md")` — Kundenzitat
5. `get_file("Glossar/06-erfolgsfaktoren.md")` — KPIs und Projekt-Metriken
6. Optional: `search_vault("[Kundenname]")` — Pressemeldungen, News

Struktur: Kundenname → Herausforderung → TravelSandbox®-Lösung → min. 1 KPI → Kundenzitat.

### 7. Content Check

→ Kombiniere mit: `/copy-editing`

Prüft bestehenden Content gegen die freshcells Wissensbasis:

1. `get_brand_voice("de")` — Terminologie + Checkliste
2. `get_file("Glossar/02-usps-nutzenversprechen.md")` — USPs abgleichen
3. `get_file("Glossar/09-sales-argumente.md")` — Sales-Botschaften prüfen
4. `get_file("Glossar/07-kundenreferenzen.md")` — Referenzen auf Aktualität prüfen
5. Optional: `get_file("Glossar/08-kundenstimmen.md")` — Zitate verifizieren

Prüfpunkte: Produktnamen korrekt (®)? KPIs aktuell? Referenzen aktuell? Belege vorhanden? Verbotene Begriffe?

### 8. Whitepaper / Langform-Content

→ Kombiniere mit: `/copywriting`, `/whitepaper-qa`

1. `get_brand_voice("de")` — Tonalität (Whitepaper: Mittel-Hoch, evidenzbasiert)
2. `get_glossar_overview(task: "whitepaper")` — empfohlene Dateien
3. Parallel: mehrere `get_file()` für relevante Glossar-Artikel
4. `search_vault("[Thema]", tag: "whitepaper")` — Whitepaper-Dokumentation
5. Optional: `get_file("Whitepaper/whitepaper-guidelines-freshcells.md")` — Personas, Strukturen

Evidenz-Kadenz: Max. 2 Absätze ohne Beleg. Spätestens im dritten Absatz: Kundenzitat, KPI oder Architektur-Fakt.

### 9. Brand Voice Check

→ Kombiniere mit: `/copy-editing`

Eigenständiger QA-Workflow für beliebigen Content:

1. `get_brand_voice("de")` — vollständige Brand Voice laden
2. Content gegen Abschnitt 10 (Checkliste) prüfen:
   - Message Pillar vorhanden?
   - Jede Behauptung belegt?
   - Keine verbotenen Begriffe?
   - TravelSandbox® / freshMS® mit ®?
   - freshcells kleingeschrieben?
   - Ton passt zum Kanal?
   - Konkreter Kundenname oder Zahl?
3. Bei Langform: Evidenz-Kadenz prüfen (max. 2 Absätze ohne Beleg)

### Andere Aufgaben

Für alle Aufgaben die nicht oben stehen:

```
get_glossar_overview(task: "[deine Aufgabe]")
```

Akzeptiert Freitext und Synonyme — z.B. „social media", „TravelSandbox", „zu teuer", „technisches Angebot". Liefert empfohlene Dateien + Workflow-Kette. 24+ vordefinierte Tasks.

Falls kein Task-Match: `search_vault("[Thema]")` als Einstieg, dann `get_file()` für Treffer.

## Tool-Referenz

| Tool | Parameter | Format | Wann |
|------|-----------|--------|------|
| `search_vault` | `query`, `folder?`, `tag?`, `limit?` | JSON | Thematische Suche, Pfad unbekannt |
| `suggest` | `query` | JSON | Vokabular erkunden vor search_vault |
| `get_file` | `path` | Markdown | Datei laden (Fuzzy-Matching) |
| `get_brand_voice` | `lang` ("de"/"en") | Markdown | IMMER vor Content-Erstellung |
| `get_glossar_overview` | `task?`, `detailed?` | JSON | Aufgaben-Routing, Glossar-Navigation |
| `list_files` | `folder?`, `detailed?` | JSON | Verfügbare Dateien erkunden |
| `search_by_tag` | `tag` | JSON | Dateien nach exaktem Tag |
| `list_tags` | — | JSON [{tag, count}] | Verfügbare Tags entdecken |
| `get_references` | `slug` | JSON | Verwandte Dokumente finden |
| `get_changelog` | `maxEntries?` | Markdown | Letzte Content-Änderungen |
| `get_design_guide` | `page?` | Markdown | Brand Design Guidelines (Fuzzy page-Match) |
| `get_design_tokens` | `category?` | JSON | Exakte Token-Werte für Code |
| `list_assets` | `type?`, `category?` | JSON | Alle Assets auflisten |
| `get_asset` | `name`, `type?` | JSON | Spezifisches Asset (URL + Alternativen) |
| `get_asset_inline` | `name`, `type?` | JSON | Asset inline (SVG/Base64) — hohe Token-Kosten! |

## Parallelisierung

Diese Tools können immer parallel aufgerufen werden:

- `get_brand_voice` + `search_vault` + `get_glossar_overview`
- Mehrere `get_file` Aufrufe
- `get_design_guide(page:)` + `get_design_tokens` + `list_assets`
- `get_asset` + `get_file`

## Anti-Patterns

| Nicht tun | Stattdessen |
|-----------|-------------|
| Content ohne `get_brand_voice` schreiben | IMMER zuerst Brand Voice laden |
| Hex-Werte erfinden | `get_design_tokens` oder `get_design_guide` nutzen |
| `get_asset_inline` für URL-Nutzung | `get_asset` reicht — inline nur bei CSP-Sandbox |
| Behauptungen ohne Beleg | Kundenzitat, KPI oder Referenz aus dem Glossar |
| Ganze Dateien laden wenn nur ein Thema gesucht | `search_vault` mit Folder/Tag-Filter nutzen |
| `list_files` für Glossar-Navigation | `get_glossar_overview` ist kompakter + hat Task-Routing |
| Große Dateien komplett laden (>40KB) | `search_vault("[spezifisches Thema]")` nutzen — liefert relevante Excerpts. Besonders: Sales-Snippets, Sales-Argumente, Brand Voice, Kundenreferenzen |
| Veraltete Produktnamen (TSB, FreshCells) | TravelSandbox® mit ®, freshcells klein |
