Install
=========

```
    $ git clone git@github.com:zhouitpro/drupaldockerdev.git
    $ docker-composer up -d
```

Work dir is ~/www/

mysql
=========

   database: drupal
   user: root
   password: root


phpMyadmin config.inc.php
=========
```
    $cfg['Servers'][$i]['host'] = 'mysql';
```

Drupal Settings.php to support drush.
===========
```
    if (drupal_is_cli()) {
      $databases = array(
        'default' =>
          array(
            'default' =>
              array(
                'database' => 'mydb',
                'username' => 'root',
                'password' => 'root',
                'host'     => '127.0.0.1',
                'port'     => '9527',
                'driver'   => 'mysql',
                'prefix'   => '',
              ),
          ),
      );

    }
    else {
      $databases = array(
        'default' =>
          array(
            'default' =>
              array(
                'database' => 'mydb',
                'username' => 'root',
                'password' => 'root',
                'host'     => 'mysql',
                'port'     => '',
                'driver'   => 'mysql',
                'prefix'   => '',
              ),
          ),
      );
    }
```
