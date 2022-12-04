
# Instalación Lighttpd

A continuación voy a instalar el servidor Lighttpd para crear mi segundo dominio servidor2.centro.intranet

Para ello accedo con sudo su e instala el paquete Lighttpd

```bash
sudo su
apt install lighttpd
```

Antes de iniciar lighttpd, debo apagar el servicio apache2:

```bash
systemctl stop apache2
```

Lighttpd se gestiona como un servicio del sistema, y por tanto vamos a poder iniciarlo escribiendo en la terminal:

```bash
systemctl start lighttpd
```

![image](https://user-images.githubusercontent.com/91189372/205490968-0df7cfe2-6502-49b2-a521-10aad49636f2.png)

Para comprobar el correcto funcionamiento del servidor, accedo desde un navegador web con la siguiente URL

```
http://127.0.0.1/index.lighttpd.html
```

![image](https://user-images.githubusercontent.com/91189372/205491658-d1fe30f2-dd10-4bdc-96c3-c5465288d718.png)
