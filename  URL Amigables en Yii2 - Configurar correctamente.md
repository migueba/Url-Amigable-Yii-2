URL Amigables en Yii2 - Configurar correctamente

1. Crear un archivo .htaccess en la aplicacion/web/.htaccess
------------------------------------------------------------------
RewriteEngine on

RewriteBase /~salem/alpha2/web
'
# If a directory or a file exists, use the request directly
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
# Otherwise forward the request to index.php
RewriteRule . index.php'


----------------------------------------------------------------
----------------------------------------------------------------

2. Configurar el servidor apache2, ingresar a la Terminal unix
  EJECUTAR LOS SIGUIENTES COMANDOS PARA ACTIVAR LOS PERMISOS DE ESCRITURA
--------------------------------------------------------------------------

$ cat /etc/apache2/mods-available/rewrite.load
$ sudo a2enmod rewrite
$ ls -al /etc/apache2/mods-enabled/rewrite.load

--------------------------------------------------------------------
-----------------------------------------------------------------------
 3. Ahora dirigirse a aplicacion/config/web.php y agregar o descomentar el siguiente codigo 
    para activar las Url amigables. :)
 
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