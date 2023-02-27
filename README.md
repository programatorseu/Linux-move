# Linux setup

## 1. Install PHP / Apache / Mysql

like always to make sure everything is updated 
-  issue with (brak mb_string) PHP 8.2
```
apt-get install php-mbstring 
```
```bash
sudo apt-get update
```

install repo ppa:ondrej

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt -y install php7.4
```

install popular modules (digital ocean recommendation)

```bash
sudo apt-get install -y php7.4-cli php7.4-json php7.4-common php7.4-mysql php7.4-zip php7.4-gd php7.4-mbstring php7.4-curl php7.4-xml php7.4-bcmath
```

easy switch ; 

```bash
sudo update-alternatives --config php
```



**mysql**

```bash
sudo apt install mysql-server
```

```bash
sudo systemctl start mysql.service
sudo mysql

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

CREATE USER 'username'@'host' IDENTIFIED WITH authentication_plugin BY 'password';
CREATE USER 'sammy'@'localhost' IDENTIFIED BY 'password';

GRANT PRIVILEGE ON database.table TO 'username'@'host';
FLUSH Privileges 
exit;

```

to check status : 

```bash
systemctl status mysql.service
sudo systemctl start mysql # to run in any case
```

Apache already installed



## 2. Install composer

```bash
sudo apt install php-cli unzip
    cd ~
    curl -sS https://getcomposer.org/installer -o composer-setup.php
    HASH=`curl -sS https://composer.github.io/installer.sig` #verify installer
# verify that inslatation is safe to ru : 
php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"

#install globally
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

```



### 3. Install laravel

```bash
composer global require laravel/installer
laravel new blog
composer create-project --prefer-dist laravel/laravel blog "5.8.*"
```

## 4 install visual studio code 

```bash
# 1. download code 
# 2. run installation 
sudo apt install ./code_1.61.2-1634656828_amd64.deb
```

**settings** -> check settings.json

### 5. Install python

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.9
```



### 6. Install node / npm

```bash
sudo apt install nodejs
node -v 
sudo apt install npm
```

## 7. Install Albert



https://albertlauncher.github.io/installing/



## 8. Key Remap - tweak tool

alt as ctrl 

ctrl as alt 

super leave as it is 



## 9. Install git

```bash
sudo apt install git-all
```



## Things to do after installing distro

- driver update (additional from menu)

- reduce swap use

- Tableplus
# Add TablePlus repo
`sudo add-apt-repository "deb [arch=amd64] https://deb.tableplus.com/debian/22 tableplus main"`

# Install
```bash
sudo apt update
sudo apt install tableplus
```

- PowerLine for Bash
`sudo add-apt-repository universe`
`sudo apt install --yes powerline`

edit `$HOME/.bashrc`
```bash
# Powerline configuration
if [ -f /usr/share/powerline/bindings/bash/powerline.sh ]; then
  powerline-daemon -q
  POWERLINE_BASH_CONTINUATION=1
  POWERLINE_BASH_SELECT=1
  source /usr/share/powerline/bindings/bash/powerline.sh
fi
```
source it :)

```
gsettings set org.gnome.shell.extensions.dash-to-dock background-opacity 0.8
```

https://github.com/spxak1/weywot/blob/main/guides/mxkeys_linux.md

## Hyperline

```https://releases.hyper.is/download/deb```
lokalizacja  config hyper by default `~/.hyper.js `
pluginy
```js
    plugins: [
        "hyperline",
        "hyperpower",
        "hyper-font-ligatures",
        "hyper-one-dark",
        "hyper-pane",
        "hyper-search",
        "hypercwd",
        "hyper-active-tab"
    ],
```

