[🇺🇸 English](README_en_US.md) | [🇩🇪 Deutsch](README_de_DE.md) | [🇪🇸 Español](README_es_ES.md) | [🇨🇳 中文](README_zh_CN.md) | [🇯🇵 日本語](README_ja_JP.md)

# IronDiscipline-dev (Eiserne Disziplin - Folia-Edition)

Umfassendes Verwaltungs- und Disziplin-Plugin für Minecraft-Server.
Entwickelt für Militär- und Gefängnis-RP-Server.

> ⚡ **Diese Version ist exklusiv für Folia!** Rangdaten werden in einer eigenen Datenbank gespeichert. LuckPerms ist nicht erforderlich.
> Für PaperSpigot verwenden Sie bitte [IronDiscipline](https://github.com/IronDiscipline-Project/IronDiscipline).

## Unterschiede zur Standardversion

| Element | Standard (IronDiscipline) | Dev (IronDiscipline-dev) |
|---|---|---|
| Server | PaperSpigot 1.18+ | Folia 1.18+ |
| Rang-Speicherung | LuckPerms Metadaten | Eigene DB (H2/MySQL) |
| LuckPerms | Erforderlich | Nicht erforderlich (optional für Migration) |
| Leistung | Über API | Direkte DB + Cache |
| Nebenläufigkeit | Standard | Thread-sichere parallele Verarbeitung |
| Folia-Unterstützung | Nicht unterstützt | Vollständig unterstützt (exklusiv) |

## Funktionen

- **Rangsystem**: Berechtigungsverwaltung nach Rang
  - Thread-sicherer paralleler Cache (`ConcurrentHashMap`)
  - Schutz vor Race-Conditions
- **PTS (Permission to Speak)**: Sprecherlaubnis-System
- **Discord-Integration**: Kontoverknüpfung, Rollensynchronisation
- **Warnsystem**: Verwarnungen mit automatischer Bestrafung
  - Verhinderung doppelter Inhaftierungen
  - Sofortige Inventar-Sicherung zur Vermeidung von Gegenstandsverlust
  - Automatische Erkennung und Reparatur von Dateninkonsistenzen
- **Prüfungssystem**: Beförderungsprüfungen mit GUI
- **Datenmigration**: Einfache Migration von LuckPerms mit `/irondev migrate`
- **Folia-Exklusiv**: Natives Folia-Scheduling über MorePaperLib

## Anforderungen

- Java 17+
- Folia 1.18+ (**PaperSpigot nicht unterstützt**)
- MySQL, SQLite oder H2 Database (Standard)

## Installation

1. Neueste JAR von [Releases](https://github.com/IronDiscipline-Project/IronDiscipline-dev/releases) herunterladen
2. In den `plugins`-Ordner des Servers legen
3. Server starten
4. `plugins/IronDisciplineDev/config.yml` nach Bedarf bearbeiten

## Migration von Standardversion

```
/irondev migrate
```

## Befehle

### 🔧 Dev-Version Befehle
| Befehl | Beschreibung | Berechtigung |
|---|---|---|
| `/irondev migrate` | Daten von LuckPerms migrieren | `iron.admin` |
| `/irondev status` | Status anzeigen | `iron.admin` |
| `/iron addon install <id\|owner/repo\|URL>` | Addon installieren | `iron.admin` |
| `/iron addon list` | Installierte Addons anzeigen | `iron.admin` |
| `/iron addon certified` | Zertifizierte Addons anzeigen | `iron.admin` |
| `/iron addon remove <id>` | Addon deinstallieren | `iron.admin` |
| `/iron addon refresh` | Registry-Cache aktualisieren | `iron.admin` |

## Addons

IronDiscipline-dev verfügt über einen integrierten Addon-Manager via `/iron addon`.

### Installation (3 Methoden)

```
# 1. Zertifiziertes Addon (vom IrDi-Team geprüft)
/iron addon install <id>

# 2. Direkt aus einem GitHub Release
/iron addon install <owner/repo>

# 3. Direkte URL (nur HTTPS, max. 50 MB)
/iron addon install https://example.com/myaddon.jar
```

Mit `/iron addon certified` kann die offizielle Addon-Registry durchsucht werden.

Entwicklerdokumentation: [docs/ADDON_DEVELOPMENT.md](docs/ADDON_DEVELOPMENT.md).

## Build

```bash
mvn clean package
```

## Lizenz

MIT License
