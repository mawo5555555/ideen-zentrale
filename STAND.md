# Ideen-Zentrale – Stand

**Version:** 1.3.0 (sichtbar oben in der App)

## 1.3.0
- Optik überarbeitet: Projekt-Kacheln im Raster, Layout passt auf Mobil-Bildschirme
- Anleitung unter „Anleitung“ in der App

## Worker (Stand 27.11.2026)
- Live: https://ideen-zentrale.mawo555.workers.dev (Cloudflare, KV „IDEEN“, Token als Secret)
- Token lokal: `worker/.token-lokal.txt` (nicht teilen)
- Node v26.13.1 installiert
- **Offen:** Claude-App-Connector. Die Code-App hat keinen Connectors-Bereich. Befehl bereit, sobald `claude` im Terminal funktioniert:
  `claude mcp add --transport http --scope user ideen-zentrale https://ideen-zentrale.mawo555.workers.dev/mcp --header "Authorization: Bearer $(pbpaste)"`
- Offen: PWA an den Worker anbinden, Testidee im Speicher entfernen

## 1.1.0
- Auto-Zuordnung per Schlüsselwörter zu bekannten Projekten (Katalog in index.html: `KATALOG`), sonst neues Projekt aus den Wörtern der Idee
- „Fragen“-Feld und „Was heute?“: lokale Empfehlung aus offenen Ideen (Projekt mit den meisten offenen Ideen, älteste zuerst)
- Grenze: keine echte KI, nur Schlüsselwörter. Die Zuordnung wird ungenau, wenn Wörter mehrdeutig sind (z. B. „sim“). Schlüsselwörter im Katalog anpassen. Für echte Auswertung braucht es einen Server mit Claude-API-Schlüssel (noch nicht gebaut)

## Was drin ist
- Ideen erfassen: Text tippen oder Button **🎤 Diktieren** (Web Speech API, de-DE)
- Projekte: Auswahl + neues Projekt anlegen, Filter nach Projekt
- Speicherung lokal im Browser (localStorage) je Gerät
- Export/Import als JSON
- Logbuch (aufklappbar)

## Offen / Grenzen
- Keine Sync-Verbindung zwischen Mac und iPhone. Browser können nicht direkt in den Obsidian-Vault schreiben. Abgleich per Export/Import.
- Diktat braucht Safari und Mikrofon-Erlaubnis. Im Home-Bildschirm-Modus ist es auf iOS unzuverlässig.
- Noch offen: Erinnerungen, Arbeitsabläufe je Projekt, Icons, Hosting (GitHub Pages nur nach Freigabe).

## Dateien
- index.html (App inkl. Styles und Logik)
- manifest.webmanifest, sw.js (Offline-Cache)

## Stand 27.11.2026 (v1.6.0, Worker 1.3.0)
- iPhone und Mac-App (Safari „Zum Dock“) mit Cloud verbunden.
- Neu: Ideen bearbeiten/löschen (PUT/DELETE /ideen/:id), Sync in beide Richtungen, Diktat-Leerzeichen.
- Testidee gelöscht. Schichtenverzeichnis-Idee in der Cloud.
- Offene Punkte: LaunchAgent `~/Library/LaunchAgents/de.ideen-zentrale.sync-offen.plist` stündlich + beim Anmelden, Log `~/Library/Logs/ideen-zentrale-sync.log`.
- Claude-Connector geprüft: verbunden.
### Offen
- Optional: Claude-API-Zuordnung (Haiku), braucht API-Guthaben.
