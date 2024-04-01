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

# Netbootxyz
  
Alle stappen kun je [hier vinden](https://landaalict.nl/posts/pxe/)