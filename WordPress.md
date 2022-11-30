
Para ello instalo apache en la máquina virtual de Ubuntu con:
```bash
sudo apt-get update
sudo apt-get install apache2
```
Una vez instalado apache compruebo su estado

```bash
systemctl status apache2
```

![image](https://user-images.githubusercontent.com/91189372/204859449-50560a95-623b-4c41-bff4-8d0de019dc52.png)

Debo permitir el tráfico web de apache:

```bash
ufw app list
```

![image](https://user-images.githubusercontent.com/91189372/204860207-3b120006-ff2c-41ad-bd76-73f29e00aa7d.png)

Compruebo que funciona apache, desde el navegador accedo con localhost o con la IP

```
http:\\127.0.0.1
```

![image](https://user-images.githubusercontent.com/91189372/204860829-6f040517-e1ec-44cb-ab23-d028ce8a2495.png)

Creo el direcotrio centro.intranet en /var/www/centro.intranet

```bash
mkdir /var/www/centro.intranet
```

![image](https://user-images.githubusercontent.com/91189372/204861760-b168f723-fed4-4a8a-b711-ab9855edf235.png)

Para saber la dirección IP del servidor uso

```bash
hostname -I
```

![image](https://user-images.githubusercontent.com/91189372/204862773-0e465124-5aa8-4872-b0c9-8a3b52c510bb.png)


Ahora edito el fichero hosts para añadir el dominio centro.intranet y una dirección IP

```bash
cd /etc
nano hosts
```

![image](https://user-images.githubusercontent.com/91189372/204862961-6fa37ed0-2568-4406-8215-4a60dd2d9f6a.png)

Ahora debo crear el directorio /var/www/centro.intranet

```bash
mkdir /var/www/centro.intranet
```

Y en su interior creo un fichero index.html 

```bash
cd /var/www/centro.intranet
nano index.html
```

Creo el archivo de host virtual para centro.intranet. Para ello copio 000-default.conf a mi nuevo dominio centro.intranet

```bash
cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/centro.intranet.conf
```

![image](https://user-images.githubusercontent.com/91189372/204865854-0a17bde3-fd3e-4fda-a502-38c655c53abf.png)

Edito el fichero de configuracion centro.intranet.conf 

```bash
cd /etc/apache2/sites-available/
nano centro.intranet.conf
```

El fichero queda de la siguiente manera, modificando ServerName, DocumentRoot

![image](https://user-images.githubusercontent.com/91189372/204866984-a76810f3-886f-4248-9c5c-e9e92c552772.png)

Ahora habilito el fichero de configuración creado y reincio apache

```bash
a2ensite centro.intranet.conf
systemctl restart apache2
```

Después desactivo el fichero de configuración 000-default.conf y reincio

```bash
a2dissite 000-default.conf
systemctl restart apache2
```

![image](https://user-images.githubusercontent.com/91189372/204868030-b91873fe-6c5e-422b-98e7-b845889afd87.png)

## Instalación PHP

Para instalar PHP uso el siguiente comando:

```bash
apt install php libapache2-mod-php php-mysql
```

Después debo cambiar el orden en el que el servidor da preeferncia a los archivos, apra que priorice los archivos php a html

```bash
nano /etc/apache2/mods-enabled/dir.conf
```

![image](https://user-images.githubusercontent.com/91189372/204871335-6bc0f7ba-0ff0-4a05-976e-f85b77c98a7e.png)


## Instalar MySQL

Lo instalo con el paquete apt

```bash
apt update
```

Después instalo el paquete específico

```bash
apt install mysql-server
```

Configuro el script de seguridad de mysql

```bash
mysql_secure_installation
```

Pulso y + enter, 1 y establezco la contraseña

![image](https://user-images.githubusercontent.com/91189372/204873546-9c405fc6-d707-479d-a496-c5358eb979a7.png)

Voy pulsando y + enter hasta terminar. Con mysql entro

```bash
mysql
```

![image](https://user-images.githubusercontent.com/91189372/204874023-336831c7-3a38-4484-bebb-f3b41c574f8e.png)


## Instalar Wordpress

Accedo a la web oficial wordpres y la descargo desde allí

![image](https://user-images.githubusercontent.com/91189372/204874446-f774b726-d1cb-44e2-a693-3374313a2cee.png)

Ahora descomprimo el fichero y instalo WordPress. Me muevo hasta la ubicación donde este el fichero descargado

```bash
cd /home/hadrian/Descargas
```

Cambio los permisos del directorio centro.intranet

```bash
chown -R www-data:www-data centro.intranet
ls -l
```

![image](https://user-images.githubusercontent.com/91189372/204880676-b8108d26-c231-45d1-a791-5ccc8c903c54.png)

Ahora creo una base de datos con mysql para wordpress, un usuario y sus privilegios

```bash
mysql -u root -p
CREATE DATABASE wordpress;
CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'H7craft YT';
GRANT ALL PRIVILEGES ON wordpress*. TO 'wordpressuser'@'localhost';
```

Ahora accedo desde el navegador a centro.intranet y aparecerá la página de wordpress

![image](https://user-images.githubusercontent.com/91189372/204883326-1688364c-52df-4e0a-a459-f176e2ecd6a0.png)

Añado mis credenciales previamente creadas y empiezo el proceso de isntalación

![image](https://user-images.githubusercontent.com/91189372/204883820-d46cbfd0-5cb4-4780-9605-21ad435ed1f3.png)

Especifico el nombre del dominio, del usuario y la contraseña

![image](https://user-images.githubusercontent.com/91189372/204884143-9c588ba0-bff5-43ec-ac39-412dbcba3037.png)

Al finalizar la instalación, accedo con total normalidad

![image](https://user-images.githubusercontent.com/91189372/204884322-09cf03f1-a92a-4c32-80e1-522a6a0f32b3.png)










