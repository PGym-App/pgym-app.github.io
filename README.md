# PGym

Ganz einfache Gym-App fürs iPhone: Sie zeigt dir, welche Übungen du am längsten nicht mehr gemacht hast. Keine Anmeldung, kein Timer, keine Werbung.

## So funktioniert's

- **Übersicht:** Oben stehen die Übungen, die du noch nie oder am längsten nicht gemacht hast. Tippst du eine Übung an, ist sie für heute erledigt und rutscht nach unten. Nochmal antippen macht es rückgängig.
- **Nach Zeit / Nach Ordner:** Entweder eine lange Liste (oben lassen sich einzelne Ordner wie „Beine“ herausfiltern) oder nach Ordnern gruppiert.
- **Farbpunkte:** grün = weniger als 7 Tage her, gelb = 7 bis 13 Tage, rot = 14 Tage oder mehr, roter Ring = noch nie gemacht.
- **Suche:** findet Übungen und Ordner. Gibt es eine Übung noch nicht, kannst du sie direkt aus der Suche anlegen.
- **Verlauf:** Alle Trainings mit Datum. Antippen, um Übungen hinzuzufügen oder zu entfernen, das Datum zu ändern oder das Training zu löschen. Vergessene Trainings lassen sich nachtragen.
- **Verwalten:** Übungen und Ordner hinzufügen, umbenennen, verschieben und entfernen. Entfernte Übungen bleiben im Verlauf erhalten.

## Wo die Daten liegen

Alles wird sofort nach jeder Änderung in PGym auf deinem iPhone gespeichert. Zusätzlich sichert PGym deine Daten automatisch in einem **geheimen Gist** in deinem GitHub-Konto, sobald du die Sicherung einmal eingerichtet hast. So geht nichts verloren, auch wenn du den Safari-Verlauf löschst, das Icon entfernst oder ein neues Handy bekommst.

- Ohne Internet speichert PGym erst auf dem iPhone und schickt die Änderungen automatisch nach, sobald wieder Empfang da ist.
- Das Wolken-Symbol oben rechts zeigt den Stand: grün = alles gesichert, orange = noch nicht eingerichtet, grau = wartet auf Internet, rot = Problem (z. B. Schlüssel abgelaufen).
- Jede Änderung ist im Gist als eigene Version gespeichert. Auf github.com unter **Your gists → pgym-daten.json → Revisions** lässt sich so auch ein alter Stand ansehen.
- Benutzt du PGym auf mehreren Geräten (z. B. iPhone und Mac), gewinnt beim Öffnen immer der neuere Stand.

### Sicherung einrichten (einmalig, ca. 3 Minuten)

1. In PGym auf **Verwalten → Sicherung einrichten** tippen, dann auf **GitHub öffnen**.
2. Bei GitHub anmelden. Auf der Seite „New personal access token“ bei **Expiration** „No expiration“ wählen. Der Haken bei **gist** ist schon gesetzt, sonst nichts anhaken.
3. Ganz unten auf **Generate token** tippen und den Schlüssel (beginnt mit `ghp_`) kopieren.
4. Zurück in PGym den Schlüssel einfügen und auf **Verbinden** tippen.
5. Den Schlüssel zusätzlich in deinen Notizen oder im Passwort-Manager speichern. Du brauchst ihn, um die Daten auf ein neues iPhone zurückzuholen.

Der Schlüssel darf nur Gists anlegen und ändern. An deine Repositories und dein Konto kommt er nicht. Ein geheimes Gist ist nirgends öffentlich gelistet, nur wer den genauen Link kennt, könnte es ansehen.

### Daten zurückholen (neues iPhone, Verlauf gelöscht)

PGym öffnen, **Verwalten → Sicherung einrichten**, gespeicherten Schlüssel einfügen, **Verbinden**. PGym findet die Sicherung selbst und lädt alles zurück. Sind auf beiden Seiten Trainings vorhanden, fragt PGym, welche Version du behalten willst.

Unter **Backup-Datei** kannst du zusätzlich eine Datei sichern und laden. Das ist nur eine Reserve und mit der GitHub-Sicherung nicht nötig.

Wichtig: Öffne PGym immer über das Icon auf dem Homescreen, nicht über Safari. Safari und die Homescreen-App haben getrennte Speicher.

## Auf GitHub hochladen

PGym bekommt eine eigene Adresse über eine kostenlose GitHub-Organisation. So kommt es Safari nicht mit deinen anderen Apps (PRouter, PRacer …) in die Quere, die unter `DEIN-NAME.github.io` liegen. Safari speichert Favoriten-Icons nur einmal pro Adresse.

1. Auf [github.com](https://github.com) anmelden, oben rechts auf dein Profilbild → **Your organizations** → **New organization** → Plan **Free**. Name z. B. `pgym-app` (falls vergeben: `pgym-pelle` o. ä.), E-Mail eintragen, „My personal account“ wählen, **Next** und den Schritt mit den Mitgliedern mit **Skip** / **Complete setup** überspringen.
2. In der neuen Organisation **New repository** wählen. Owner: die Organisation. Repository-Name **genau** `pgym-app.github.io` (also Organisationsname + `.github.io`), Sichtbarkeit **Public**, dann **Create repository**.
3. **uploading an existing file** anklicken und **alle Dateien aus diesem Ordner** hineinziehen (`index.html`, `sw.js`, `manifest.webmanifest`, `icon.svg`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`, `README.md`). Mit **Commit changes** bestätigen.
4. Unter **Settings → Pages** prüfen, dass *Source* auf **Deploy from a branch**, Branch **main**, Ordner **/ (root)** steht (sonst einstellen und **Save**).
5. Nach ein bis zwei Minuten ist PGym unter `https://pgym-app.github.io/` erreichbar.

## Aufs iPhone holen

1. Die Adresse aus Schritt 5 in **Safari** öffnen.
2. Unten auf das **Teilen-Symbol** (Quadrat mit Pfeil) tippen, dann **Zum Home-Bildschirm**.
3. **Hinzufügen** tippen. PGym erscheint mit Logo auf dem Homescreen, startet ohne Safari-Leisten und funktioniert auch ohne Empfang im Gym.

## Später etwas ändern

Geänderte Dateien einfach erneut ins GitHub-Repository hochladen (gleiche Namen überschreiben die alten). Zusätzlich in `sw.js` die Zeile `const CACHE = 'pgym-v25';` hochzählen (z. B. `pgym-v26`) und in `index.html` `const VERSION = 25;` auf dieselbe Zahl setzen, damit das iPhone die neue Version sicher lädt. Deine Trainingsdaten bleiben dabei erhalten.
