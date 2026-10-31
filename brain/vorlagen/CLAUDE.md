# Gedächtnis

Zentrales Gedächtnis von {{NAME}} für alle Claude-Instanzen (Claude-App, Handy, Claude Code). Privates GitHub-Repo `{{REPO}}`.

## Aufbau

- `uebersicht.md`: wer ich bin (kurz), alle Projekte/Themen mit 1–2 Sätzen, wo sie liegen, Status
- `projekte/<name>.md`: je Projekt **Zweck · Motivation · Wo liegt was · Stand · Entscheidungen · Offene Ideen/To-dos**
- `plaene/`: größere Arbeitspläne, Häkchen beim Abarbeiten setzen

## Lesen

Zu Beginn einer Aufgabe `uebersicht.md` und die betroffene Projektdatei lesen.

## Regeln

- Sprache: Deutsch, UTF-8
- **Niemals** speichern: Passwörter, Keys, Tokens, Zugangsdaten, Kontonummern, private Daten Dritter
- Fakten knapp halten. Veraltetes aktualisieren statt Neues anhängen, Erledigtes aus den To-dos streichen
- Bei Statusänderungen das Datum dazuschreiben
- Neues Projekt: Datei in `projekte/` nach demselben Schema anlegen und in `uebersicht.md` eintragen
- Dateinamen in Kleinbuchstaben ohne Leerzeichen

## Workflow „brain save“

1. `git pull --rebase`
2. Was ist neu, entschieden oder erledigt? → `uebersicht.md` und betroffene `projekte/*.md` aktualisieren
3. `git diff` prüfen (keine Secrets, keine privaten Daten Dritter)
4. Commit mit kurzer Message, dann `git push`
5. In 1–2 Sätzen sagen, was geändert wurde

Bei Konflikten zusammenführen, nichts Fremdes verwerfen.
