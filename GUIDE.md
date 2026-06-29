```
PS C:\> php -v
PHP 8.5.6 (cli) (built: May  6 2026 09:31:05) (ZTS Visual C++ 2022 x64)
Copyright (c) The PHP Group
Built by The PHP Group
Zend Engine v4.5.6, Copyright (c) Zend Technologies
    with Zend OPcache v8.5.6, Copyright (c), by Zend Technologies
```

```
PS C:\> composer -V
Composer version 2.9.8 2026-05-13 09:28:38
PHP version 8.5.6 (C:\Users\%USERNAME%\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.5_Microsoft.Winget.Source_8wekyb3d8bbwe\php.exe)
Run the "diagnose" command to get more detailed diagnostics output.
```

Uncomment in a text editor
`C:\Users\%USERNAME%\AppData\Local\Microsoft\WinGet\Packages\PHP.PHP.8.5_Microsoft.Winget.Source_8wekyb3d8bbwe\php.ini`
`;extension=fileinfo` to `extension=fileinfo`

Terminal
```
PS C:\> composer create-project laravel/laravel task-manager
cd task-manager
php artisan serve
```
