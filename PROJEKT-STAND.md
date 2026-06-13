# Projektstand – Tagesnotizen

**Kurz:** Meine eigene Tagebuch- & Buch-App. Ziel: **alles an einem Ort** – Notizen, Bücher (Lebenslauf/Erinnerungen), Bilder, Dokumente. Für den **Nachlass**: später alles aufs Papier + Bilder auf ein separates Medium.

**Aktuelle Version:** v39 (oben im Buch/Editor sichtbar als „· vNN" – zum Prüfen, ob die neueste Fassung geladen ist).

---

## 1) Tagesnotizen (pro Tag)
- Notizen pro **Tag** und **Kategorie** (sprechen oder tippen)
- **KI-Zusammenfassung** und **Prosa-Geschichten**
- **Bilder, Audio, Videos, Dokumente** pro Tag
- **Suche**, **Export**, Kalender-Absprung
- (Noch zu prüfen von mir: ob bei den Tagesnotizen alles schön ist – evtl. eigener Chat)

## 2) Bücher (Buch-Kategorien) – das große Thema der letzten Tage
Eine Buch-Kategorie = ein Buch mit **drei Ebenen**: 📖 Kapitel → 📑 Abschnitt → 📄 Unterabschnitt.

**Lese-Ansicht (Buch öffnen):**
- Inhaltsverzeichnis 📑 mit Einrückung pro Ebene; **Titel antippen** = hinspringen, **📷** = zum Kapitel springen + Foto-Modus an.
- Ganzer Text am Stück; **in den Text tippen = ab dort vorlesen**; Zielüberschrift **blinkt gelb** beim Hinspringen.
- Kopfleiste: 🔊 alles vorlesen (stoppbar ⏹), ✏️ bearbeiten, 📷 Foto-Modus, 🖨️ drucken.
- **📷 Foto-Modus:** pro Kapitel/Abschnitt Bilder/Dateien hochladen, ⬇️ herunterladen, ✕ löschen, **↪ zu anderer Überschrift verschieben**; umbenannte Überschriften → „📦 nicht zugeordnete Medien".

**Bearbeiten (✏️):**
- Jeder Block = eine Überschrift + Text. **Rechte Knopf-Spalte (läuft mit):** 🎤 Mikro, 📝 Rechtschreibung, 🪄 KI, 🔊 Vorlesen (ab Cursor), ↩, ✖.
- **🪄-Fenster:** Modell wählen + Stil (schlicht/normal/blumig) + „nur markierter Teil" + „vorher Rechtschreibung".
- **Automatisches Speichern** (kein Speichern-Knopf nötig). Mikro-Aus löst nichts aus; **anderer Knopf** = Abschnitt abschließen (Rechtschreibung + sichern).
- **📍 Stecknadel:** zuletzt vorgelesene Stelle; rot = auffindbar, ⚫ schwarz = verloren (neu vorlesen). Obere Leiste antippen = hinspringen.
- **Verschieben** ⬆️⬇️ (blinkt + rückt in Bildmitte), **einfügen** ➕📖/➕📑/➕📄 direkt darunter, **zusammenführen** 🔗 (ankreuzen).
- **📑 Gliederung:** kompakte Ansicht zum Verschieben/Einfügen, 🟢 = hat Inhalt / ⚪ = leer, Titel antippen = zum Block.

## 3) KI
- GitHub Models (Token im Bereich „🤖 KI-Analyse"). Modelle: gpt-4o-mini, gpt-4o, Phi-4, Llama-3.3-70B, **Ministral-3B**.
- gpt-4o-mini & Ministral-3B bleiben am ehesten beim Inhalt. KI erfindet **keine** Politiker/Ereignisse (so eingestellt).
- Vorlese-Stimme **pro Gerät** auswählbar (Stimmen sind geräteabhängig).
- **Rechtschreibung** auch bei Tagesnotizen: 📝-Knopf (Inhalt bleibt exakt). „"-Knopf zum Setzen von Anführungszeichen. (Der 🪄-Zauberstab macht KEINE Auto-Rechtschreibung mehr – das hatte ihn blockiert.)
- **🗣️ Aussprache-Liste (schwarzer Knopf):** pro Wort eine **Sprache** wählbar (Englisch/Französisch/…) → wird **in echter Sprachstimme** vorgelesen, *falls die Stimme auf dem Gerät installiert ist*. Sonst greift die **lautmalerische Ersatz-Schreibweise** (z. B. Roger → „Ro scheee"). Vorlesen erfolgt **segmentweise mehrsprachig** (Deutsch drumherum + Fremdwort in seiner Sprache). Voreingestellt: **Roger → Französisch** (Ersatz „Ro scheee"). Im Text bleibt immer das Original.
  - Hinweis: kleiner Übergang/Pause beim Stimmwechsel ist technisch bedingt; nahtlos nur mit kostenpflichtigem Cloud-TTS. Sprachstimmen müssen am Gerät installiert sein (Einstellungen → Sprachausgabe).

## 4) Sicherheit – ERLEDIGT (Schritt 1) ✅
- **Login** (Supabase Auth, E-Mail + Passwort). Konto: renapralat@gmail.com. Anmeldung pro Gerät **einmal**, bleibt gespeichert (immer dasselbe github.io-Lesezeichen nutzen!).
- **RLS aktiv** auf `tagesnotizen_entries`, `tagesnotizen_categories`, `tagesnotizen_media`: **nur das eigene Konto** (per E-Mail) hat Zugriff.
- **Noch offen (Schritt B):** Die **Bild-Dateien im Speicher** (Bucket `tagesnotizen-media`) sind technisch noch über ihre zufällige URL erreichbar. Die *Liste* der URLs ist aber geschützt (steckt nur in der jetzt gesicherten Datenbank). Voller Schutz = Bucket privat + signierte URLs.
- **Ernährung & Sammlungen:** noch ungesichert (eigene Repos/Aufträge). Dasselbe Login-Konto gilt später mit.

---

## Offene Punkte (nächste Schritte, Reihenfolge)
1. **🖨️ Druck mit Bild-Hinweisen:** Druck bleibt reiner Text (spart Tinte), aber pro Kapitel ein kleiner Vermerk „📷 dazu gibt es Bilder: …". Bilder selbst nicht drucken.
2. **💾 „Alle Bilder herunterladen"** (mit Bezeichnungen) – für den Nachlass aufs separate Medium (Stick/Platte).
3. **🔒 Schritt B:** Bild-Dateien absichern (Bucket privat + signierte URLs).
4. **Ernährung & Sammlungen** absichern (eigene Repos).
5. Kleinere: Tagesnotizen mal durchsehen; Verknüpfungen/Stichwörter (zurückgestellt).

## So arbeiten wir
- Claude baut → ich bekomme eine **Vorschau** → „passt" → es wird **live** (auch auf `main`, damit mein github.io-Lesezeichen die neueste Version zeigt).
- Versionsnummer oben (vNN) hilft beim Prüfen, ob die neue Fassung geladen ist.

## Wichtige Daten
- GitHub: **renapralat/Tagesnotizen** · Arbeits-Zweig: **claude/tagesnotizen-improvements-XhQpS** (wird auch auf **main** veröffentlicht)
- Datenbank: **Supabase** (Projekt `bxwamphvycjfeexjzgyv`), Bucket `tagesnotizen-media`
- App-Lesezeichen: **github.io** (immer dieses nutzen, damit man angemeldet bleibt)
