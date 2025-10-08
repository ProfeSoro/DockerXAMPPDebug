# XAMPP Stack using Docker (Compose)

You can use this stack to replace your XAMPP instances. It contains a very basic setup with:
- PHP 8.2
- MariaDB 11.3.2
- PHPMyAdmin 5.2.1

**You should only use this for testing/development! It is NOT suitable for production.**

## Configuration
- Database:
  - Root user: _root_
  - Root password: _root_
  - Secondary user: _user_
  - Secondary user password: _user_
  - Hostname: _db_
  - Data is stored in the `mariadb_data` directory
- PHPMyAdmin:
  - Autologin using the credentials above
- PHP:
  - Enabled Apache modules: _rewrite_
  - Installed extensions: _mysqli_, *pdo_mysql*, _pdo_
  - Installed xdebug

## Using the database in PHP
To use the database in your PHP application, you can refer to the database using it's hostname (_db_). Check the example `src/index.php` file.

## Running
To run the stack, do the following:
1. Download and install Docker for your OS.
2. Clone this repo.
   ```sh
   $ git clone ... repository_name
   ```
3. Use Docker Compose to run.
   ```sh
   $ docker compose up -d
   ```


## Configuring VSC for XDebug
- Install PHP Debug extension
- Create a launch.json file into the root directory
- Paste this into launch.json
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
