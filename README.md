# logbook

Lokale Bodybuilding-Trainings-App als statische PWA. Keine Anmeldung, kein Backend und keine Cloud.

## Dateien
- `index.html` – Oberfläche und Styles
- `app.js` – Anwendungslogik und lokale Datenhaltung
- `manifest.webmanifest` – PWA-Metadaten
- `sw.js` – Offline-Cache
- `icon.svg` – App-Icon

## Lokal testen
Die App sollte über einen lokalen HTTP-Server geöffnet werden (Service Worker funktionieren nicht zuverlässig über `file://`). Im Ordner:
```bash
python -m http.server 8000
```
Dann `http://localhost:8000` öffnen.

## GitHub Pages veröffentlichen
1. ZIP entpacken.
2. Ein GitHub-Repository erstellen.
3. Alle Dateien aus dem Ordner `logbook` direkt in den Repository-Hauptordner hochladen (insbesondere `index.html`).
4. Repository → **Settings → Pages**.
5. **Deploy from a branch** wählen, Branch `main`, Ordner `/ (root)` und speichern.
6. Nach dem Deployment die angezeigte Pages-URL öffnen. Die App benötigt HTTPS für PWA-Installation und Service Worker.

## Installation
- **iPhone:** Pages-URL in Safari öffnen → Teilen → „Zum Home-Bildschirm“ → Hinzufügen.
- **Android:** Pages-URL in Chrome öffnen → Menü → „App installieren“ oder „Zum Startbildschirm hinzufügen“.
- **Desktop:** In unterstützten Browsern das Installationssymbol in der Adressleiste verwenden.

## Speicherung und Backup
Daten werden im Browser-Speicher (`localStorage`) des jeweiligen Geräts und Browserprofils gespeichert. Browserdaten löschen, privater Modus oder Gerätewechsel können Daten entfernen. Regelmäßig unter **Profil → JSON-Backup exportieren** sichern. Auf dem Zielgerät **Backup importieren** und den Überschreibdialog bestätigen. Das Backup enthält alle Profile, Pläne, Übungen, Trainings, Geräte und Gewichtseinträge.

## Wichtige Hinweise
- Die App ist eine lokale Einzelgeräte-Anwendung: Daten werden nicht automatisch zwischen Geräten synchronisiert.
- Für Offline-Betrieb muss die App mindestens einmal online über HTTPS geladen worden sein.
- Der Service Worker cached die Kern-Dateien. Nach App-Updates kann ein Neuladen erforderlich sein.
- Vor dem Import wird eine Formatprüfung durchgeführt; ein gültiges Backup ersetzt den vorhandenen lokalen Datenbestand.
