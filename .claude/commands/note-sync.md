Synchronisiere Markdown-Dateien aus dem Repository in Apple Notes (Ordner "Theologie").

Fach (optional): $ARGUMENTS

Falls kein Fach angegeben ist, alle Faecher synchronisieren. Falls die Zuordnung unklar ist, Faecher nummeriert auflisten und nachfragen.

## Ziel

Alle relevanten Markdown-Dateien sollen in Apple Notes unter dem Ordner "Theologie" abgelegt werden. Pro Fach wird ein Unterordner angelegt. Nur Markdown-Dateien werden importiert, keine anderen Formate.

## Was importiert wird

1. **Zusammenfassungen von Transkriptionen** aus `Moodle`: Dateien mit dem Suffix `-Zusammenfassung.md`, die zu einer Video-Transkription gehoeren (d. h. eine gleichnamige `.mp4`-Datei oder eine Transkriptions-Markdown-Datei ohne PDF-Gegenstueck existiert).
2. **Eigene Notizen** aus `Notes`: Alle `.md`-Dateien im `Notes`-Ordner des Fachs.

## Was NICHT importiert wird

- Markdown-Dateien, die aus einer PDF-Konvertierung stammen (d. h. eine gleichnamige `.pdf`-Datei im selben Ordner existiert).
- Reine Transkriptionen (ohne Zusammenfassungs-Suffix).
- Nicht-Markdown-Dateien (PDFs, HTML, TIFF, etc.).
- `DB.md` und `README.md`.
- Dateien in Ordnern, die in `DB.md` unter `Ignorierte Ordner` gelistet sind.

## Ablauf

1. Fach oder Faecher identifizieren.
2. `DB.md` des Fachs lesen und `Ignorierte Ordner` beachten.
3. Alle relevanten Markdown-Dateien sammeln nach obigen Regeln.
4. In Apple Notes pruefen, ob der Ordner "Theologie" > "[Fachname]" existiert. Falls nicht, anlegen.
5. Fuer jede Datei pruefen, ob bereits eine gleichnamige Notiz im Zielordner existiert.
   - Falls ja: Inhalt der bestehenden Notiz mit dem aktuellen Dateiinhalt aktualisieren (ueberschreiben).
   - Falls nein: Neue Notiz anlegen.
6. Am Ende eine Zusammenfassung ausgeben: welche Notizen neu erstellt, aktualisiert oder uebersprungen wurden.

## Technische Umsetzung

### Markdown zu HTML

Apple Notes verwendet HTML intern. Markdown-Dateien muessen vor dem Import nach HTML konvertiert werden:

```bash
npx -y marked < "datei.md"
```

### Apple Notes via AppleScript

Ordner anlegen (falls nicht vorhanden):

```applescript
tell application "Notes"
  set theolFolder to folder "Theologie"
  try
    set subFolder to folder "FACHNAME" of theolFolder
  on error
    make new folder at theolFolder with properties {name:"FACHNAME"}
    delay 0.5
    set subFolder to folder "FACHNAME" of theolFolder
  end try
end tell
```

Notiz anlegen oder aktualisieren:

```applescript
tell application "Notes"
  set subFolder to folder "FACHNAME" of folder "Theologie"
  set noteExists to false
  repeat with n in notes of subFolder
    if name of n is "NOTIZNAME" then
      set body of n to "HTML_CONTENT"
      set noteExists to true
      exit repeat
    end if
  end repeat
  if not noteExists then
    make new note at subFolder with properties {name:"NOTIZNAME", body:"HTML_CONTENT"}
  end if
end tell
```

### Wichtig bei der Umsetzung

- HTML-Inhalt muss fuer AppleScript korrekt escaped werden (Anfuehrungszeichen, Backslashes).
- Den HTML-Inhalt am besten ueber eine temporaere Datei an AppleScript uebergeben, um Escaping-Probleme zu vermeiden.
- Empfohlener Ansatz: HTML in eine temp-Datei schreiben, dann per AppleScript `read file` einlesen.

```bash
# Markdown -> HTML -> temp file
npx -y marked < "datei.md" > /tmp/note_sync_content.html

# AppleScript liest aus temp file
osascript -e '
  set htmlContent to read POSIX file "/tmp/note_sync_content.html" as «class utf8»
  tell application "Notes"
    -- ... Notiz erstellen/aktualisieren mit htmlContent ...
  end tell
'
```

- Nach dem Sync temporaere Dateien aufraeumen.
- Bei vielen Dateien sequentiell arbeiten, um Apple Notes nicht zu ueberlasten (kurze Pause zwischen Operationen).

## Performance-Regeln

- Zuerst Dateinamen pruefen, bevor Inhalte gelesen werden.
- Nur Dateien verarbeiten, die den Importkriterien entsprechen.
- Bestehende Notizen nur aktualisieren, wenn sich der Inhalt geaendert hat (optional: Hash-Vergleich).
- Ordner aus `Ignorierte Ordner` komplett ausschliessen.
