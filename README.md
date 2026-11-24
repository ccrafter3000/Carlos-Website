# LernPilot – Anleitung für Carlos

## Hochladen (3 Dateien)
Diese 3 Dateien **in denselben Ordner** auf dein Hosting hochladen:

```
index.html      ← die Website
curriculum.md   ← dein Lernstoff (ausfüllen!)
MEMORY.md       ← Anweisungen für die KI (optional anpassen)
```

Wichtig: Nur die `index.html` hochladen funktioniert, aber ohne die beiden
`.md`-Dateien kann die KI nicht auf das Curriculum zugreifen.

⚠️ Die .md-Dateien immer als **UTF-8** speichern (Windows-Editor: „Speichern
unter" → Codierung UTF-8) und per FTP im Binärmodus hochladen. Die Website
repariert kaputte Umlaute (Ã¼, â€") inzwischen automatisch, sauber speichern
ist trotzdem besser.

## Erster Login
- Passwort: `carlos2026`  →  **sofort ändern!** (Einstellungen → Passwort ändern)
- Der neue Hash wird angezeigt → in `index.html` die Zeile `const ARGON2_HASH = '...'`
  ersetzen und neu hochladen.

## KI einrichten (Einstellungen)
Ein KI-Anbieter genügt. Schlüssel gehören NUR in deinen Browser, nie in den Quellcode.

| Anbieter | Wo bekomme ich den Schlüssel | Hinweis |
|---|---|---|
| OpenCode Go | opencode.ai → Console → API Keys | ⚠️ erlaubt Browser-Aufrufe (CORS) derzeit nicht – ggf. blockiert |
| ChatGPT (OpenAI) | platform.openai.com/api-keys | kostet pro Nutzung; funktioniert im Browser |
| Google Gemini | aistudio.google.com/app/apikey | kostenloses Kontingent; **empfohlen, funktioniert sicher** |
| Claude | console.anthropic.com | am teuersten; funktioniert im Browser |
| GLM | open.bigmodel.cn / z.ai | günstig; ⚠️ evtl. CORS-Block |
| Ollama (lokal) | keins nötig | läuft nur, wenn Ollama auf demselben PC läuft; starten mit `OLLAMA_ORIGINS=* ollama serve` |

## Sicherheit
- Passwort: Argon2id-Hash im Quellcode (niemand kann daraus das Passwort lesen).
- API-Schlüssel: nur lokal in deinem Browser (localStorage).
- Sitzung: nach 30 Minuten Inaktivität automatisch gesperrt (Session-Cookie).
- Wenn du den Laptop in der Schule teilst: Einstellungen → „Alles löschen".

## Ollama (eigene KI auf dem PC) verbinden
1. Ollama herunterladen und installieren: https://ollama.com/download
2. Im Terminal ein Modell laden: `ollama pull llama3.1`
3. Ollama **mit erlaubter Website-Adresse** starten, damit die gehostete Website
   darauf zugreifen darf:
   - macOS/Linux: `OLLAMA_ORIGINS=* ollama serve`
   - Windows (PowerShell): `$env:OLLAMA_ORIGINS="*"` und dann Ollama neu starten
4. In der App: Einstellungen → Anbieter „Ollama (lokal auf dem PC)" → Speichern.

⚠️ Wichtig: Funktioniert nur, wenn der Browser auf demselben PC läuft wie Ollama
(der Browser ruft `http://localhost:11434` auf). Vom Handy aus geht es nicht –
dann Gemini als Anbieter nehmen. Zum Prüfen, ob Ollama läuft: http://localhost:11434

## Bekannte Grenzen (Bewertung ehrlich erwähnen, gibt Pluspunkte 😉)
- Ohne Datenbank: Lernzettel liegen im Browser – löscht jemand die Browserdaten,
  sind sie weg (deshalb: „Als .md herunterladen"-Button).
- Der Ollama-Modus funktioniert nur am eigenen PC, nicht vom Handy aus.
- Die Passwortprüfung lädt eine kleine Bibliothek vom CDN → Internet nötig.
