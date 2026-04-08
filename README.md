# freshcells Agent Skills

Skills und MCP-Integration für KI-Agenten bei freshcells.

## Installation

### Claude Desktop (Plugin-Marketplace)

1. **Anpassen → Skills → + Fähigkeiten durchsuchen → Plugins → Persönlich → + Marketplace hinzufügen**
2. GitHub-URL einfügen: `https://github.com/dmerfert/freshcells-agent-skills`
3. Fertig — MCP-Verbindung und Skills sind sofort verfügbar

### Claude Code

```
/plugin install dmerfert/freshcells-agent-skills
```

## Enthaltene Skills

| Skill | Beschreibung |
|-------|-------------|
| `marketing-hub-mcp` | 9 Workflows, Brand Rules, Tool-Referenz für den Marketing Hub MCP (15 Tools, 120+ Dokumente) |

## MCP-Verbindung

Das Plugin konfiguriert automatisch die Verbindung zum [Marketing Hub MCP](https://marketing-hub-phi.vercel.app). Der MCP-Server liefert Inhalte aus dem [Marketing Hub Repo](https://github.com/dmerfert/marketing-hub) — Glossar, Brand Voice, Referenzen und Design-Tokens werden dort gepflegt. Beim ersten Aufruf erfolgt ein OAuth-Login mit eurem @freshcells.de Google-Konto.

## Empfohlene Ergänzungen

| Plugin | Befehl | Inhalt |
|--------|--------|--------|
| **Marketing Skills** | `claude install-plugin github:coreyhaines31/marketingskills` | 32 Skills (`/copywriting`, `/cold-email`, `/social-content` etc.) |
| **Figma** | `claude plugin install figma@claude-plugins-official` | Offizieller Figma MCP für Design-Umsetzung |

## Plugin-Updates

Updates an Skills werden über den Plugin-Marketplace automatisch verteilt:

1. Skill-Datei unter `skills/<skill-name>/SKILL.md` bearbeiten
2. Version in `plugin.json` und `marketplace.json` hochzählen
3. Commit + Push auf `main`
4. Nutzer bekommen das Update beim nächsten Plugin-Refresh

### Neuen Skill hinzufügen

1. Ordner `skills/<neuer-skill>/` erstellen
2. `SKILL.md` mit Frontmatter (`name`, `description`) anlegen
3. Version hochzählen
4. Commit + Push

## Links

- [Marketing Hub](https://marketing-hub-phi.vercel.app) — Zentrale Wissensplattform
- [Onboarding](https://marketing-hub-phi.vercel.app/onboarding) — Einstieg für alle Teams
- [Skills-Übersicht](https://marketing-hub-phi.vercel.app/skills) — Alle verfügbaren Skills
