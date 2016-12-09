# ionCube on Ubuntu 12.04.x

download and extract the IonCube Loader PHP modules
```
cd /var/www
wget http://downloads3.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz
tar xvfz ioncube_loaders_lin_x86-64.tar.gz
```

navigate over to server IP address + /ioncube/loader-wizard.php
```
e.g http://10.1.1.123/ioncube/loader-wizard.php
Select Local install
```

*Loader Wizard* will suggests which module to use
```
e.g ioncube_loader_lin_5.3.so
```

run the following command in terminal to find php extension_dir,
```
php -i | grep extension_dir
```

copy extension_dir path for next step
```
/usr/lib/php5/20090626+lfs
```

move module to php extension_dir
```
mv ioncube_loader_lin_5.3.so /usr/lib/php5/20090626+lfs
```

create ioncube.ini in Ubuntu 12.04
```
echo "zend_extension = /usr/lib/php5/20090626+lfs/ioncube_loader_lin_5.3.so" | sudo tee /etc/php5/conf.d/ioncube.ini
```

soft link to apache2
```
cd /etc/php5/apache2/conf.d 
sudo ln -fs /etc/php5/conf.d/ioncube.ini ioncube.ini
```

soft link to cli
```
cd /etc/php5/cli/conf.d 
sudo ln -fs /etc/php5/conf.d/ioncube.ini ioncube.ini
```
