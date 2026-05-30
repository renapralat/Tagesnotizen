# 📔 Tagesnotizen

Persönliches digitales Tagebuch mit Spracheingabe, KI-Zusammenfassung und Cloud-Speicherung.
Läuft komplett im Browser, ohne Installation — optimiert für Android.

---

## Was die App macht

- **Notizen erfassen** — per Mikrofon (Sprache) oder Tastatur
- **Kategorien** — eigene Themengebiete anlegen (z. B. Tagesprotokoll, Gedanken, Familie)
- **Zwischenspeichern** — mehrere Sprachaufnahmen sammeln, bevor man zusammenfasst
- **KI-Zusammenfassung** — rohe Notizen werden zu einem sauberen Tagebucheintrag umgeschrieben
- **Vorlesen** — Einträge per Text-to-Speech anhören (ganzer Eintrag oder ab Cursor-Position)
- **Globale Suche** — über alle Kategorien und alle Tage, mit Wildcard-Unterstützung
- **Export & Löschen** — nach Tag oder Zeitraum, gefiltert nach Kategorie, als `.txt`-Datei

---

## Bedienung (Kurzübersicht)

### Kategorie wählen (blaue Chips)
Erst eine Kategorie antippen → dann erscheint das Eingabefeld.

### Eingabe-Bereich (rechte Spalte)
| Symbol | Funktion |
|--------|----------|
| 🎤 | Aufnahme starten / stoppen |
| ÜE / FT | Zusammenfassung **mit Überschriften** oder als **Fließtext** |
| + | Aufnahme zwischenspeichern (mehrere sammeln) |
| − | Eingabefeld leeren |
| 🪄 | KI-Zusammenfassung erstellen |

### Zusammenfassungs-Bereich (rechte Spalte)
| Symbol | Funktion |
|--------|----------|
| 🔊 | Gesamten Text vorlesen |
| ▶ | Ab Cursor-Position vorlesen |
| 💾 | Zusammenfassung speichern |
| ↩ | Zurück zur Eingabe |

### Suche
Im Suchfeld mit 🌐 sucht man über **alle Kategorien und alle Tage**.
Wildcard-Syntax:
- `Ei` → findet nur das Wort „Ei" (exakt)
- `*fee` → findet Wortenden (z. B. „Kaffee")
- `Ka*` → findet Wortanfänge (z. B. „Kathy", „Kaffee")
- `*kaff*` → findet den Begriff überall im Wort

### Export / Löschen
- **Von–Bis** + Kategorie-Auswahl → Zeitraum herunterladen oder löschen
- **📥 Tag** + Datum → einzelnen Tag herunterladen oder löschen
- Kategorie-Dropdown: leer = alle Kategorien; einzelne oder mehrere auswählbar

---

## Technischer Aufbau

### Hosting
- **GitHub Pages** — die App besteht aus einer einzigen Datei: `index.html`
- URL: `https://renapralat.github.io/Tagesnotizen`

### Datenbank
- **Supabase** (PostgreSQL, kostenloser Free Tier)
- Tabelle: `tagesnotizen_entries`
- Spalten: `datum` (Datum), `category` (Kategorie), `text` (Inhalt)
- Supabase-Projekt-ID: `bxwamphvycjfeexjzgyv`
- Verbindung: Supabase JS Client via CDN, anonymer Public Key

### KI-Zusammenfassung
- **API:** GitHub Models API
  - Endpunkt: `https://models.inference.ai.azure.com/chat/completions`
  - Modell: `gpt-4o`
- **Authentifizierung:** GitHub Personal Access Token (PAT)
  - Wird lokal im Browser gespeichert (`localStorage`): Key `tagesnotizen-github-pat`
  - Token einmalig über „Token verwalten" eingeben — bleibt gespeichert
- **System-Prompt:** Weist die KI an, die Ich-Perspektive beizubehalten, Namen korrekt zuzuordnen (Norbert = Ehemann), Themen zu gliedern und optional fette Überschriften zu setzen

### Sprache
- **Eingabe:** Web Speech API (`SpeechRecognition`) — funktioniert in Chrome/Android
- **Ausgabe:** Web Speech Synthesis (`SpeechSynthesis`) — Stimme im Browser wählbar

---

## Für eine neue App: Was hat hier gut funktioniert?

| Baustein | Empfehlung |
|----------|------------|
| **Datenbank** | Supabase Free Tier — einfach, schnell, kein Backend nötig |
| **KI** | GitHub Models API mit `gpt-4o` — kostenlos mit GitHub-Konto, sehr gut auf Deutsch |
| **Token-Handling** | GitHub PAT in `localStorage` speichern — einfach, sicher genug für private Apps |
| **Single-File-App** | Eine `index.html` — leicht zu pflegen, sofort deploybar auf GitHub Pages |
| **Spracheingabe** | `webkitSpeechRecognition` mit `lang: 'de-DE'` — funktioniert gut auf Android Chrome |
| **TTS** | `SpeechSynthesis` — kostenlos, kein API nötig, Stimme im Browser wählbar |

---

## GitHub Token erstellen (für KI-Funktion)

1. GitHub → Settings → Developer Settings → Personal Access Tokens → Fine-grained tokens
2. Token erstellen (kein spezieller Scope nötig für GitHub Models)
3. In der App: „Token verwalten" → Token einfügen → Speichern

---

*Erstellt mit Claude Code · Stand: Mai 2026*
