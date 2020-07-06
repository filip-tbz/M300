# M300

K1 
=======

## VirtualBox

*Vorbereitungen für die VM Erstellung*

1. Als erstes auf [dieser Webseite](https://www.virtualbox.org) VirtualBox heruntergeladen und danach GUI-basiert installiert. Keine Speziellen einstellungen vornehmen bei der GUI-basierten installation.
2. Danach Ubuntu Desktop 20.04 auf [dieser Webseite](https://www.ubuntu.com/#download) heruntergeladen. 

*VM erstellen mit Virtualbox*

1. VirtualBox starten
2. Mit einem klick auf `Neu` eine neue VM erstellen.
3. Als nächstes muss man folgende Attribute angeben:
   *  Name:           `m300_ubuntu`
   *  Typ:            `Linux`
   *  Version:        `Ubuntu (64-bit)`
   *  Speichergrösse: `2048 MB`
   *  Platte:         `[X] Festplatte erzeugen`
4. Nun auf `Erzeugen` klicken
5. Im nächsten Fenster, folgende Informationen eintragen:
   *  Dateipfad:                       standard
   *  Dateigrösse:                     `10.00 GB`
   *  Dateityp der Festplatte:         `VMDK (Virtual Maschine Disk)`
   *  Storage on physical hard disk:   `dynamisch alloziert`
6. Nun erneut auf `Erzeugen` klicken, dann im Hauptmenü die VM anwählen (blau markiert) und den Punkt `Ändern` aufrufen
7. Im Abschnitt `Massenspeicher` den SATA-Controller anwählen und auf das CD+Symbol klicken
8. Unter `Medium auswählen` das zuvor heruntergeladene Systemabbild (ISO-Datei) anwählen
9. Alle Änderungen speichern und die VM starten
10. Nun den Installationsanweisungen der OS-Installation folgen. 


*Folgende Befehle ausführen in der Bash der VM.*

1. Paketliste neu einlesen und Pakete aktualisieren:
   ```Shell 
   $  sudo apt-get update   #Paketlisten des Paketmanagement-Systems "APT" neu einlesen
   
   $  sudo apt-get update   #Installierte Pakete wenn möglich auf verbesserte Versionen aktualisieren

   $  sudo reboot           #System-Neustart durchführen
   ```
2. Software Controlcenter "Synaptic" installieren:
   ```Shell 
   $  sudo apt-get install synaptic
   ````
3. Nach erfolgreicher Installation in der Suche nach "Synaptic Package Manager" suchen und diesen starten
4. Innerhalb des Managers nach "apache" (Webserver-Programm) suchen und dieses (inkl. aller Abhängigkeiten) installieren
5. System-Neustart durchführen:
   ```Shell 
   $  sudo reboot
   ```
6. Prüfen ob der Standard-Content des Webservers unter "http://127.0.0.01:80" erreichbar ist.


## Vagrant
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*Vagrant installation*

Zuerst habe ich Vagrant auf [dieser Webseite](https://www.vagrantup.com/ "vagrantup.com")   heruntergeladen und GUI-Basiert installiert.

*Mit Vagrant eine VM erstellt.*
1. Bash öffnen
2. In Ordner für die VM installation gehen:
    ```Shell
      $ cd C:\User\filip\Documents\Modul_300

    ``` 
3. Vagrantfile erzeugen, VM erstellen und starten:
    ```Shell
      $ vagrant box add http://10.1.66.11/vagrant/ubuntu/xenial64.box --name ubuntu/xenial64  #Vagrant-Box vom Netzwerkshare hinzufügen
      $ vagrant init ubuntu/xenial64        #Vagrantfile erzeugen
      $ vagrant up --provider virtualbox    #Virtuelle Maschine erstellen & starten
    ``` 
4. Die VM ist nun bereit und kann mit SSH-Zugriff bedient werden:
    ```Shell
      $ cd C:\Users\filip\Documents\Modul_300    #Zum Verzeichnis der VM wechseln
      $ vagrant ssh                       #SSH-Verbindung zur VM aufbauen
     ```

*VM erstellen mit Apache Webserver mit abgeändertem  Vagrantfile erstellt:*

1. Bash öffnen
2. In das M300-Verzeichnis wechseln:
    ```Shell
      $ cd C:\Users\filip\Documents\Modul_300
     ```
3. VM erstellen und starten:
    ```Shell
      $ vagrant up
    ``` 
4.Webbrowser prüfen, ob der Standard-Content des Webservers unter "http://127.0.0.01:8080" (localhost) erreichbar ist
5. Später habe ich im Ordner `$home\var\www\web` die Hauptseite `index.html` editieren und das Resultat überprüfen.
6. Abschliessend habe die VM  löschen:
    ```Shell
      $ vagrant destroy -f
    ```

## Visual Studio Code
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*Visual Studio Code installieren und konfigurieren.*

1. Visual Studio Code auf [dieser](https://code.visualstudio.com/"visualstudio.com") Seite heruntergelden und GUI-basiert installieren.
2. Danach im Editor drei wichtige Extensions hinzugefügt:

* Markdown All in One (von Yu Zhang)
* Vagrant Extension (von Marco Stanzi)
* vscode-pdf Extension (von tomiko1207)

Dazu folgende Anweisungen befolgen: 

  1. Visual Studio Code öffnen
  2. Die Tastenkombination `CTRL` + `SHIFT` + `X` drücken und in der Suchleiste die erwähnten Extensions suchen.
  3. Auf `Install` klicken und anschliessend auf `Reload`, um die Extension in den Arbeitsbereich zu laden.

*Dokumentation lokal mit Visual Studio Code zu bearbeiten*

  1. Änderungen am Readme-File von meinem Repositorys vornehmen
  2. Datei speichern und in der linken Leiste das Symbol mit einer "1" aufrufen
  3. Unter dem Abschnitt *Changes* die betroffenen Files bezüglich ihres Changes "stagen"
  4. Nachricht hinterlegen und Haken setzen
  5. Bei den 3 Punkten (...) auf *Push* klicken
  6. Warten, bis Dateien vollständig gepusht wurden

## Git-Client
> [⇧ *Nach oben*](#inhaltsverzeichnis)


*Client installieren*
Client-Installation auf [dieser](https://git-scm.com/downloads) Seite heruntergeladen und GUI-basiert installieren.

*Den Client konfiguriert:*
1. Bash öffnen
2. Git konfigurieren mit Informationen des GitHub-Accounts:
    ```Shell
      $ git config --global user.name "<filip-tbz>"
      $ git config --global user.email "<filipstevanoviic@gmail.com>"
    ``` 

*Repository heruntergeladen, um lokal zu arbeiten.*

1. Bash öffnen
2. Ordner für Repository erstellen:
    ```Shell
      $ cd C:\Users\djord\Documents\Modul_300
      $ mkdir MeinLokalesRepository
     ```
3. Repository mit SSH klonen:
    ```Shell
      $ git clone git@github.com:djordje-tbz/LB02.git

      Cloning into 'lb2'...
    ``` 
4. Repository aktualisieren und Status anzeigen:
    ```Shell
      $ git pull

      Already up to date.
    ```

## SSH-Key 
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*SSH-Key erstellen lokal*

1.  Folgenden Befehl mit der Account-E-Mail von GitHub in Bash einfügen:
    ```Shell
      $  ssh-keygen -t rsa -b 4096 -C "filipstevanoviic@gmail.ch"
    ```
2. Neuer SSH-Key wird erstellt:
    ```Shell
      Generating public/private rsa key pair.
    ```
3. Bei der Abfrage, unter welchem Namen der Schlüssel gespeichert werden soll, die Enter-Taste drücken (für Standard):
    ```Shell
      Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
    ```
4.Passwort für den Key festgelegt:
    ```Shell
      Enter passphrase (empty for no passphrase): [Passwort]
      Enter same passphrase again: [Passwort wiederholen]
    ```
*SSH-Key dem Client hinzufügen*

1. Auf www.github.com im Benutzerkonto *Settings* aufrufen
2.  Unter den Menübereichen auf der linken Seite zum Abschnitt *SSH und GPG keys* wechseln
3.  Auf *New SSH key* klicken
4.  Im Formular unter *Title* die Bezeichnung MB SSH-Key vergeben
5.  Den Key von der Datei *C:\Users\User\.ssh\id_rsa.pub* einfügen und auf *Add SSH key* klicken

*SSH Zugriff auf VM*

SSH Zugriff auf VM:
```shell
vagrant ssh
```
K2
======

*Github Account erstellt*
1. Auf [GitHub.com](https://github.com) gehen
2. Auf *Sign up* klicken
3. Username, E-mail und Passwort eingeben sowie Aufgabe zum verifizieren lösen
4. Auf *Create an Account* klicken

*Mark Down Extension Visual Studio Code hinzufügen*
1. Virtual Studio Code öffnen
2. *CTRL* + *SHIFT* + *X* drücken und nach Mark Down suchene. 
3. Auf *install* klicken.

K3
======

## Netzwerkumgebung

!Probleme beim Einfügen!

## Docker installation

Ich habe Docker auf meiner Ubuntu VM installiert. Die Installation habe ich gemacht mit dieser Anleitung hier: https://docs.docker.com/engine/install/ubuntu/

Folgende Befehle habe ich ausgeführt: 
1. Test ob es schon Installiert ist - ältere Version:
   ```Shell 
   $ sudo apt-get update
   $ sudo apt-get install docker-ce docker-ce-cli containerd.io
   ````
2. Die Installation
   ```Shell 
   $ sudo apt-cache madison docker-ce
   ````
3. Test ob die Installation funktioniert
   ```Shell 
   $ sudo docker run hello-world
   ````
   
   ## Backend und Frontend Container
Ich habe zwei Container erstellt. Einen Apache Server im Backend und einen Mysql Server im Frontend: 
   
Apache Server: 
   ```Shell 
   $ docker container run -d -p 8081:80 --name MyApache httpd
   ````
Mysql Server: 
   ```Shell 
   $ docker container run -it -p 8082:80 mysql
   ````
Danach habe ich in der VM http://localhost:8081 aufgerufen, um zu sehen, dass der Apache Server läuft. 

   ## Wichtige Docker Befehle
   | Befehl              | Funktion       |
| ------------------- | -------------- |
| `docker ps -a`      | Dadurch werden Container aufgelistet.|
| `docker container ls -a`        | Dadurch werden Container aufgelistet, auch die offline.|
| `docker ps -aq`       | Dadurch werden alle Container gestoppt.|
| `docker container stop [ID]`    | Dadurch wird ein Container beendet. |

## Wordpress

Ich habe zuerst ein .yml File erstellt mit Visual Code Studio. Danach habe ich sie mir per Mail gesendet, damit ich das File auf meiner Ubuntu Maschine habe. Ich habe zusätzlich das Verzeichnis /lib/docker/wp/ erstellt. Dort legte ich das File ab. Das File habe ich Folgendermassen benannt: docker-compose.yml

Im Terminal d führte folgenden Befehl aus: 

1. Um Docker Compose zu installieren:
   ```Shell 
   $ apt install docker-compose
   ````
2. Danach ging ich in das Verzeichnis /lib/docker/wp/ und führte folgendes aus: 

   ```Shell 
   $ docker-compose up -d
   ````
K4
=====

## Speicher Begrenzung

Mit einer Speicher Begrezung schützt man sich vor Speicherlecks und DoSAttacken: 

   ```Shell 
   $ ocker run -m 128m --memory-swap 128m amouat/stress stress --vm 1 --vm-bytes 127m -t 5s
   ````
## Neustart Begrenzung

Eine Begrenzung des Neustartes ist intelligent, da wenn ein Container nicht richtig funktioniert und die ganze Zeit abschmiert, werden nach einer bestimmten Anzahl Neustarts nicht mehr ressourcen verwendet für den Neustart.

   ```Shell 
   $ docker run -d --restart=on-failure:10 httpd
   
   $ docker run -d --restart=on-failure:10 mysql
   ````

## Ressourcenbeschränkung

   ```Shell 
   $ docker run --ulimit cpu=12=14 amouat/stress stress --cpu 1
   ````
 ## Cadvisor 
 
 Ich habe versucht, dass Monitoring Tool zu installieren, was leider aber nicht richtig funktioniert hat. Ich hab es mit diesem Befehl versucht: 
 
    ```Shell 
   $ docker run -d --name cadvisor -v /:/rootfs:ro -v /var/run:/var/run:rw -    v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -p 8080:8080         google/cadvisor:latest
   ````
   
K5
=====

## Reflexion

Da ich vor kurzem erst die LB2 abgegeben habe, hatte ich Zeit Probleme mit der LB3 und da natürlich nicht alles reibungslos funktionierte, konnte ich nicht komplett alles umsetzen, was verlangt wurde. 

## Wissenstand

Ich habe zuvor noch nie mit Docker gearbeitet, daher war das eine neue Erfahrung für mich. Im Internet fand man aber genug informationen zu diesem Thema.

Einen Mysql und Apache Server hatte ich schon mal installiert, daher war es nicht wirklich schwierig. 
   
## Quellen

Saii hat mir sehr bei dieser Arbeit geholfen und auch seine Dokumentation. 
   


