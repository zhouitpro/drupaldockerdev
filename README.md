
Install
=========

install dnsmasq
```
    $brew install dnsmasq
    $cd $(brew --prefix); echo 'address=/.dev/127.0.0.1' > etc/dnsmasq.conf
    $sudo cp -v $(brew --prefix dnsmasq)/homebrew.mxcl.dnsmasq.plist /Library/LaunchDaemons
    $sudo launchctl load -w /Library/LaunchDaemons/homebrew.mxcl.dnsmasq.plist
    $sudo mkdir /etc/resolver
    $sudo bash -c 'echo "nameserver 127.0.0.1" > /etc/resolver/dev'
```


Install docker-sync
==========
http://docker-sync.io/
```
    $ gem install docker-sync
    $ brew install fswatch
```

clong and install
```
    $ git clone git@github.com:zhouitpro/drupaldockerdev.git
    $ docker-sync-stack start
```

Work dir is ~/www/Sites, if you want change this. <docker-sync.yml  (src: '~/www/Sites/') >

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
