# ProyectoWebApache

### Vamos a instalar un servidor web interno para un instituto. Se Pide:
**- Instalación del servidor web apache. Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python**

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



