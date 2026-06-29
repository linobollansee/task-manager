Find which php.ini file your command line is using by running:
```
php --ini
```

PHP ships with almost all extensions turned off by default to save server memory and system resources.

Removes the comment semicolon (;) to activate the fileinfo extension in PHP.

```
PS C:\> (Get-Content "$env:USERPROFILE\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.5_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini") -replace ';extension=fileinfo', 'extension=fileinfo' | Set-Content "$env:USERPROFILE\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.5_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini"
```

Searches your php.ini file and prints every line that contains the text extension=fileinfo

```
PS C:\> Select-String -Path "$env:USERPROFILE\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.5_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini" -Pattern "extension=fileinfo"
```

Lists all the compiled-in and dynamically loaded PHP modules (extensions) that are currently active in your environment

```
PS C:\> php -m
```

Composer uses a vendor/package format to find code on Packagist (the PHP package registry)

Downloads the official Laravel project template into a new folder named task-manager

```
PS C:\> composer create-project laravel/laravel task-manager
```

Changes your terminal's working directory to task-manager

```
PS C:\> cd task-manager
```

Starts a lightweight, built-in local web development server specifically for your task-manager Laravel project

```
PS C:\task-manager> php artisan serve
```

Local address and port where your Laravel website or API is actively running for development

<http://127.0.0.1:8000/>


Opens the PostgreSQL terminal as the admin user (postgres).

```
PS C:\> psql -U postgres
```

Creates a blank database container named task_manager to store your tables and data

```
postgres=# CREATE DATABASE task_manager;
```

The default database configuration block inside a freshly installed Laravel .env file.

```
DB_CONNECTION=sqlite
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=laravel
# DB_USERNAME=root
# DB_PASSWORD=
```

Uses PowerShell to find the default SQLite/MySQL placeholder block inside your .env file and completely replaces it with your live PostgreSQL connection settings

```
PS C:\task-manager> $envFile = ".\.env"; $content = Get-Content $envFile -Raw; $target = 'DB_CONNECTION=sqlite\s*#\s*DB_HOST=127\.0\.0\.1\s*#\s*DB_PORT=3306\s*#\s*DB_DATABASE=laravel\s*#\s*DB_USERNAME=root\s*#\s*DB_PASSWORD='; $replacement = "DB_CONNECTION=pgsql`nDB_HOST=127.0.0.1`nDB_PORT=5432`nDB_DATABASE=task_manager`nDB_USERNAME=postgres`nDB_PASSWORD=password"; $content -replace $target, $replacement | Set-Content $envFile
```

After running the command, the .env file is updated to configure Laravel to use PostgreSQL instead of the default SQLite database. The configuration specifies that the PostgreSQL server is running locally (127.0.0.1), communicates through the default PostgreSQL port (5432), connects to the task_manager database, and authenticates using the postgres user with the password `password`

```
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=task_manager
DB_USERNAME=postgres
DB_PASSWORD=password
```


Clears the cached configuration
```
php artisan config:clear
```

Removes the comment semicolon (;) to activate the PostgreSQL extensions in PHP.

```
PS C:\> (Get-Content "$env:USERPROFILE\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.5_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini") -replace ';extension=pdo_pgsql', 'extension=pdo_pgsql' -replace ';extension=pgsql', 'extension=pgsql' | Set-Content "$env:USERPROFILE\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.5_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini"
```

Executes your application's database migrations

```
PS C:\task-manager> php artisan migrate
```

Create a Task model

```
php artisan make:model Task -mcr
```