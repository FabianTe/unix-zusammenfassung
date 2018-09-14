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

## Eingaben / Ausgaben (```echo``` und ```cat```)
```sh
# Etwas ausgeben
echo
# Umgebungsvariablen ausgeben
echo $HOME

# Setzte den Inahlt der Datei test.txt zu "Hallo Welt!" Ersetzt bestehenden Inahlt!
echo Hallo Welt! >test.txt

# Gibt den Inhalt einer Datei im Terminal aus
cat test.txt 

# Leitet die folgenden Terminaleingaben in die Datei test.txt um.
cat >test.txt

# Leitet den Inhalt der Datei A in die Datei B um
cat <A >B
```

**Achtung:** Das Umleiten der Eingaben / Ausgaben übernimmt die Shell! Der eigentliche Prozess (```cat``` in den obrigen Beispielen) bekommt davon gar nichts mit, da dieser auf die Dateien im Ordner ```/proc/.../fd``` zugreift (```...``` ist die PID des Prozesses).

Außerdem übernimmt die Shell außerdem das ersetzen von bspw. Umgebungsvariablen wie ```$HOME```. Davon bekommen die eigentlichen Prozesse ebenfalls nichts mit!

## Prozesse
```sh
# Zeigt die aktiven Prozesse der aktiven Session inkl. Details aus.
ps

# ps erweitert um Informationen zu TTY (mit welchem Terminal ist der Prozess verbunden) und STAT (Status des Prozesses)
ps -x
```

### ```stdin, stdout, sterr``` eines Prozesses anzeigen

Jeder Prozess verfügt über 3 geöffnete Dateien, in die Standardausgaben, Fehler geschrieben und Eingaben gelesen werden. Diese können, wenn die PID eines Prozesses bekannt ist (siehe ```ps```), angezeigt werden:

```sh
# Angenommen die PID ist 8473
ls -l /proc/8473/fd
```

Werden beispielsweise via ```cat > Ausgabe.txt``` die Terminal-Eingaben in eine Datei umgeleitet, dann wird auffallen, dass eine der 3 Dateien umgeleitet ist auf ```Ausgabe.txt```.

## Hilfen
```sh
# Hilfe zum Befehl ... ausgeben
man ...
man echo # Hilfe für echo ausgeben
```

Ansonsten hat fast jeder Befehl die Option ```-h```:

```sh
# Zeigt die Hilfe für den Befehl mkdir an.
mkdir -h
```

## Tipps / Tricks

**ACHTUNG: Diese Befehle sind nicht Teil der Vorlesung, für einige könnten sie allerdings ganz interessant sein.**

### Alias für Befehl erstellen

Den Befehl ```cls```gibt es in Linux standardmäßig nicht. Bei Windows würde ```cls``` das Terminal leeren. Mittels ```alias``` kann man bspw. den Befehl ```cls``` selbst festlegen.

```sh
alias cls=clear
```

Eine Ausführung von ```cls``` führt nun den Befehl ```clear``` aus!
