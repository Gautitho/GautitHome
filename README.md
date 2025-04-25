# RaspHome

## Installation

Matériel : 
- PC avec un port carte SD
- Raspberry Pi 5
- Carte SD 64 Go minimum
- Alimentation USB C

### Raspberry Pi

Télécharger et installer Raspberry Pi Imager : https://www.raspberrypi.com/software/  

Dans Raspberry Pi Imager :
- Sélectionner le modèle de Raspberry Pi
- Sélectionner l'OS recommandé
- Brancher la carte SD à l'ordinateur et la séléctionner
- Ne pas sélectionner les paramètres par défaut
- Mettre un nom d'utilisateur et un mot de passe
- Paramétrer le Wifi
- Activer le SSH
- Terminer et écrire la carte SD

Il est normalement possible de se connecter en SSH sur la Raspberry Pi avec le l'utilisateur et le mot de passe défini lors de la configuration :
```
ssh USERNAME@RASP_PI_IP
```

### Docker
```
sudo apt install docker
```
Si ça ne fonctione pas : 
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
