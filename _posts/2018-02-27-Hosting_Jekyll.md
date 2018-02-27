---
layout: single
title:  "Hosting einer Jekyll Website auf einem Linux Server"
tags:
  - jekyll
  - Hosting
  - Internet
  - Linux  
---

### Folgende Voraussetzungen solltet ihr für die folgende Anleitung/Tutorial mitbringen:

* Linux-Server z.B. mit Ubuntu 16.04 bei einem Web-/Cloudhoster
* Jekyll Website (diese sollte lokal auf eurem PC laufen! Befehl, den ihr im Ordner der jekyll Website ausführen müsst: `bundle exec jekyll serve`)
* (Domain auf die ihr gerne die Website verknüpfen wollt)

weiterhin hilfreich sind Erfahrungen...:

* ...mit dem Terminal in Linux
* ...mit git

### Vorbereitung des Servers

1. Einloggen mit dem Terminal auf eurem Linux-Server `ssh root@SERVER-IP`
1. Update & Upgrade des Servers `apt-get update && upgrade`
1. Installation eines HTTP Servers wie z.B. nginx `apt-get install nginx`
1. Installation von git `apt-get install git-all`
1. Installation von Nano (Text Editor) `apt-get install nano`
1. Installation von Ruby über [rvm](http://rvm.io/), die Schritte hierfür:
    1. `gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB`
    1. `apt-get install curl`
    1. `\curl -sSL https://get.rvm.io | bash -s stable`
    1. `source /etc/profile.d/rvm.sh`
    1. `rvm install ruby`
1. Insallation von bunble `gem install bundle`
1. Installation von jekyll `gem install jekyll`

Nun haben wir alle wesentlichen Programme und Pakete installiert! :smile:

### Ereichbarkeit des Servers (Zwischen-Test)

Nachdem wir nun einen HTTP Server installiert haben, können wir ausprobieren, ob dieser bereits erreichbar ist.

1. Dazu starten wir nginx mit `service nginx start`
2. In eurem Browser solltet ihr nun, wenn ihr die IP Adresse eures Servers eingebt, folgende Website sehen:
![nginx]({{ "/assets/images/nginx_screenshot.png" | absolute_url }}){:class="img-responsive"}

### Konfiguration von nginx

1. Damit nginx auf den korrekten Ordner für unsere jekyll Website zugreift, erstellen wir noch den passenden Ordner
2. Wir wechseln in das passende Verzeichnis `cd /var/www`
3. Erstellen eines neuen Ordners für die Website z.B. `mkdir eure_website`
1. Anpassung von nginx, damit es auf die Website zugreift `nano /etc/nginx/sites-enabled/default`, nun passt die Einstellung `root /var/www/html;` in `root /var/www/eure_website;`


### Vorbereitung des git Repositorys auf unserem Server

1. Erstellen eines neues Ordners `mkdir repo_website.git`
1. Wechseln in den Ordner `cd repo_website.git`
1. Initialisierung des Repositorys `git --bare init`
1. Erstellen einer neuen Datei `post-receive`, diese Datei sorgt bei jedem neuen Commit unserer Website von unserem PC dafür, dass die jekyll Website neu aufgebaut wird. Dazu geben wir ein `nano hooks/post-receive`. Es öffnet sich das nano Fenster in diesen könnt ihr folgendes bash-Skript kopieren:
   ``` bash
    #!/bin/bash -l
    set -x
    GIT_REPO=$HOME/repo_website.git
    TMP_GIT_CLONE=$HOME/tmp/repo
    GEMFILE=$TMP_GIT_CLONE/Gemfile
    PUBLIC_WWW=/var/www/eure_website

    git clone $GIT_REPO $TMP_GIT_CLONE
    BUNDLE_GEMFILE=$GEMFILE bundle exec jekyll build -s $TMP_GIT_CLONE -d $PUBLIC_WWW
    rm -Rf $TMP_GIT_CLONE
    exit
    ```
1. Die Datei machen wir jetzt noch ausfübar mit `chmod +x post-receive`
1. Jetzt gehen wir wieder in den Ordner, in dem sich unsere jekyll Website befindet. Hier habe ich bereits git Repository erstellt. Damit wir dieses jetzt auf unseren Server pushen können geben wir folgenden Befehl ein `git remote add deploy root@SERVER-IP:~/repo_website.git`
1. Mit `git push deploy master` wird jetzt eure jekyll Website auf den Server gepusht und das Skript `post-receive` ausgeführt, hierbei kann es unterumständen noch zu kleineren Problemen kommen, dies hängt beispielsweise davon ab, ob ihr für euer jekyll Theme alle pakete installiert habt. Auf eurem Server könnt ihr im Verzeichnis `repo_website.git/hooks/` mit `bash post-receive` solange testen bis alle Probleme behoben sind. Wenn es durch läuft, müsst ihr noch für einen neuen Post einen push auf eurem Rechner durchführen und die Website passt sich automatisch an.
1. Abschließend startet ihr noch nginx neu `nginx -s reload`, dann greift der HTTP Server auf das neue Verzeichnis zu.

Ich hoffe, dass ihr jetzt nun erfolgreich euren jekyll Blog oder Website posten konntet :+1:
Wenn ihr eine Domain bereits erworben habt und sie auf euren Linux Server umleiten wollte, müsst ihr nur einen A-Record erstellen und in diesem euere SERVER-IP eingeben.
