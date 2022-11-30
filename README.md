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




![image](https://user-images.githubusercontent.com/91189372/203992940-8a35f71a-5c66-4f58-a4b2-30b61ea96848.png)

![image](https://user-images.githubusercontent.com/91189372/204246941-635d4a4d-593b-41d1-82dd-d1fa66d6355c.png)

![image](https://user-images.githubusercontent.com/91189372/204489954-2b251650-6d28-4c84-8558-cf1b773398a8.png)

![image](https://user-images.githubusercontent.com/91189372/204490517-40bda8c4-c83f-4683-b031-237e626406e4.png)

![image](https://user-images.githubusercontent.com/91189372/204490718-7c259f3b-9ab0-4645-b888-220397859e6a.png)

![image](https://user-images.githubusercontent.com/91189372/204491258-aa6d7c63-d71b-4b74-b30b-5cbffabfbf3c.png)

![image](https://user-images.githubusercontent.com/91189372/204493404-371101c1-e8b9-41fa-a167-1fda5d79f3c2.png)

ç![image](https://user-images.githubusercontent.com/91189372/204494253-93ddfd1b-30ea-48bd-8c11-5cd2bb960c38.png)

![image](https://user-images.githubusercontent.com/91189372/204619865-5f2d72aa-0e93-470f-8f48-d4fa4e072ee4.png)

![image](https://user-images.githubusercontent.com/91189372/204621253-c243da06-c971-45f4-bb28-f58daece7149.png)

![image](https://user-images.githubusercontent.com/91189372/204622326-33928b90-4865-4823-a3e9-cdc11fed11d4.png)



