---
name: brain
description: Gemeinsames Gedächtnis für alle Claude-Oberflächen (Claude-App, Handy, Claude Code) in einem privaten GitHub-Repo. Verwenden, wenn der Nutzer "brain configure", "brain read" oder "brain save" sagt, nach dem Stand seiner Projekte oder früheren Entscheidungen fragt, oder Neues festgehalten werden soll.
---

# brain – gemeinsames Gedächtnis über GitHub

Das Gedächtnis ist ein **privates GitHub-Repo** mit Markdown-Dateien. Jede Claude-Instanz (Claude-App am Handy, im Browser, Claude Code am PC) liest es mit „brain read“ und schreibt neue Erkenntnisse mit „brain save“ zurück. So kennen alle denselben Stand.

## Konfiguration

<!-- Wird von "brain configure" ausgefüllt. Solange hier NICHT_KONFIGURIERT steht, ist der Skill die allgemeine Vorlage. -->
- Name: NICHT_KONFIGURIERT
- GitHub-Repo (owner/repo): NICHT_KONFIGURIERT
- Lokaler Ordner am PC (optional): NICHT_KONFIGURIERT
- Sprache des Gedächtnisses: Deutsch

**Steht oben noch `NICHT_KONFIGURIERT`, dann bei „brain read“ oder „brain save“ zuerst kurz erklären, dass der Skill noch eingerichtet werden muss, und „brain configure“ anbieten.**

---

## „brain configure“

Ziel: Der Nutzer hat am Ende ein eigenes privates Gedächtnis-Repo und eine persönliche Version dieses Skills. Freundlich, Schritt für Schritt, immer nur den nächsten Schritt erklären und auf Rückmeldung warten. Der Nutzer muss kein Entwickler sein.

**Niemals nach Passwörtern, Tokens oder Zugangsdaten fragen.** Alle Anmeldungen macht der Nutzer selbst im Browser.

### 1. Grunddaten erfragen
- Wie soll ich dich nennen?
- Hast du schon einen GitHub-Account? Wenn ja: Benutzername?
- Wo arbeitest du mit Claude? (nur App/Handy · auch Claude Code am PC)

### 2. GitHub-Account (falls nötig)
- Auf github.com kostenlos registrieren, E-Mail bestätigen.

### 3. Privates Repo anlegen
- github.com → oben rechts „+“ → **New repository**
- Name z. B. `gedaechtnis`, Sichtbarkeit **Private**, Haken bei „Add a README file“ setzen → **Create repository**

### 4. Claude Zugriff auf das Repo geben
Zwei Dinge sind nötig, das zweite wird oft vergessen:
1. In der Claude-App unter **Einstellungen → Connectors** GitHub verbinden.
2. Die **Claude-GitHub-App installieren**: github.com/apps/claude → **Install** → eigenen Account wählen → „Only select repositories“ → das Gedächtnis-Repo auswählen → bestätigen.
   - Nur „autorisiert“ reicht nicht: Unter GitHub → Settings → Applications muss Claude bei **Installed GitHub Apps** auftauchen.

Dann prüfen: Repo zur Sitzung hinzufügen und klonen. Klappt es nicht, Schritt 4 nochmal durchgehen.

### 5. Grundgerüst anlegen
Ins Repo schreiben (Vorlagen im Ordner `vorlagen/` dieses Skills, Platzhalter `{{NAME}}`, `{{REPO}}`, `{{DATUM}}` ersetzen):
- `CLAUDE.md` ← `vorlagen/CLAUDE.md`
- `uebersicht.md` ← `vorlagen/uebersicht.md`
- `projekte/beispiel.md` ← `vorlagen/projekt.md` (oder gleich ein echtes Projekt, das der Nutzer nennt)

Den Nutzer fragen, ob er schon 2–3 Projekte, Themen oder Vorhaben nennen will, die ins Gedächtnis sollen, und diese gleich eintragen. Dann committen (`brain: Grundgerüst angelegt`) und pushen.

### 6. Nur bei Claude Code am PC
- Git installieren (Windows: git-scm.com, Standardeinstellungen), Claude Code installieren
- Repo in einen Ordner klonen, z. B. `C:\Claude\gedaechtnis`, und den Pfad erfragen
- Die persönliche `SKILL.md` (Schritt 7) ablegen unter `~/.claude/skills/brain/SKILL.md` (Windows: `C:\Users\<Name>\.claude\skills\brain\SKILL.md`), Ordner `vorlagen/` daneben
- Optional in `~/.claude/CLAUDE.md` ergänzen: „Mein Gedächtnis liegt in <Pfad>. Zu Beginn einer Aufgabe `uebersicht.md` und die passende Projektdatei lesen.“

### 7. Persönliche Version des Skills erzeugen
Ein in der App hochgeladener Skill kann sich selbst nicht ändern, deshalb bekommt jeder eine eigene Kopie:
1. Diesen Skill-Ordner kopieren
2. Im Abschnitt **Konfiguration** die Werte eintragen (Name, owner/repo, lokaler Ordner oder „–“)
3. Als ZIP packen (Ordner `brain/` mit `SKILL.md` und `vorlagen/` darin) und dem Nutzer geben
4. Erklären: ZIP in der Claude-App unter **Einstellungen → Skills** hochladen (vorher die allgemeine Version entfernen). Bei Claude Code die `SKILL.md` wie in Schritt 6 ablegen.
5. Zusätzlich die persönliche `SKILL.md` unter `skills/brain/SKILL.md` ins Gedächtnis-Repo committen, dann ist sie versioniert.

### 8. Test
„brain read“ ausführen und zeigen, dass alles funktioniert. Kurz erklären: „brain read“ am Anfang eines Gesprächs, „brain save“ wenn etwas entschieden oder erledigt wurde.

---

## Repo bereitstellen (für read/save)
- **Claude-App (Web/Handy):** das konfigurierte Repo mit Schreibzugriff zur Sitzung hinzufügen, klonen, darin arbeiten.
- **Claude Code am PC:** im konfigurierten lokalen Ordner arbeiten.
- Immer zuerst `git pull --rebase`.

## „brain read“
1. Repo bereitstellen + `git pull --rebase`
2. `CLAUDE.md` und `uebersicht.md` lesen
3. Projektdateien in `projekte/` lesen, die zum aktuellen Thema passen (bei Unklarheit nur die Übersicht)
4. Dem Nutzer in 2–4 Sätzen sagen, welcher Stand geladen ist – keinen Dateiinhalt abschreiben

## „brain save“
1. Repo bereitstellen + `git pull --rebase`
2. Aus dem bisherigen Gespräch sammeln: Was ist neu, entschieden, erledigt oder geändert?
3. Betroffene Dateien aktualisieren (`uebersicht.md` + `projekte/*.md`, neue Projektdatei bei neuem Projekt). Veraltetes ersetzen statt anhängen, Datum bei Statusänderungen
4. Diff prüfen: **keine** Passwörter, Keys, Tokens, Zugangsdaten, Kontonummern, keine privaten Daten Dritter
5. Commit mit kurzer Message (z. B. `Projekt X: Entscheidung Y`), dann `git push`
6. In 1–2 Sätzen sagen, was gespeichert wurde
- Konflikte zusammenführen, nichts Fremdes verwerfen
- Gibt es nichts Neues: nichts committen und das kurz sagen

Die Regeln in der `CLAUDE.md` des Gedächtnis-Repos haben Vorrang vor diesem Skill.
