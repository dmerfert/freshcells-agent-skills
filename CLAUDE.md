# freshcells Agent Skills

Claude Plugin mit Marketplace-Support für freshcells. Enthält MCP-Verbindung und Nutzungs-Skills.

## Repo-Struktur

```
freshcells-agent-skills/
├── .claude-plugin/
│   ├── marketplace.json      ← Plugin-Katalog (Marketplace-Installation)
│   └── plugin.json           ← Plugin-Manifest
├── .mcp.json                 ← Remote MCP-Config (Marketing Hub auf Vercel)
├── skills/
│   └── marketing-hub-mcp/
│       └── SKILL.md          ← Nutzungsanweisungen für den MCP
├── README.md
├── CLAUDE.md                 ← Diese Datei
└── LICENSE
```

## Abhängigkeiten

- **Marketing Hub MCP:** `.mcp.json` zeigt auf `https://marketing-hub-phi.vercel.app/api/mcp` (Repo: [dmerfert/marketing-hub](https://github.com/dmerfert/marketing-hub)). Bei Änderungen an der MCP-URL oder den OAuth-Einstellungen muss `.mcp.json` angepasst werden.
- **MCP-Tools:** Die Tool-Liste in `skills/marketing-hub-mcp/SKILL.md` muss mit den tatsächlich verfügbaren Tools im Marketing Hub übereinstimmen. Quelle der Wahrheit: `marketing-hub/web/lib/vault.ts`.

## Regeln

- **Brand Content Rules gelten:** TravelSandbox® mit ®, freshcells kleingeschrieben, Plural-Ihr, echte Umlaute in Content-Dateien
- **Marketplace-Kompatibilität:** `marketplace.json` und `plugin.json` müssen valides JSON bleiben. Plugin-Name `freshcells-marketing` nicht ändern (wird von Installationen referenziert).
- **Versionierung:** Bei inhaltlichen Änderungen an Skills oder MCP-Config die `version` in `plugin.json` und `marketplace.json` hochzählen.

## Sync mit Marketing Hub

- **Bei MCP-Tool-Änderungen:** Wenn im Marketing Hub MCP Tools umbenannt, Parameter geändert oder neue Tools hinzugefügt werden → SKILL.md hier aktualisieren (Tool-Referenz-Tabelle, betroffene Workflows)
- **Bei neuen Glossar-Dateien:** Wenn neue Glossar-Artikel erstellt werden → prüfen ob Workflows in SKILL.md angepasst werden müssen
- **Quelle der Wahrheit:** MCP-Tools → `marketing-hub/web/lib/vault.ts`. Glossar → `marketing-hub/marketing-hub-content/Glossar/`

## Skills bearbeiten

Skills liegen als Markdown-Dateien unter `skills/<skill-name>/SKILL.md`. Der SKILL.md-Frontmatter (`name`, `description`) wird von Claude für die Skill-Erkennung genutzt.

Neue Skills hinzufügen:
1. Ordner unter `skills/<skill-name>/` erstellen
2. `SKILL.md` mit Frontmatter anlegen
3. Version in `plugin.json` und `marketplace.json` hochzählen
