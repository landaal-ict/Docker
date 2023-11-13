# Docker
Docker examples

Dit zijn mijn persoonlijke docker files.  
Je kunt ze gebruiken.  
Gevoelige data is weg gelaten dus sommige compose files moet je wel nog even correcte gegevens in zetten.  
o.a usernames en wachtwoorden.  
Ik werk met al mijn containers met een .env file.  

# Unifi 

Zorg er voor dat unifi-controller en unifi-db in het zelfde docker netwerk zitten.  
Bij unifi-db moet je nog een file aanmaken genaamd: init-mongo.js in die file moet je het volgende zetten:  
```
db.getSiblingDB("unifi").createUser({user: "unifi", pwd: "jewachtwoord", roles: [{role: "dbOwner", db: "unifi"}, {role: "dbOwner", db: "MONGO_DBNAME_stat"}]});
```
Dit word een regel.  
Pas jewachtwooord aan voor een door jou gekozen wachtwoord.  

# Home assistant  

## HACS installeren  

docker exec -it homeassistant bash  
wget -q -O - https://install.hacs.xyz | bash -  


# Zigbee2mqtt  

## config voor zigbee2mqtt  
```
homeassistant: true
permit_join: true
mqtt:
  base_topic: zigbee2mqtt
  server: mqtt://192.168.1.2
  user: hass
  password: 'geheim'
frontend: true
advanced:
  pan_id: 6770
serial:
  port: /dev/ttyUSB0
```
pas de gegevens hier boven aan 

# Mosquitto  
## config voor mosquitto.  

```
persistence true
persistence_location /mosquitto/data/

log_dest stdout
log_dest file /mosquitto/log/mosquitto.log
log_type warning
log_timestamp true
connection_messages true

listener 1883

## Authentication ##
allow_anonymous false
password_file /mosquitto/config/password.txt
```
Zet deze config in /mosquitto/config met de naam mosquitto.conf  

Maak je password file aan:  
docker exec -it mosquitto /bin/sh  
mosquitto_passwd -c /mosquitto/config/password.txt jegebruikersnaam  

# Vaultwarden  
## Wachtwoord hashen voor vaultwarden.  
Je moet je admin token hashen voor vaultarden zodat het geen platte tekst is.  
Ik heb deze site er voor gebruikt [Argon2 online](https://argon2.online/)  

# Netbootxyz
  
Alle stappen kun je [hier vinden](https://landaalict.nl/posts/pxe/)