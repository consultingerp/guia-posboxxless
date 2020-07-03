# guia-posboxxless

## Guía de instalación de POSBOXLESS en un entorno virual usando Virtualenv

### Crear entorno Virtual con el usuario "pi", crear contraseña "raspberry" y activar el entorno virtual

	sudo useradd -m -d /home/pi -U -r -s /bin/bash pi
	sudo usermod -aG sudo,www-data pi
	sudo su - pi
	sudo passwd pi # pass=raspberry
	python3 -m venv ~/server/11
	cd ~/server/11
	source bin/activate

### Instalar modulos necesarios

	apt-get -y install cups adduser python3 python3-dateutil python3-decorator python3-docutils python3-feedparser python3-pil python3-jinja2 python3-ldap python3-lxml python3-mako python3-mock python3-openid python3-passlib python3-psutil python3-psycopg2 python3-babel python3-pydot python3-pyparsing python3-pypdf2 python3-reportlab python3-requests python3-tz python3-vatnumber python3-vobject python3-werkzeug python3-yaml python3-gevent python3-serial  python3-dev localepurge mg screen iw hostapd isc-dhcp-server git rsync console-data

### Descargar Odoo e instalar modulos y requeriments.txt

	cd ~/server/11
	source bin/activate #Obviar esta linea si ya estas dentro del env
	git clone --depth 1 --branch 11.0 --single-branch https://www.github.com/odoo/odoo
	pip3 install --upgrade pip && pip3 install --upgrade setuptools
	pip3 install wheel 
	pip3 install -r odoo/requirements.txt
	pip3 install phonenumbers

### (Opcional) Eliminar addons innecesarios y los que se necesitan para el POSBOXXLESS
	mv ~/server/11/odoo/addons ~/server/11/odoo/addons_bkp
	mkdir ~/server/11/odoo/addons
	cd ~/server/11/odoo/addons_bkp/ #mas adelante esta carpeta se puede borrar
	mv hw_blackbox_be hw_escpos hw_posbox_homepage hw_posbox_homepage hw_posbox_upgrade hw_scanner hw_screen web website point_of_sale ~/server/11/odoo/addons

### Descargar hw_printer_network
	cd ~/server/11/odoo/addons/
	git clone --depth 1 --branch 11.0 --single-branch https://github.com/itpp-labs/pos-addons.git
	cd ~/server/11/odoo/addons/pos-addons
	mv hw_printer_network ~/server/11/odoo/addons
	mv hw_twitter_printing ~/server/11/odoo/addons # Opcional
	rm -rf ~/server/11/odoo/addons/pos-addons


