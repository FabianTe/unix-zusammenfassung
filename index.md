# Linux Einführung

## Arbeiten im Dateisystem

```sh
# Verzeichnis wechseln
cd /
cd /home
# Zum Home-Verzeichnis wechseln
cd
cd $HOME

# Absoluter Pfad
pwd

# Verzeichnis listen
ls
# Verzeichnis als Liste listen
ls -l

# Setzen des Änderungsdatums einer Datei auf den aktuellen Zeitpunkt
touch text.txt # Das Änderungsdatum der Datei text.txt ist jetzt gesetzt
# Besonderer Fall: Wenn text.txt nicht existiert, wird sie als neue, leere Datei angelegt!

# Neue Datei anlegen
>leereDatei
# Sonderzeichen beachten!
>leere\ Neue Datei
```

## Eingaben / Ausgaben
```sh
# Etwas ausgeben
echo
# Umgebungsvariablen ausgeben
echo $HOME
```

## Hilfen / Sonstiges
```sh
# Hilfe zum Befehl ... ausgeben
man ...
man echo # Hilfe für echo ausgeben
```

## Tipps / Tricks

**ACHTUNG: Diese Befehle sind nicht Teil der Vorlesung, für einige könnten sie allerdings ganz interessant sein.**

### Alias für Befehl erstellen

Den Befehl ```cls```gibt es in Linux standardmäßig nicht. Bei Windows würde ```cls``` das Terminal leeren. Mittels ```alias``` kann man bspw. den Befehl ```cls``` selbst festlegen.

```sh
alias cls=clear
```

Eine Ausführung von ```cls``` führt nun den Befehl ```clear``` aus!
