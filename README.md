# GautitHome

## Installation

Cible : Raspberry Pi 4

## Installer Docker
```
curl -sSL https://get.docker.com | sh
```

## Démarrer le conteneur HA
```
sudo docker run -d --name homeassistant --privileged --restart=unless-stopped -e TZ=Europe/Paris -v ha_config --network host ghcr.io/home-assistant/home-assistant:stable
```

## Mettre à jour le conteneur HA
```
sudo docker pull ghcr.io/home-assistant/home-assistant:stable
sudo docker stop homeassistant
sudo docker rm homeassistant
```
Puis réeffectuer l'étape (Démarrer le conteneur HomeAssitant)[#Demarrer-le-conteneur-HomeAssitant].

## Accéder à l'interface web HA

HomeAssistant est disponible à l'adresse suivante : http://localhost:8123/
