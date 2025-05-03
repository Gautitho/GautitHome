# RaspHome

## Installation

**Matériel :**
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

### HomeAssistant

Il existe plusieurs façons d'installer HomeAssistant :
- HomeAssistant OS : Ne permet pas d'utiliser la Raspberry Pi pour d'autres applications en parallèle (non traité dans ce tutoriel)
- Docker simple : Ne permet pas d'utiliser les modules complémentaires (Add-on) notamment les applications développées par la communauté
- Docker supervised : Installation compliquée mais support de toutes les fonctionnalités

#### Docker simple

**Démarrer le conteneur HA**
```
sudo docker run -d --name homeassistant --privileged --restart=unless-stopped -e TZ=Europe/Paris -v ha_config --network host ghcr.io/home-assistant/home-assistant:stable
```

**Mise à jour du conteneur HA**
```
sudo docker pull ghcr.io/home-assistant/home-assistant:stable
sudo docker stop homeassistant
sudo docker rm homeassistant
```
Puis réeffectuer l'étape précédente.

### Docker supervised
```
sudo wget https://github.com/HuckleberryLovesYou/Homeassistant-Supervised-on-Raspberry-Pi-5/raw/main/installHomeassistant.sh -O installHomeassistant.sh && sudo chmod +x installHomeassistant.sh && sudo ./installHomeassistant.sh
```
La Raspberry Pi va redémarrer 2 fois.  
Avant de redémarrer lle script d'installation va préparer des instructions pour le prochain redémarrage dans .bashrc.  
Après chaque redémarrage, il faudra se connecter en tant que **su** pour lancer la suite du script.  
Une fois terminé, le script lance directement un docker avec HA.  
  
Cette installation vient d'un script communautaire :  
https://github.com/HuckleberryLovesYou/Homeassistant-Supervised-on-Raspberry-Pi-5  
  
*Snapshot personnel : https://github.com/Gautitho/Homeassistant-Supervised-on-Raspberry-Pi-5*  

## Accéder à l'interface web HA

HomeAssistant est disponible à l'adresse suivante : http://localhost:8123/
