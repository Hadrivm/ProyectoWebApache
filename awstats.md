
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
