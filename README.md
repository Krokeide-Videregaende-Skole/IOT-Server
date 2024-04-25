# Ming-Stack

I docker-compose.yml er det satt opp komplett konfigurasjon av en MING-Stack.

Kjør `sudo docker-compose up -d` og du får opp kontainere som kjører:
* Mosquitto
* InfluxDB
* Node-RED
* Grafana

Det er også en kontainer som kjører Portainer. Denne lar deg overvåke og administrere kontainerne.
Siden det er litt styr å navigere til web-tjenestene kontainerne kjører med ulike portnummer har vi også
en kontainer som kjører en NGINX server som fungerer som omvendt proxy til de ulike tjenestene.

I docker-compose.yml brukes det variabler som blir satt i `.env` filen; dette er brukernavn og passord.

For å generere passord-hashen til portainer er denne kommandoen brukt:
```
sudo docker run --rm httpd:2.4-alpine htpasswd -nbB admin iotAdministrator | cut -d ":" -f2
```
For å generere passord-hashen til nodered er denne kommandoen brukt:
```
sudo docker exec -it nodered node-red admin hash-pw
```
