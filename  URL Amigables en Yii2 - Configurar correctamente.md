#URL Amigables en Yii2 - Configurar correctamente

#1. Dirigirse a aplicacion/config/web.php y agregar o descomentar el siguiente codigo para activar las Url amigables.
 ```bash
  'components' => [
        'urlManager' => [
            'enablePrettyUrl' => true,
            'showScriptName' => false,
            'rules' => [
                '' => 'site/index',
                '<action>'=>'site/<action>',
            ],
        ],
  ],
  ```
#2. Crear un archivo .htaccess en la aplicacion/web/.htaccess
```bash
Options +FollowSymLinks
IndexIgnore */*

RewriteEngine on

# If a directory or a file exists, use the request directly
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
# Otherwise forward the request to index.php
RewriteRule . index.php
```

#3. Configurar el servidor apache2, ingresar a la Terminal unix
  EJECUTAR LOS SIGUIENTES COMANDOS PARA ACTIVAR LOS PERMISOS DE ESCRITURA
--------------------------------------------------------------------------
```bash
$ cat /etc/apache2/mods-available/rewrite.load
$ sudo a2enmod rewrite
$ ls -al /etc/apache2/mods-enabled/rewrite.load
```
#4. Ahora sustituye a todos los "AllowOverride None" por "AllowOverride All" en el archivo de configuración apache2:
```bash
$ sudo gedit /etc/apache2/apache2.conf
```
#5.Finalmente reinicie su servidor apache:
```bash
$ sudo service apache2 restart
```

Listo ahora la aplicacion Yii2 esta configurado correctamente con Url amigables :) 
