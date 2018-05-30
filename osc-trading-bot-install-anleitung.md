# OSC Trading Bot Installations- Anleitung
<br>

Dies ist eine Installations-Anleitung für Gekko, einen Open Source Cryptocurrency Trading Bot.
Diese Anleitung ist für die Installation auf Linux Debian/Ubuntu, ArchLinux, Raspbian.

<br>

#### Schritt 1: Benötigte Pakete installieren

Auf einer jungfräulichen Linux-Distribution werden zuerst mehrere Programme benötigt. Als Beispiel wird eine aktuelle Linux Mint Xfce Distribution verwendet.

> WICHTIG!<br>
> Die aktuelle Version von Node.js ist v10. Gekko benötigt jedoch v8, mit der neuesten Version ist es nicht kompatibel.

Die Pakete heißen auf verschiedenen Linux-Distributionen teilweise anders. In unserem Beispiel werden folgende Pakete benötigt:

* Node.js v8: Die Plattform, auf der Gekko basiert
* NPM: Der Paketmanager, um Module für Node.js zu installieren
* Git: Das Versionskontrollsystem, um Repositories, u.a. Gekko selbst, von GitHub zu klonen
<br>

1.1: Die Pakete inkl. Abhängigkeiten werden unter **Linux Debian/Ubuntu** mit folgenden Befehlen installiert:
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo bash -
sudo apt-get install nodejs
sudo apt-get install npm
sudo apt-get install git
```
<br>

1.2: Die Pakete inkl. Abhängigkeiten werden unter **Arch Linux** mit folgendem Befehl installiert:
```
sudo pacman -S nodejs-lts-carbon npm git
```
<br>

1.3: Für **Raspbian** lauten die Befehle wie folgt:
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo bash -
sudo apt-get install nodejs
sudo apt-get install git
```
<br>

