# Chargement d'une carte ESP32

## Auteur

Kevin Doolaeghe

## Chargement d'une carte ESP32

### Installation de l'utilitaire `esptool`

```
sudo apt update && sudo apt install wget python3 python3-pip
pip3 install esptool
```

### Connexion de la carte ESP32

Vérifier que le périphérique est correctement reconnu par le système :

```
ls -l /dev/ttyUSB*
```

Si aucun autre périphérique USB n'est connecté alors la carte sera connectée au port USB0.

### Attribution des droits d'utilisation des ports USB à l'utilisateur

```
sudo usermod -aG dialout,tty ${USER}
```

### 4. Réinitialisation de la mémoire FLASH

```
esptool.py --port /dev/ttyUSB0 erase_flash
```

### 5. Ecriture du firmware dans la mémoire FLASH

```
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x1000 [firmware].bin
```

## Sources

- [Dépôt Git de l'utilitaire `esptool`](https://github.com/espressif/esptool)
- [Chargement d'une carte ESP32-CAM sous Tasmota](https://easydomoticz.com/forum/viewtopic.php?f=24&p=94316)
