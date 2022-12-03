
# Configuración Apache y Virtual Host

Apache ya está instalado y explicada su instalación el apartado anterior, ya que fue necesaria para crear el primer dominio con Wordpress

A continuación, debo crear el directorio departamentos.centro.intranet. Todas estas modificaciones con el comando sudo su para entrar como superusuario

```bash
sudo su
cd /var/www/
mkdir departamentos.centro.intranet
```

![image](https://user-images.githubusercontent.com/91189372/205455752-7f6aede8-ce10-453b-b7fe-a7e473a43980.png)

A este nuevo dominio le asigno una ip dentro del fichero hosts

```bash
cd /etc/
nano hosts
```

Y en su interior asigno la misma ip que el primer dominio a departamentos.centro.intranet

![image](https://user-images.githubusercontent.com/91189372/205455814-59505634-1708-4aaa-b5ce-9ec485d887e1.png)

A su vez, debo crear el fichero de configuración de este nuevo dominio y configurarlo

```bash
cd /etc/apache2/sites-available/
nano departamentos.centro.conf
```
Editando el interior de la siguiente manera:

![image](https://user-images.githubusercontent.com/91189372/205456228-ccb924e3-7dc7-4140-925d-62e361e0ffec.png)

# Instalación y configuración Python

El primer paso es instalar python3

```bash
sudo apt update
sudo apt install python3
```

Con python3 compruebo que está instalado

![image](https://user-images.githubusercontent.com/91189372/205458523-d6c3ac00-ef58-490b-987f-74586d2e80bd.png)

En principio, necesitamos hacer que Apache, incorpore un soporte para servir archivos Python. Para ello, necesitaremos habilitarle un módulo, que brinde este soporte.

Para habilitar mod_wsgi en Apache, basta con instalar el paquete libapache2-mod-wsgi:

```bash
sudo apt-get install libapache2-mod-wsgi-py3
```

![image](https://user-images.githubusercontent.com/91189372/205458994-da1de7bf-2dc3-401c-a431-488f8a9c265e.png)

Ahora dentro del directorio departamentos.centro.intranet voy a dividir su arquitectura en dos partes:

1. Destinada al almacenaje de nuestra aplicación Python pura (será un directorio privado, no servido).

2. Destinada a servir la aplicación (directorio público servido) en el cuál solo almacenaremos archivos estáticos.

```bash
sudo mkdir /var/www/departementos.centro.intranet/mypythonapp
sudo mkdir /var/www/departementos.centro.intranet/public_html
```

![image](https://user-images.githubusercontent.com/91189372/205459135-eea8c166-26bd-421b-92c5-f471ba2935a0.png)

Aprovecharemos este paso, para crear una carpeta, destinada a almacenar los logs de errores y accesos a nuestra Web App

```bash
sudo mkdir /var/www/departementos.centro.intranet/logs
```

Ahora debo crear un controlador para la aplicación. Dicho módulo, solo se encargará de definir una función, que actúe con cada petición del usuario. Esta función, deberá ser una función WSGI aplicación válida. 

```bash
echo '# -*- coding: utf-8 -*-' > mypythonapp/controller.py
```
