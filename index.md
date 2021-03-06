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

# Erstelle einen neuen Ordner im aktuellen Verzeichnis
mkdir neuerOrdner

# Benenne eine Datei um. A wird umbenannt in B
mv A B

# Erstelle einen Symlink (Soft-Link)
ln -s original linked

# Entferne den Symlink. Dies entfernt nicht das "Original"
rm linked
```

## Eingaben / Ausgaben (```echo``` und ```cat```)

**Hinweis**: Wenn von Dateien gesprochen wird, dann können auch Verzeichnisse betroffen sein, da diese bei Linux ebenfalls Dateien sind.

```sh
# Etwas ausgeben
echo
# Umgebungsvariablen ausgeben
echo $HOME

# Gibt alle Dateien im aktuellen Verzeichnis aus.
# Die Shell ersetzt * durch alle Namen der Dateien im Verzeichnis.
# Versteckte Dateien werden nicht beachtet.
# Wenn im Verzeichnis KEINE Dateien sind, dann wird * gar nicht ersetzt.
echo *

# Zeige alle versteckte Dateien
echo .*

# Zeige alle Dateien, die einen Punkt im Namen enthalten. Das beinhaltet NICHT versteckte Dateien
echo *.*

# Gibt alle Dateien aus, die 3 Zeichen lang sind
echo ???

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

## Inter-Prozess-Kommunikation mittels `grep`

Unter Linux wird das Piping verwendet, um Kommunikation zwischen Prozessen herzustellen.

Mittels des Befehls `grep` können Ausgaben eines Programmes durch Regex-Anweisungen extrahiert werden.

```sh
# Gibt alle Zeilen der Datei /etc/passwd aus, die den Term "root" beinhalten.
cat /etc/passwd | grep root
```

## System

```sh
# Beinhaltet alle Benutzer des Systems
cat /etc/passwd
```

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
