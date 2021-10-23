# Chargement d'une carte ESP32

## Auteur

Kevin Doolaeghe

## Chargement d'une carte ESP32

### Installation de l'utilitaire `esptool` :

```
sudo apt update && sudo apt install wget python3 python3-pip
pip3 install esptool
```

### Connexion de la carte ESP32 :

Vérifier que le périphérique est correctement reconnu par le système :

```
ls -l /dev/ttyUSB*
```

Si aucun autre périphérique USB n'est connecté alors la carte sera connectée au port USB0.

### Attribution des droits d'utilisation des ports USB à l'utilisateur :

```
sudo usermod -aG dialout,tty ${USER}
```

### Réinitialisation de la mémoire FLASH :

```
esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash
```

### Chargement du firmware :

```
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x1000 [firmware].bin
```

## Installation de Tasmota pour ESP32-CAM sous Windows

1. [Télécharger](https://github.com/Jason2866/ESP_Flasher/releases) l'exécutable `ESP-Flasher`

2. [Télécharger](https://tasmota.github.io/docs/ESP32/) le firmware Tasmota

3. [Télécharger](http://www.wch-ic.com/downloads/CH341SER_ZIP.html) le driver pour le composant CH340 du module USB

4. Connecter le module ESP32-CAM au PC par l'intermédiaire du module USB

5. Installer le driver du module USB

6. Démarrer l'exécutable `ESP-Flasher` et sélectionner le port série adéquat ainsi que le firmware téléchargé précédemment

7. Flasher l'ESP32

## Sources

- [Dépôt Git de l'utilitaire `esptool`](https://github.com/espressif/esptool)
- [Chargement d'une carte ESP32-CAM sous Tasmota](https://easydomoticz.com/forum/viewtopic.php?f=24&p=94316)
- [Installation du driver pour le composant CH340 du module USB](https://learn.sparkfun.com/tutorials/how-to-install-ch340-drivers/all)
- [Utilisation du module EPS32-CAM avec Arduino® - Le Blog Gotronic](https://www.gotronic.fr/blog/guides/utilisation-du-module-eps32-cam-avec-arduino/)
- [Installation du firware Tasmota sur ESP32](https://tasmota.github.io/docs/ESP32/)
- [Programmation d'une carte ESP32-CAM via une carte Arduino Uno](https://www.youtube.com/watch?v=q-KIpFIbRMk)
- [Erreur `rst:0x1 (POWERON_RESET),boot:0x3 (DOWNLOAD_BOOT(UART0/UART1/SDIO_REI_REO_V2))`](https://github.com/espressif/arduino-esp32/issues/3195)
