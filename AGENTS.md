# Studienprojekt-Regeln

Dieses Repository enthaelt die Unterlagen fuer mein Theologiestudium.

## Ziel des Projekts

Alle Inhalte aus Moodle sollen lokal in diesem Projekt abgelegt werden, damit wir gemeinsam damit arbeiten koennen: lernen, Hausaufgaben bearbeiten, Inhalte zusammenfassen und neue Materialien erstellen.

## Ordnerstruktur

- Jeder Fachbereich hat einen eigenen Ordner auf oberster Ebene.
- In jedem Fachordner gibt es genau diese beiden Unterordner:
  - `Moodle`
  - `Notes`
- In jedem Fachordner gibt es zusaetzlich eine Datei:
  - `DB.md`
- Im Projektwurzelordner gibt es zusaetzlich eine zentrale Datei:
  - `README.md`

## Bedeutung der Ordner

### `Moodle`

In `Moodle` liegen alle Inhalte, die aus Moodle stammen, zum Beispiel:

- PDFs
- Word-Dateien
- Praesentationen
- Arbeitsblaetter
- Videos
- weitere Originaldateien aus Moodle

Innerhalb von `Moodle` existieren in der Regel weitere Unterordner fuer verschiedene Einheiten, Sitzungen oder Themen.

Diese Einheitenordner enthalten die zugehoerigen Materialien der jeweiligen Einheit, zum Beispiel:

- Vortraege
- Handouts
- PDFs
- Videos
- Transkriptionen als Markdown

Wichtig:

- Material, das fachlich zusammengehoert, kann in unterschiedlichen Einheitenordnern liegen.
- Zum Beispiel koennen Vortrag, Video und Transkription in einem Einheitenordner liegen, waehrend die dazugehoerige PowerPoint in einem anderen Einheitenordner abgelegt ist.
- Der Assistent soll deshalb nicht nur nach dem Ordnerkontext, sondern auch nach Dateinamen, Thema und inhaltlicher Zuordnung arbeiten.

### `Notes`

In `Notes` liegen alle Inhalte, die wir selbst erarbeiten oder erstellen, zum Beispiel:

- Lernnotizen
- Zusammenfassungen
- Aufgabenloesungen
- Uebersichten
- Entwuerfe
- gemeinsam erstellte Materialien

### `DB.md`

Jeder Fachordner enthaelt eine `DB.md` als arbeitsbezogenen Memory-Speicher fuer den Assistenten.

Diese Datei dient dazu, pro Fach eine laufende Uebersicht zu behalten, damit wichtige Informationen auch in spaeteren Chats schnell wieder auffindbar sind.

In `DB.md` koennen unter anderem stehen:

- offene Hausaufgaben
- Abgaben und Fristen
- Pruefungstermine
- wichtige organisatorische Hinweise
- Dinge, auf die besonders zu achten ist
- offene Fragen
- kurze Zusammenfassungen des aktuellen Stands

Regeln fuer `DB.md`:

- Vor inhaltlicher Arbeit in einem Fach nach Moeglichkeit zuerst `DB.md` lesen.
- Wenn es neue wichtige Informationen gibt, `DB.md` aktualisieren.
- Nur fachbezogene und nuetzliche Arbeitsinformationen eintragen.
- Kurz, klar und uebersichtlich schreiben.
- Bereits erledigte Punkte als erledigt markieren oder sauber in einen passenden Abschnitt verschieben, statt die Datei unstrukturiert wachsen zu lassen.
- Wenn es fachbezogene Ordner gibt, die standardmaessig nicht bearbeitet werden sollen, diese in `DB.md` in einem eigenen Abschnitt `Ignorierte Ordner` fuehren.

### `Ignorierte Ordner` in `DB.md`

Ein Fach kann in seiner `DB.md` einen Abschnitt `Ignorierte Ordner` enthalten.

Regeln dafuer:

