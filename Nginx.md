
# Instalación Nginx

A continuación voy a instalar el servidor Lighttpd para crear mi segundo dominio servidor2.centro.intranet

Para ello accedo con sudo su e instala el paquete nginx

```bash
sudo su
apt update
apt install nginx
```

Configuro el firewall.

Obtengo una lista de las configuraciones de las aplicaciones con las que ufw sabe trabajar escribiendo:

```bash
ufw app list
```

Antes de iniciar lighttpd, debo apagar el servicio apache2:

```bash
systemctl stop apache2
```

Lighttpd se gestiona como un servicio del sistema, y por tanto vamos a poder iniciarlo escribiendo en la terminal:

```bash
systemctl start lighttpd
ssytemctl status lighttpd
```

![image](https://user-images.githubusercontent.com/91189372/205490968-0df7cfe2-6502-49b2-a521-10aad49636f2.png)

Para comprobar el correcto funcionamiento del servidor, accedo desde un navegador web con la siguiente URL

```
http://127.0.0.1/index.lighttpd.html
```

![image](https://user-images.githubusercontent.com/91189372/205491658-d1fe30f2-dd10-4bdc-96c3-c5465288d718.png)

# Fichero de configuración de servidor2.centro.intranet

Creo el directorio correspondiente al nuevo dominio

```bash
mkdir -p /var/www/servidor2.centro.intranet/html
```

Para el correcto funcionamiento del servidor, debo  crear un ficheeo de configuración de lighttpd, en mi caso copiare el fichero por defecto y lo modificare con el siguiente comando:

```bash
cp /etc/lighttpd/lighttpd.conf /etc/lighttpd/servidor2.centro.conf
```

Modifico el interior del fichero de configuración

```bash
cd /etc/lighttpd/
nano servidor2.centro.conf
```

Modifico el documentRoot y el puerto, lo cambio al 8080

![image](https://user-images.githubusercontent.com/91189372/205492505-9df3f9ef-ff19-431e-b52f-826426144d3b.png)

Modifico el fichero hosts para asignarle una ip a servidor2.centro.intranet, para ello:

```bash
nano /etc/hosts
```

![image](https://user-images.githubusercontent.com/91189372/205492710-2810df60-8111-4b43-9742-611c78c619ca.png)




# Añadir soporte PHP a Lighttpd