Überprüfen  von Node.js, NPM und Git Version
```
node -v
	v8.11.2
npm -v
	5.6.0
git --version
	git version 2.7.4
```
![Version Test](https://github.com/schwarzwaldjoker/osc-trading-bot-doku/blob/master/screenshots/02_version-test.png)
*Ergebnisse von Versiontests*

<br>
<br>

#### Schritt 2: Gekko installieren


Wir benutzen den stabilen Zweig des originalen GitHub Repositories von [askmike](https://github.com/askmike/).
Das Gekko inkl. Abhängigkeiten werden unter **Linux Debian/Ubuntu, ArchLinux, Raspbian** mit folgenden Befehlen installiert:


In das Home Verzeichnis wechseln.
```
cd ~
```
<br>

Das GitHub Repository klonen.
```
git clone git://github.com/askmike/gekko.git -b stable
```
<br>

In das Gekko Verzeichnis wechseln.
```
cd gekko
```
<br>

Alle zum Ausführen von Gekko benötigten Node.js Module installieren.
```
npm install --only=production
```
NPM wird eine Warnung ausgeben, dass in einigen Modulen Sicherheitslücken (vulnerabilities) vorhanden sind, was aber ignoriert werden kann.

Somit ist Gekko mit einer Handvoll mitgelieferten Indikatoren einsatzbereit.

Gekko starten.
```
node gekko --ui
```
Der Befehl startet den Webserver und öffnet automatisch ein Browser-Fenster. Sollte keine Desktop-Umgebung bzw. kein Window-Manager laufen oder kein Browser installiert sein, beschwert sich Gekko zwar, dass der Browser nicht geöffnet werden konnte, der Webserver läuft aber und ist unter localhost auf Port 3000 erreichbar.

http://localhost:3000/

![Gekko](https://github.com/schwarzwaldjoker/osc-trading-bot-doku/blob/master/screenshots/01_gekko-ui.png)
*Gekko Start*

<br>

In der Konsole, in der Gekko ausgeführt wird, kann es mit der Tastenkombination Ctrl-C (deutsch Strg-C) beendet werden.

<br>
<br>


#### Schritt 3: Mehr Indikatoren/Strategien für Gekko

Eine Liste von Indikatoren, die hier verwendet werden:
* ichimoku
* fibo
* bollinger
* ema rainbow oder andere ema (tema,dema,)
* hull
* fibo trendlines
* BullBear oder BBRSI
* Trailing Stop
* Take Profit
* hodlgreed
* Ann
* PingPong
* Crossover
* Overbought
* Alligator
* Bodhi
* CCI
* Combination
* Scalping
* yuru
* Neuralnet
* Genetic

<br>

3.1: Zusätzliche Strategien installieren

Es gibt viele Quellen für einzelne Strategien.
Der GitHub User [xFFFFF](https://github.com/xFFFFF/) hat in einem seiner Repositories eine Sammlung mit über 40 Strategien inkl. eines Installations-Scripts zusammen getragen.
Dieses Repository klont man mit folgendem Befehl:
```
git clone --recursive https://github.com/xFFFFF/Gekko-Strategies
```
<br>

> WICHTIG!<br>
> Einige der Strategien liegen auf externen GitHub Repositories. Der Parameter
*--recursive* wird benötigt, um diese mit zu klonen, ansonsten findet man einige leere Ordner vor und einige Strategien fehlen.
<br>

In das Gekko-Strategies Verzeichnis wechseln.
```
cd Gekko-Strategies
```
<br>

Installations-Skript ausführen. Hat man Gekko, wie oben beschrieben, ins Home Verzeichnis geklont, lautet der Befehl:
```
./install.sh ~/gekko
```
Der Pfad ~/gekko muss natürlich entsprechend angepasst werden, sollte Gekko in einem anderen Ordner liegen.

<br>

3.2: Voraussetzungen für Strategien


Manche Strategien benötigen zusätzliche Konfiguration oder Pakete, um zu funktionieren.

[TODO: Welche Strategien sind das? Zumindest für Ichimoku ist oben die Liste]

* ichimoku
```
npm install --save ichimoku
npm install talib		xxx
npm install tulind		xxx
npm install mathjs
npm install convnetjs
npm install joi
npm install alligator		2x WARN
npm install zero-fill		2x WARN
npm install numbro		2x WARN
npm install gauss		2x WARN
```

    [TODO: Erklärung]

[TODO: Für jede aus dem Gekko-Strategies von xFFFFF sollten wir hier eine Liste (und evtl. Installations-Anleitung mit NPM) einfügen]



<br>
<br>


#### Schritt 4: Datensätze importieren


Gekko bietet die Möglichkeit, Strategien anhand vergangener Daten aus Charts zu testen. Dafür werden zuerst Datensätze benötigt.

4.1: Datensätze im Gekko importieren

Gekko bietet die Möglichkeit, Datensets von Exchanges, die dafür eine API anbieten, zu importieren.
Das ist unter dieser URL zu finden:

http://localhost:3000/#/data/importer

<br>

![Data Importer](https://github.com/schwarzwaldjoker/osc-trading-bot-doku/blob/master/screenshots/03_daten-import.png)
*Datensätze mit Gekko importieren (lange Wartezeiten!)*

<br>

4.2: Datensätze direkt importieren

Das Importieren dauert aber sehr lange.
Eine Alternative ist, bereits importierte Datenbanken zu verwenden.
Eine Reihe von diesen Datenbanken ist unter folgender URL zu finden:

https://drive.google.com/drive/folders/1G5yQbIG8_N2tVb1CnuK9_JNUcjo4icoo

Die Datensätse sind SQLite Datenbank Dateien. Damit Gekko sie benutzen kann, müssen sie entpakt und in diesen Ordner gelegt werden:
```
~/gekko/history
```
Sollte der Ordner noch nicht existieren, muss er vorher angelegt werden, entweder mit einem Dateimanager oder mit diesem Befehl:
```
mkdir ~/gekko/history
```

<br>

4.3 Nicht mehr benötigte Datensätze wieder entfernen

Wenn Datensätze nicht mehr benötigt werden, können diese auch wieder entfernt werden.
Dazu wird entweder die komplette Exchange- Datenbank aus dem Ordner */history* beseitigt
oder die einzelne Paare/Tabellen mit dem Tool „DB Browser for SQLite“ (GUI Anwender) bzw. das Paket SQLite3 (SSH Anwender) entfernt.

Siehe dazu die Anleitung [datensaetze-entfernen.md](datensaetze-entfernen.md)

<br>
<br>

#### Schritt 5. Strategien testen (Backtest)

Gekko bietet die Möglichkeit, eine Strategie auf einem Datensatz zu testen.
Das funktioniert aber nur für jeweils eine Strategie, d.h. es muss für jede manuell gestartet werden.

![Backtest-UI](https://github.com/schwarzwaldjoker/osc-trading-bot-doku/blob/master/screenshots/05_backtest-gekko.png)
*Gekko eigener Backtest (nur einzelne Paare und Strategien)*

<br>

5.1 Backtest Tool installieren

[xFFFFF](https://github.com/xFFFFF/) bietet in einem seiner Repositories ein Tool an,
das alle installierten Strategien nacheinander testet und die Ergebnisse sowohl in der Konsole ausgibt,
als auch in einer CSV Datei speichert.

Neueste Version von https://github.com/xFFFFF/Gekko-BacktestTool/releases herunterladen.

[Gekko-BacktestTool-v0.7-Ubuntu-amd64.zip](https://github.com/xFFFFF/Gekko-BacktestTool/releases/download/v0.7/Gekko-BacktestTool-v0.7-Ubuntu-amd64.zip)

Die .zip Datei entpacken und den Inhalt (*backtest und backtest-config.pl*) in das **Hauptverzeichnis** von Gekko kopieren.

Weitere Installations- Anleitungen findet man direkt auf GitHub von [xFFFFF](https://github.com/xFFFFF/):

https://github.com/xFFFFF/Gekko-BacktestTool

5.2 Backtest durchführen

Um den ausführlichen Backtest im Terminal zu starten wechselt man in das Gekko Hauptverzeichnis cd ~/gekko und verwendet folgenden Befehl:
```
./backtest
```
<br>

![Backtest-Tool](https://github.com/schwarzwaldjoker/osc-trading-bot-doku/blob/master/screenshots/06_backtest-tool.png)
*Backtest Tool von xFFFFF*

<br>

[TODO: Anleitung, wie man das Tool verwendet]
Zusätzliche Optionen zum *./backtest*

Mode:<br>
  -i, --import	 - Import new datasets<br>
  -g, --paper	 - Start multiple sessions of PaperTrader<br>
  -v, --convert TOMLFILE - Convert TOML file to Gekko's CLI config format, ex: backtest.pl -v MACD.toml<br>
  -a, --analyze CSVFILE	 - Perform comparision of strategies and pairs from csv file, ex: backtest.pl -a database.csv<br>

Optional parameters:<br>
  -c, --config		 - BacktestTool config file. Default is backtest-config.pl<br>
  -s, --strat STRAT_NAME - Define strategies for backtests. You can add multiple strategies seperated by commas example: backtest.pl --strat=MACD,CCI<br>
  -p, --pair PAIR	 - Define pairs to backtest in exchange:currency:asset format ex: backtest.pl --p bitfinex:USD:AVT. You can add multiple pairs seperated by commas.<br>
  -p exchange:ALL	 - Perform action on all available pairs. Other usage: exchange:USD:ALL to perform action for all USD pairs.<br>
  -n, --candle CANDLE	 - Define candleSize and warmup period for backtest in candleSize:warmup format, ex: backtest.pl -n 5:144,10:73. You can add multiple values seperated by commas.<br>
  -ft, --period DAYS - Time range in days - perform action on period from last x days ex: backtest.pl -ft 7<br>
  -f, --from		- Time range for backtest datasets or import. Example: backtest.pl --from="2018-01-01 09:10" --to="2018-01-05 12:23"<br>
  -t, --to<br>
  -f last		- Start import from last candle available in DB. If pair not exist in DB then start from 24h ago.<br>
  -t now		- 'now' is current time in GMT.<br>
  -o, --output FILENAME - CSV file name.

<br>
<br>

#### Schritt 6: Parameter Tuning für Strategien


[TODO: Dirks Parameter für Multi-Strategie, etc.]


<br>
<br>

#### Schritt 7: Produktiv-Einsatz


[TODO: Soweit ist glaub ich noch niemand]

<br>
<br>
<br>
<br>


## Quellen und nützliche Links

Gekko
https://gekko.wizb.it/

Offizielles Gekko Forum
https://forum.gekko.wizb.it/thread-1676.html

Installations- Script BannanaDJoe
https://github.com/BannanaDJoe/scripts/tree/master/gekko-scripts

GitHub Help
https://help.github.com/categories/writing-on-github/

GUI Clints für GitHub
https://git-scm.com/download/gui/linux
<br><br><br>

Videos (deutsch)<br><br>
Git Crashkurs - Was ist Git?
https://www.youtube.com/watch?v=Nkz7TnhFvWU&feature=youtu.be

SourceTree
https://www.youtube.com/watch?v=EfU4o7U_xAk
