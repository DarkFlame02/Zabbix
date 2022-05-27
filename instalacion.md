# Instalación de Zabbix en Ubuntu 18.04.

1. En una maquina con Ubuntu 18.04 instalado descargamos zabbix con el siguiente comando y lo instalamos:

```bash
wget https://repo.zabbix.com/zabbix/4.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_4.2-1+bionic_all.deb 
```

![imagen1](imagenes/instalacion1.png)

```bash
sudo dpkg -i zabbix-release_4.2-1+bionic_all.deb 
```

![imagen2](imagenes/instalacion2.png)

2. Actualizamos los repositorios e instalamos el resto de paquetes necesarios para el servidor zabbix(esto último tardara un rato):

```bash
sudo apt update
```

![imagen3](imagenes/instalacion3.png)

```bash
sudo apt install -y zabbix-server-mysql zabbix-frontend-php zabbix-agent
```

![imagen4](imagenes/instalacion4.png)

3. Conectamos al servidor de bases de datos y creamos la base de datos:

```bash
sudo mysql -uroot -p
```

![imagen5](imagenes/instalacion5.png)

4. Creamos el usuario con su contraseña y le damos todos los privilegios sobre la base de datos:

```sql
	create database zabbix character set utf8 collate utf8_bin;
```

```sql
	grant all privileges on zabbix.* to zabbix@localhost identified by 'password';
```

![imagen6](imagenes/instalacion6.png)