- Alle dort gelisteten Ordner sind standardmaessig von `Sync`-Laeufen ausgeschlossen.
- Diese Ordner werden auch bei normalen inhaltlichen Arbeiten nicht beruecksichtigt, zum Beispiel bei:
  - Zusammenfassungen
  - Lernnotizen
  - Aufgabenpruefung
  - Termin- und Fristenextraktion
  - allgemeinen inhaltlichen Rueckfragen zum Fach
- Dateien in solchen Ordnern sollen nur dann einbezogen werden, wenn der Nutzer den Ordner oder konkrete Dateien daraus ausdruecklich nennt oder ihre Einbeziehung klar wuenscht.
- Bei `Sync` bedeutet das: Diese Ordner werden standardmaessig weder inhaltlich durchgegangen noch fuer PDF-zu-Markdown-Konvertierungen oder To-do-Extraktionen priorisiert.

### `README.md`

Die `README.md` im Projektwurzelordner ist die zentrale Start- und Uebersichtsdatei fuer das gesamte Studien-Repository.

Sie soll kompakt enthalten:

- eine Liste aller Faecher im Repository
- die Grundstruktur des Projekts
- kurze, wichtige Ueberblicksinformationen aus den jeweiligen `DB.md`-Dateien

Regeln fuer `README.md`:

- Wenn neue Faecher hinzukommen, `README.md` aktualisieren.
- Wenn sich wichtige fachliche Informationen in einer `DB.md` aendern, die zentrale Uebersicht in `README.md` mitaktualisieren.
- `README.md` dient als Schnellueberblick und ersetzt nicht die detaillierten `DB.md`-Dateien in den Fachordnern.
- Nur die wichtigsten Punkte aus `DB.md` in komprimierter Form uebernehmen.

## Umgang mit PDFs

- Jedes PDF soll zusaetzlich als Markdown-Datei mit demselben Namen vorliegen.
- Beispiel:
  - `Skript.pdf`
  - `Skript.md`
- PDF-Dokumente sollen inhaltlich nicht direkt ausgewertet, zitiert oder als primaere Textquelle verwendet werden.
- Fuer inhaltliche Arbeit soll immer die konvertierte Markdown-Datei mit demselben Namen verwendet werden.
- Wenn eine passende Markdown-Datei existiert, soll ausschliesslich die Markdown-Datei verwendet werden statt direkt im PDF zu arbeiten oder daraus zu lesen.
- Die Umwandlung von PDF nach Markdown erfolgt mit `markitdown`.

Verwendung:

```bash
markitdown path-to-file.pdf > document.md
markitdown path-to-file.pdf > document.md
cat path-to-file.pdf | markitdown
```

## Umgang mit Videos

- Zu jedem Video soll es eine Markdown-Datei mit demselben Namen geben, die die Transkription enthaelt.
- Beispiel:
  - `Vorlesung1.mp4`
  - `Vorlesung1.md`
- Wenn eine passende Markdown-Datei zur Transkription existiert, soll bevorzugt diese Datei verwendet werden statt das Video selbst auszuwerten.
- Die Video-Transkriptionen werden manuell erstellt.
- Video-Dateien im Format `mp4` sollen nicht in Git einbezogen werden.
- Fuer Git soll eine `.gitignore` verwendet werden, die `*.mp4` ausschliesst.

## Arbeitsweise fuer den Assistenten

- Bevorzugt in vorhandenen `.md`-Dateien nachschauen, wenn diese zu PDFs oder Videos gehoeren.
- PDFs nicht als Textquelle benutzen, wenn eine gleichnamige Markdown-Datei vorhanden ist oder erzeugt werden kann.
- Originaldateien in `Moodle` nicht unnoetig veraendern.
- Eigene inhaltliche Ausarbeitungen, Zusammenfassungen oder Lernhilfen in `Notes` ablegen, sofern der Kontext nichts anderes verlangt.
- Die bestehende Fachstruktur beibehalten und nicht ohne Grund umorganisieren.
- Neue Dateien so benennen, dass die Zuordnung zu Fach, Thema und Quelle klar bleibt.
- Pro Fach `DB.md` als ersten Ueberblickspunkt fuer Aufgaben, Termine und wichtige Hinweise nutzen.
- Pro Fach auch einen moeglichen Abschnitt `Ignorierte Ordner` in `DB.md` beachten und diese Ordner standardmaessig auslassen.
- `README.md` als zentrale Projektuebersicht nutzen und bei relevanten Aenderungen mitpflegen.
- Bei Materialien in `Moodle` beachten, dass zusammengehoerige Dateien ueber mehrere Einheitenordner verteilt sein koennen.
- MP4-Dateien als grosse Originalmedien behandeln und nicht fuer Git-Tracking vorsehen.

