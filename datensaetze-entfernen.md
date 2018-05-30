# Nicht mehr benötigte Datensätze wieder entfernen

Wenn Datensätze nicht mehr benötigt, können diese auch wieder entfernt werden. Dazu wird entweder die komplette Exchange- Datenbank aus dem Ordner /history beseitigt oder die einzelne Paare/Tabellen mit dem Tool „DB Browser for SQLite“ (GUI Anwender) bzw. das Paket SQLite3 (SSH Anwender) entfernt.

4.3.1 Komplette  Exchange- Datenbank löschen

Mit **Dateimanager** zum Verzeichnis *~/gekko/history* Navigieren und die entsprechende Datenbank.db löschen.

<br>

4.3.2 Mit [DB Browser for SQL Lite](https://wiki.ubuntuusers.de/SQLite_Database_Browser/) einzelne Tabellen löschen

DB Browser for SQL Lite über die Anwendungsverwaltung nachinstallieren, starten, zum *~/gekko/history* Verzeichnis navigieren, entsprechende Datenbank.db öffnen (1) und einzelne Tabellen/Paare löschen (2).

                                  sreenshot DB browser

<br>

4.3.3 Mit [SQLite3](https://wiki.ubuntuusers.de/SQLite/) per Eingabebauforderung einzelne Tabellen löschen

SQLite installieren:

**Linux Debian/Ubuntu, Raspbian**
```
sudo apt-get install sqlite3
```
<br>

**Archlinux**
```
sudo pacman -S sqlite3
```
<br>

SQLite3 Starten:
```
sqlite3 
```
<br>

Datenbank öffnen:
```
.open /home/DEIN-PFAD/gekko/history/BEISPIEL_0.1.db
```
<br>

Tabellen anzeigen:
```
sqlite> .tables
candles_USD_BTC  candles_USD_IOT
```
<br>

Tabelle löschen
```
sqlite> DROP TABLE candles_USD_BTC;
```
<br>

Tabellen anzeigen:
```
sqlite> .tables
candles_USD_IOT
```
<br>

SQLite verlassen:
```
sqlite> .exit
```
<br>


