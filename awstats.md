
# Instalar AwStats

Para ello debo instalarlo mediante el siguiente comando, todo con sudo su:

```bash
sudo su
apt install awstats libgeo-ip-perl libgeo-ipfree-perl
```

# Configuración VirtualHost

Edito el archivo virtual host de apache

```bash
nano /etc/apache2/sites-avaialble/departamentos.centro.conf
```

Y en su interior añado las siguientes directivas:

![image](https://user-images.githubusercontent.com/91189372/205601656-8cf24e21-2f74-4c33-a181-28101343768d.png)

```bash
a2enmod cgi
systemctl restart apache2
```

A continuación, desde el navegador accedo a awstats:

```
http://departamentos.centro.intranet/cgi-bin/awstats.pl
```

![image](https://user-images.githubusercontent.com/91189372/205603346-a5c3cfdf-40d0-4079-ba16-96270a2657dd.png)


# Configuración AwStats

Copio el fichero de configuración a un nuevo fichero

```bash
cp /etc/awstats/awstats.conf /etc/awstats/awstats.departamentos.centro.conf
```

![image](https://user-images.githubusercontent.com/91189372/205603920-de23cb3f-092f-45cf-b103-c4d6f9cc9059.png)

Edito el nuevo fichero

```bash
nano /etc/awstats/awstats.departamentos.centro.conf
```

Cambio el valor de la siguiente línea a '1'

```bash
LogFormat=1
```

![image](https://user-images.githubusercontent.com/91189372/205604862-17c07f7f-b3cd-4254-9885-7faa9b4d1dbf.png)


Añado el dominio

```bash
SiteDomain="departamentos.centro.intranet"
```

![image](https://user-images.githubusercontent.com/91189372/205605097-ace52552-6330-436e-b1dd-0aa28e2deca0.png)

También, añado el nombre de dominio al parámetro HostAliases

```bash
HostAliases="departamentos.centro.intranet localhost 127.0.0.1"
```

![image](https://user-images.githubusercontent.com/91189372/205605465-88cb85c7-c366-4b94-9bc1-8c80bbb7a70a.png)


Guardo y cierro, permito www-data leer los logs de Apache usando el siguiente comando:

```bash
setfacl -R -m "u:www-data:rx" /var/log/apache2/
```