## Sync-Befehl

Wenn der Nutzer einen `Sync` fuer ein Fach anfordert, erfolgt die Arbeit immer fachbezogen.

### Bedeutung von Fachnummer

- Die Fachnummer bezieht sich auf einen Fachordner auf oberster Ebene.
- Falls die Zuordnung der Nummer nicht eindeutig aus dem bisherigen Kontext hervorgeht, zuerst die verfuegbaren Faecher geordnet auflisten und die Nummern dazu verwenden.

### Ablauf bei `Sync`

Bei einem `Sync` fuer ein Fach soll der Assistent moeglichst effizient in dieser Reihenfolge arbeiten:

1. Das angegebene Fach identifizieren.
2. Sicherstellen, dass im Fach eine `DB.md` existiert; falls nicht, eine anlegen.
3. `DB.md` auf einen Abschnitt `Ignorierte Ordner` pruefen und diese Ordner fuer den aktuellen `Sync` standardmaessig ausschliessen.
4. Den verbleibenden Fachordner durchsuchen und alle PDF-Dateien finden, fuer die noch keine gleichnamige `.md`-Datei existiert.
5. Diese fehlenden Markdown-Dateien mit `markitdown` erzeugen.
6. Danach die vorhandenen fachbezogenen Markdown-Dateien durchgehen, insbesondere die aus PDF-Konvertierungen und Video-Transkriptionen.
7. Pruefen, ob darin Hinweise auf Hausaufgaben, Abgaben, Fristen, Pruefungen oder wichtige To-dos enthalten sind.
8. Relevante Ergebnisse strukturiert in `DB.md` eintragen oder aktualisieren.

### Performance-Regeln fuer `Sync`

- Zuerst ueber Dateinamen und vorhandene Markdown-Ableitungen arbeiten, bevor Inhalte gelesen werden.
- PDFs nicht direkt inhaltlich lesen, wenn stattdessen eine Markdown-Konvertierung erstellt werden kann.
- Fuer die inhaltliche Pruefung bevorzugt nur die vorhandenen `.md`-Dateien verwenden.
- Ordner aus der `Ignorierte Ordner`-Liste eines Fachs standardmaessig komplett aus dem Sync-Arbeitslauf ausschliessen.
- Nur das Fach bearbeiten, das beim `Sync` angefordert wurde, nicht das gesamte Repository.
- `DB.md` als zentrale Uebersicht aktuell halten, damit kuenftige Chats schneller und konsistenter arbeiten koennen.

## Benennungskonvention

- Wenn moeglich, soll eine Markdown-Datei denselben Basisnamen wie die zugehoerige Quelldatei tragen.
- Beispiele:
  - `Literaturliste.pdf` -> `Literaturliste.md`
  - `Sitzung-03.mp4` -> `Sitzung-03.md`
- Die Memory-Datei eines Fachs heisst immer exakt `DB.md`.

## Prioritaeten

1. Bestehende Fachstruktur respektieren.
2. Moodle-Materialien in `Moodle` ablegen.
3. Eigene Ausarbeitungen in `Notes` ablegen.
4. Wenn vorhanden, mit den Markdown-Ableitungen von PDF und Video arbeiten.
5. `DB.md` pro Fach als laufende Uebersicht pflegen.
6. `README.md` als zentrale Faecher- und Statusuebersicht aktuell halten.
7. Inhalte so strukturieren, dass gemeinsames Lernen und Weiterarbeiten einfach moeglich ist.
