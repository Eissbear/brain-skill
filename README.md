# brain – ein gemeinsames Gedächtnis für Claude

Claude vergisst zwischen Chats und Geräten vieles, und Claude Code am PC weiß nichts von dem, was du in der Claude-App am Handy besprochen hast. **brain** löst das mit einem privaten GitHub-Repo voller Markdown-Dateien, das jede Claude-Oberfläche lesen und schreiben kann.

- **`brain read`**: lädt deinen aktuellen Stand (Übersicht + passende Projekte)
- **`brain save`**: hält fest, was im Gespräch entschieden oder erledigt wurde, und pusht es
- **`brain configure`**: richtet alles Schritt für Schritt ein

Das Gedächtnis gehört dir: normale Textdateien in deinem eigenen privaten Repo, mit kompletter Versionsgeschichte.

## Einrichtung

1. [`brain.zip`](https://github.com/Eissbear/brain-skill/raw/main/brain.zip) herunterladen
2. In der Claude-App unter **Einstellungen → Skills** hochladen (Code-Ausführung muss aktiviert sein)
3. Neuen Chat starten und **`brain configure`** schreiben – Claude führt dich durch den Rest:
   GitHub-Repo anlegen, Claude-GitHub-App installieren, Grundgerüst anlegen und am Ende deine **persönliche Version** des Skills erzeugen

Für Claude Code: Ordner `brain/` nach `~/.claude/skills/brain/` kopieren.

## Was du brauchst

- Claude-Plan mit Skills (Pro, Max, Team oder Enterprise) und aktivierter Code-Ausführung
- Kostenlosen GitHub-Account
- Für Claude Code zusätzlich Git

## Sicherheit

- Das Gedächtnis-Repo ist **privat**
- Der Skill fragt nie nach Passwörtern oder Tokens; Anmeldungen machst du selbst
- Regel im Gedächtnis: keine Zugangsdaten und keine privaten Daten Dritter speichern

## Lizenz

MIT
