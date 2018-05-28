### SQLite installieren:

##### Linux Debian/Mint
```
sudo apt-get install sqlite3 
```
##### Archlinux
```
sudo pacman -S sqlite3
```

Starten:
```
sqlite3 
```
Datenbank öffnen:
```
.open /home/DEIN-PFAD/gekko/history/BEISPIEL_0.1.db
```

Tabellen anzeigen:
```
sqlite> .tables
candles_USD_BTC  candles_USD_IOT
```

Tabelle löschen
```
sqlite> DROP TABLE candles_USD_BTC;
```

Tabellen anzeigen:
```
sqlite> .tables
candles_USD_IOT
```
SQLite verlassen:
```
sqlite> .exit
```