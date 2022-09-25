# CodeIgniter 4 Admin

My ci4 admin demo

# [Running Multiple Applications with one CodeIgniter Installation](https://codeigniter.com/user_guide/general/managing_apps.html#running-multiple-applications-with-one-codeigniter-installation)

If you would like to share a common CodeIgniter framework installation, to manage several different applications, simply put all of the directories located inside your application directory into their own (sub)-directory.

For example, let’s say you want to create two applications, named `foo` and `bar`. 
You could structure your application project directories like this:

```
foo/
    app/
    public/
    tests/
    writable/
    env
    phpunit.xml.dist
    spark
bar/
    app/
    public/
    tests/
    writable/
    env
    phpunit.xml.dist
    spark
vendor/
    autoload.php
    codeigniter4/framework/
composer.json
composer.lock
```

This would have two apps, `foo` and `bar`, both having standard application directories and a `public` folder, and sharing a common `codeigniter4/framework`.

The `$systemDirectory` variable in `app/Config/Paths.php` inside each of those would be set to refer to the shared common `codeigniter4/framework` folder:

```php
<?php

namespace Config;

class Paths
{
    // ...

    public $systemDirectory = __DIR__ . '/../../../vendor/codeigniter4/framework/system';

    // ...
}
```

And modify the `COMPOSER_PATH` constant in `app/Config/Constants.php` inside each of those:

```php
<?php

defined('COMPOSER_PATH') || define('COMPOSER_PATH', ROOTPATH . '../vendor/autoload.php');
```

Only when you change the Application Directory, see Renaming or [Relocating the Application Directory](https://codeigniter.com/user_guide/general/managing_apps.html#renaming-app-directory) and modify the paths in the `index.php` and `spark`.
