
# Proteger instalación Python

Debo proteger el acceso a la aplicación de Python mediante autenticación

Editando, el archivo Virtual Hosts:

```bash
cd /etc/apache2/sites-available/
nano departamentos.centro.conf
```

En su interior añado las siguientes directivvas:

```bash
AuthType Digest
AuthName "Top Secret"
AuthDigestProvider wsgi
WSGIAuthUserScript /usr/local/wsgi/scripts/auth.wsgi
Require valid-user
```
