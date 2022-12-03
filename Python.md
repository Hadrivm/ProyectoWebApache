
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

![image](https://user-images.githubusercontent.com/91189372/205455814-59505634-1708-4aaa-b5ce-9ec485d887e1.png)
