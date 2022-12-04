
# Instalación Nginx

A continuación voy a instalar el servidor Nginx para crear mi segundo dominio servidor2.centro.intranet

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

Una vez instalado, doy privilegios a nginx en el firewall:

```bash
ufw allow 'Nginx HTTP'
```

Antes de iniciar nginx, debo apagar el servicio apache2:

```bash
systemctl stop apache2
systemctl start nginx
```


A continuación, creo la carpeta para el servidor2.centro.intranet

```bash
mkdir -p /var/www/servidor2.centro.intranet/html
```

Posteriormente, asigno la titularidad del directorio con la variable de entorno $USER:

```bash
chown -R $USER:$USER /var/www/servidor2.centro.intranet/html
chmod -R 755 /var/www/servidor2.centro.intranet
```

Creo una página inex para la web 

```
cd /var/www/servidor2.centro.intranet/html
nano index.html
```

Creo el fichero de directiva

```bash
cd /etc/nginx/sites-available/
nano servidor2.centro.intranet
```

En su interior escribo lo siguiente:

```bash
server {
        listen 8080;
        listen [::]:8080;

        root /var/www/servidor2.centro.intranet/html;
        index index.html index.htm index.nginx-debian.html;

        server_name servidor2.centro.intranet www.servidor2.centro.intranet;

        location / {
                try_files $uri $uri/ =404;
        }
}
```

Después, voya habilitar el archivo creando un enlace desde el mismo al directorio sites-enabled (habilitado para sitios), el cual Nginx usa para leer durante el inicio


```bash
ln -s /etc/nginx/sites-available/servidor2.centro.intranet /etc/nginx/sites-enabled/
```

Ahora, debo ajustar un solo valor en el archivo /etc/nginx/nginx.conf para evitar un posible problema de memoria de hash bucket, el que puede surgir al agregar nombres de servidores adicionales. Abro el archivo:

```bash
nano /etc/nginxnginx.conf
```

Busco la directiva server_names_hash_bucket_size y quite el símbolo # para descomentar la línea:

```bash
...
http {
    ...
    server_names_hash_bucket_size 64;
    ...
}
...
```
Posteriormente, hago una prueba para asegurarse de que no haya errores de sintaxis en ninguno de misarchivos de Nginx:

```bash
nginx -t
```

El cual me devuelve que no hay errores

![image](https://user-images.githubusercontent.com/91189372/205498588-f3b3b1a8-0507-4d90-8286-364de16d8062.png)

Reinicio Nginx para habilitar sus cambios:

```bash
systemctl restart nginx
```

Ahora desde el navegador

```
http://servidor2.centro.intranet:8080
```

![image](https://user-images.githubusercontent.com/91189372/205499016-21071526-341f-46fb-a099-c994353c1075.png)




