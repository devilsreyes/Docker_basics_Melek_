# Hier alle im Video erwähnten Befehle:

## Docker installieren:

```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
```

Falls kein curl installiert: `apt install curl`

Wenn man nicht mit dem Nutzer Root arbeitet, sollte man den aktuellen Benutzer berechtigen:

```
sudo usermod -aG docker $USER
```

## Mit Docker arbeiten

* Laufende Container auflisten: `docker ps`
* Alle Container auflisten (auch gestoppte): `docker ps -a`
* Einen Container anhalten: `docker stop <Containername>` (den Namen findet man mit `docker ps` heraus)
* Einen gestoppten Container endgültig löschen: `docker rm <Containername>`

## Einen simplen Webserver starten

Der Container aus dem Image nginx fährt mit folgendem Befehl hoch:

```
docker run -p 80:80 nginx
```
Die eigene IP-Adresse erhält man mit `ip a`

## Arbeiten mit Docker-Compose

Legt euch am besten einen eigenen Ordner für das Docker-Projekt an, um Ordnung zu halten. Die Datei docker-compose.yml enthält die Definition der Container.

Bearbeitet wird die Datei mit:

```
nano docker-compose.yml
```

Die Inhalte findet ihr unten in diesem GitHub-Gist. Den Texteditor Nano beendet man mit: `Strg+X`, dann `Y`

Die Compose-Zusammenstellung hochfahren:

```
docker compose up -d
```

Will man die Container updaten, lädt man die neuen Images mit 

```
docker compose pull
```

## Eine oder mehrere Docker-Compose-Dateien?

Das ist definitiv Geschmachssache und hängt von der Umgebung ab. Wenn man mehr als ein Projekt (zum Beispiel einen Blog und ein Pihole) auf einem Server betreibt, sollte man für jedes einen Ordner anlegen und darin eine Docker-Compose-Datei ablegen. Die nützlichen Helfer wie Portainer und Watchtower kommen zusammen in eine weitere Datei. Dann kann man mit `docker compose down`gezielt Teile der Umgebung herunterfahren.


## Pihole

Ein Pi-hole ist ein netzwerkweiter Werbe- und Trackingblocker, der als virtuelles Schutzschild dient und unerwünschte Inhalte blockiert, noch bevor sie Ihre Geräte überhaupt erreichen

## Portainer

Portainer ist eine intuitive, webbasierte Benutzeroberfläche zur einfachen Verwaltung und Überwachung von Docker-Containern, Kubernetes-Clustern und Docker Swarm-Umgebungen.

## Watchtower

Watchtower ist ein automatisiertes Open-Source-Werkzeug für Docker, das laufende Container im Hintergrund überwacht und sie automatisch auf die neueste Version aktualisiert, sobald ein neues Image in der Registry verfügbar ist.

## Nginx

Nginx ist eine extrem schnelle und ressourcenschonende Open-Source-Software, die hauptsächlich als Webserver, Reverse Proxy und Load Balancer eingesetzt wird, um Webinhalte stabil und effizient an viele Nutzer gleichzeitig auszuliefern.

