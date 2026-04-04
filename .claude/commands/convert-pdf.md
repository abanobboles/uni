Konvertiere die angegebene PDF-Datei (oder alle PDFs in einem Ordner) nach Markdown mit `markitdown`.

Angabe (Dateipfad oder Ordnerpfad): $ARGUMENTS

## Ablauf

1. Falls ein Ordnerpfad angegeben ist: Finde alle PDF-Dateien im Ordner, fuer die noch keine gleichnamige `.md`-Datei existiert.
2. Falls ein einzelner Dateipfad angegeben ist: Pruefe, ob bereits eine gleichnamige `.md`-Datei existiert.
3. Erzeuge fehlende Markdown-Dateien mit: `markitdown datei.pdf > datei.md`
4. Melde, welche Dateien konvertiert wurden und welche bereits vorhanden waren.
