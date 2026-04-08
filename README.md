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
| `marketing-hub-mcp` | Nutzungsanweisungen für den freshcells Marketing Hub MCP — Brand Voice, Glossar, Referenzen, Design-Tokens |

## MCP-Verbindung

Das Plugin konfiguriert automatisch die Verbindung zum [Marketing Hub MCP](https://marketing-hub-phi.vercel.app). Der MCP-Server liefert Inhalte aus dem [Marketing Hub Repo](https://github.com/dmerfert/marketing-hub) — Glossar, Brand Voice, Referenzen und Design-Tokens werden dort gepflegt. Beim ersten Aufruf erfolgt ein OAuth-Login mit eurem @freshcells.de Google-Konto.

## Links

- [Marketing Hub](https://marketing-hub-phi.vercel.app) — Zentrale Wissensplattform
- [Onboarding](https://marketing-hub-phi.vercel.app/onboarding) — Einstieg für alle Teams
- [Skills-Übersicht](https://marketing-hub-phi.vercel.app/skills) — Alle verfügbaren Skills
