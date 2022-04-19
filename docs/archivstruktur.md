# Struktur der ZIP-Datei

## Dateiname

Der Dateiname besteht aus:

- dem String *Infodb*
- einem Unterstrich
- Ihrem Kundennamen
- einem Unterstrich
- dem Zeitstempel der Datenerzeugung im Format (`JJJJMMTTHHnnss`)
- der Endung *.zip*

### Beispiel

```
Infodb_Mustermann_20220418082907.zip
```

## Inhalt der ZIP-Datei

In der ZIP-Datei befinden sich:

- ein oberstes Verzeichnis *Infodatenbanken*
- darunter ein Verzeichnis mit dem Zeitstempel (wie im Dateinamen, jedoch im Format `JJJJ-MM-TT_HH-nn-ss`)
- unterhalb des Zeitstempel-Verzeichnisses: ein Verzeichnis *CSV* mit allen CSV-Dateien
- unterhalb des Zeitstempel-Verzeichnisses: ein Verzeichnis *SQLite* mit allen Datensätzen in einer SQLite-Datenbank (nur für Abo-Kunden)
- unterhalb des Zeitstempel-Verzeichnisses: ein Verzeichnis *SQL* mit allen Datensätzen in SQL-Skripten mit INSERT-Statements für den einfachen Import in eine SQL-Datenbank (nur für Abo-Kunden)

### Beispiel

```
Infodatenbanken
  2022-04-18_08-29-07
    CSV
      LAND.csv
      PLZ.csv
      ...
    SQL
      LAND.sql
      PLZ.csv
      ...
    SQLite
      Infodb.db3
```

!!! tip

    Diese Form der Verzeichnisstruktur im ZIP-Archive erlaubt es Ihnen, mehrere ZIP-Archiv nacheinander (immer wenn Sie einen neuen Datenstand holen) in das gleiche Basisverzeichnis (hier: Infodatenbanken) zu entpacken. Sie erhalten dann darunter für jeden Datenstand ein Unterverzeichnis mit dem jeweiligen Zeitstempel.
