# Moviedatabase
Vergleichsprojekt zur Seminararbeit MSI CoffeeScript.
## Übersicht
- Der Server ist in CoffeeScript geschrieben (*src/app.coffee* und kompiliert in *dist/app.js*)
- Der Client befindet sich im *public/* Ordner (*src/clientApp.coffee* und kompiliert in *dist/clientApp.js*)
- Tests zur Vollständigkeit eingerichtet *test* mit mocha
nähere Details siehe unten.
## Installation
Installation getestet für Ubuntu ab 14.04.
### Konfiguration
Datei *config/defaultExample.json* kopieren und umbenennen in *default.json*. Je nach Umgebung die Werte anpassen.

### Nodejs und Dependencies
node js mit nvm installieren. 
```
curl https://raw.githubusercontent.com/creationix/nvm/v0.11.1/install.sh | bash
source ~/.profile
nvm ls-remote
nvm install v4.6.2
nvm use v4.6.2
node --version
```
nvm Version _v4.6.2_ benutzen.
Gegebenenfalls node Version einstellen, falls node Befehle nicht funktionieren.
```
nvm ls
nvm use v4.6.2
node --version
```

Dependencies installieren (*coffee-script, docco, express, mocha, should*):
```
npm install
```
Einige Symlinks werden benötigt (Cakefile).
```
sudo ln -s /home/<path inside your home folder>/Moviedatabase/node_modules/coffee-script/bin/cake /usr/local/bin/cake
sudo ln -s /home/<path inside your home folder>/Moviedatabase/node_modules/docco/bin/docco /usr/local/bin/docco
sudo ln -s /home/<path inside your home folder>/Moviedatabase/node_modules/mocha/bin/mocha /usr/local/bin/mocha
```
Moviedatabase dann starten mit 
```
node ./dist/app.js
```
Je nach *config/default.json* Einstellung erreichbar unter:
```
localhost:5001
```

## Cake Befehle:
In der Präsentation wurde Cakefile und Sourcemaps vorgestellt. Hier nochmals eine Übersicht über die implementierten Befehle:
```
cake --map build
cake --map watch
cake docs
cake test
cake clean
```
Als Vorlage für die Cakefile diente [dieses Template](http://twilson63.github.io/cakefile-template/).
### Sourcemaps
Kleine Anmerkungen zu Sourcemaps:
 - probleme in firefox 53.0.2 (in chrome funktioniert alles)
 - sourcemap angaben passen nicht zum webserver (files liegen in public ordner)
 - coffeescript Option -M (inline sourcemaps) ging nicht

## Dokumentation
Zwei Beispiele zur Dokumentation: [docco](https://jashkenas.github.io/docco/) und literate Programming (CoffeeScript).
### docco
Die Cakefile genertiert mit *cake docs* mittels [docco](https://jashkenas.github.io/docco/) eine Dokumentation, die man sich unter
```
localhost:5001/app.html
localhost:5001/clientApp.html
```
anschauen kann (je nach config) und liegt im *docs/* Ordner.
### literate Programming
Unter *public/literateProgramming* ist ein Abbild von *public/src/clientApp.coffee* einmal als .litcoffee und .litcoffee.md. 

Die Datei .litcoffee kann compiliert werden (wie eine .coffee Datei):
```
coffee -c clientApp.litcoffee
```
Die Dateiendung .md ermöglicht die Darstellung für Markdown siehe [clientApp.litcoffee.md](https://github.com/chappy2/Moviedatabase/blob/master/public/literateProgramming/clientApp.litcoffee.md).
