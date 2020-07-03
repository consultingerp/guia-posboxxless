# guia-posboxxless

## Guía de instalación de POSBOXLESS en un entorno virual usando Virtualenv

### Crear entorno Virtual con el usuario "pi", crear contraseña "raspberry" y activar el entorno virtual

sudo useradd -m -d /home/pi -U -r -s /bin/bash pi
sudo usermod -aG sudo,www-data pi
sudo su - pi
sudo passwd pi
pass=raspberry
python3 -m venv ~/server/11
cd ~/server/11
source bin/activate
