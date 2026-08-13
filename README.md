# ⏱ Stempeluhr

Eine kleine, eigenständige Web-App zur Arbeitszeiterfassung mit Sekundengenauigkeit,
automatischer Zuschlagsberechnung und Wochen-/Jahresübersicht.

Läuft komplett im Browser – **keine Installation, kein Server, kein Backend** nötig.
Alle Daten werden lokal im `localStorage` des Browsers gespeichert.

## Funktionen

- **Wochenansicht** (Mo–So) mit Start-/Endzeit auf die Sekunde genau
- **Automatische Zuschlagsberechnung**:
  - 06:00–22:00 Uhr → normal (×1)
  - 04:00–06:00 Uhr → ×1,5
  - 22:00–04:00 Uhr → Nachtarbeit ×2
  - Samstag/Sonntag → Wochenende, pauschal ×2
  - Eine Schicht wird automatisch korrekt über mehrere Zeitfenster aufgeteilt (z. B. eine Nachtschicht von 20–06 Uhr)
- **Pausenregelung**: Ab 6 Stunden Bruttoarbeitszeit wählbar, ob 30 Minuten Pause gemacht wurden (wird anteilig von den Zuschlagszeiten abgezogen)
- **Soll-/Ist-Vergleich pro Woche**: frei einstellbare wöchentliche Sollstunden, geleistete Stunden werden automatisch abgezogen → Über-/Minusstunden auf einen Blick
- **Jahresrückblick**: aggregierte Übersicht für das aktuelle Jahr und die zwei Vorjahre, inkl. Monatsaufschlüsselung und Zuschlagskategorien
- **Sicherung (Backup)**: alle Daten lassen sich als JSON-Datei exportieren und auf einem anderen Gerät/Browser wieder importieren

## Nutzung

Die App besteht aus einer einzigen Datei: [`index.html`](index.html).

- **Lokal öffnen**: Datei per Doppelklick im Browser öffnen – funktioniert offline.
- **GitHub Pages**: Repository auf GitHub veröffentlichen und unter *Settings → Pages* den Branch `main` (Root) als Quelle einstellen. Die App ist danach unter `https://<username>.github.io/<repo>/` erreichbar.

### Lokaler Testserver (optional)

Für die Entwicklung liegt ein kleines PowerShell-Serverskript bei:

```powershell
powershell -ExecutionPolicy Bypass -File serve.ps1
```

Startet einen lokalen Server unter `http://localhost:5501/`.

## Datenspeicherung & Sicherung

Alle Einträge werden ausschließlich lokal im Browser gespeichert (`localStorage`).
Es gibt **keine Cloud-Synchronisation**. Über die Buttons *Sicherung exportieren* /
*Sicherung importieren* lassen sich die Daten als JSON-Datei sichern bzw. auf ein
anderes Gerät übertragen.

## Technik

Reines HTML/CSS/JavaScript, keine Abhängigkeiten, keine Build-Schritte.
