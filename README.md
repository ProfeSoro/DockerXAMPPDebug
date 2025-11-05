# XAMPP Stack usando Docker (Compose) con XDebug

Puedes usar esta pila para sustituir la instalación de XAMPP en tu qeuipo. Contiene una configuración básica con:
- PHP 8.2
- MySQL lastest
- PHPMyAdmin 5.2.1

**Deberías usar esta pila únicamente para desarrollo/pruebas. No se recomienda para aplicaciones en producción.**

## Configuración
- Database:
  - Root user: _root_
  - Root password: _root_
  - Hostname: _db_
  - Los datos de la base de datos se almacenan en el directorio `mysql_data`
- PHPMyAdmin:
  - Autologin con las credenciales de Database
- PHP:
  - Enabled Apache modules: _rewrite_
  - Installed extensions: _mysqli_, *pdo_mysql*, _pdo_
  - Installed xdebug

## Como usar la base de datos en PHP
Para usar la base de datos en tu aplicación PHP, debes usar como hostname (_db_). Puedes consultar el ejemplo del fichero `src/index.php`.

## Ejecutar la pila XAMPP
Para utilizar esta pila debes seguir los siguientes pasos:

1. Descargar e instalar Docker para tu sistema operativo.
2. Clonar este repositorio.
   ```sh
   $ git clone https://github.com/ProfeSoro/DockerXAMPPDebug.git
   ```
3. Usar Docker para levantar los contenedores.
   ```sh
   $ docker compose up -d
   ```


## Configurar Visual Studio Code para XDebug
- Instalar la extensión 'PHP Debug'.
- Crear un fichero 'launch.json' en el directorio raíz del repositorio (ya viene creado).
- Poner lo siguiente en el fichero 'launch.json'
```
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Listen for Xdebug",
      "type": "php",
      "request": "launch",
      "port": 9003,
      "pathMappings": {
        "/var/www/html": "${workspaceFolder}/src"
      },
      "log": true
    }
  ]
}
```
