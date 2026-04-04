Fuehre einen Sync fuer das angegebene Fach durch.

Fachnummer oder Fachname: $ARGUMENTS

## Ablauf

1. Identifiziere das Fach anhand der Angabe. Falls die Zuordnung unklar ist, liste alle Faecher auf oberster Ebene nummeriert auf und frage nach.
2. Stelle sicher, dass im Fach eine `DB.md` existiert. Falls nicht, lege eine an.
3. Pruefe `DB.md` auf den Abschnitt `Ignorierte Ordner` und schliesse diese Ordner fuer den gesamten Sync aus.
4. Durchsuche den verbleibenden Fachordner nach PDF-Dateien, fuer die noch keine gleichnamige `.md`-Datei existiert.
5. Erzeuge fehlende Markdown-Dateien mit `markitdown`.
6. Gehe die vorhandenen Markdown-Dateien durch (insbesondere PDF-Konvertierungen und Video-Transkriptionen).
7. Pruefe, ob darin Hinweise auf Hausaufgaben, Abgaben, Fristen, Pruefungen oder wichtige To-dos enthalten sind.
8. Trage relevante Ergebnisse strukturiert in `DB.md` ein oder aktualisiere bestehende Eintraege.

## Performance-Regeln

- Zuerst ueber Dateinamen und vorhandene Markdown-Ableitungen arbeiten, bevor Inhalte gelesen werden.
- PDFs nicht direkt lesen, wenn stattdessen eine Markdown-Konvertierung erstellt werden kann.
- Fuer inhaltliche Pruefung nur die `.md`-Dateien verwenden.
- Ordner aus `Ignorierte Ordner` komplett ausschliessen.
- Nur das angegebene Fach bearbeiten, nicht das gesamte Repository.
- `DB.md` aktuell halten fuer kuenftige Chats.
