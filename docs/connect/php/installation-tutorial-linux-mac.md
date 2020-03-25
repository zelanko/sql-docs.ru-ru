---
title: Руководство по установке драйверов Майкрософт для PHP для SQL Server в Linux и MacOS | Документация Майкрософт
ms.date: 12/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: 913b6d95a7bb9a690f0a8cdd7d8c88b29782f876
ms.sourcegitcommit: 577e7467821895f530ec2f97a33a965fca808579
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79058578"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Руководство по установке драйверов Майкрософт для PHP для SQL Server в Linux и MacOS
В следующих инструкциях предполагается чистая среда и показано, как установить PHP 7.x, драйвер Microsoft ODBC, веб-сервер Apache и драйверы Майкрософт для PHP для SQL Server в Ubuntu 16.04, 18.04 и 19.10, RedHat 7 и 8, Debian 8, 9 и 10, SUSE 12 и 15, Alpine 3.11 (экспериментальная версия) и macOS 10.13, 10.14 и 10.15. В этих инструкциях рекомендуется установка драйверов с помощью PECL, но вы можете скачать предварительно созданные двоичные файлы со страницы проекта [драйверов Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) на сайте GitHub и установить их по инструкциям из статьи [Loading the Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md) (Загрузка драйверов Майкрософт для PHP для SQL Server). Описание процесса загрузки расширений и причины, по которым расширения не добавляются в файл php.ini, см. в статье [о загрузке драйверов](../../connect/php/loading-the-php-sql-driver.md#loading-the-driver-at-php-startup).

Эти инструкции по умолчанию устанавливают PHP 7.4. Обратите внимание, что некоторые поддерживаемые дистрибутивы Linux по умолчанию используют PHP 7.1 и более ранних версий, которые не поддерживаются последней версией драйверов PHP для SQL Server. Изучите рекомендации в начале каждого раздела, чтобы установить вместо них версию PHP 7.2 или 7.3.

Также включены инструкции по установке диспетчера процессов PHP FastCGI (PHP-FPM) в Ubuntu. Это необходимо, если вместо Apache используется веб-сервер nginx.

## <a name="contents-of-this-page"></a>Содержимое этой страницы:

- [Установка драйверов в Ubuntu 16.04, 18.04 и 19.10](#installing-the-drivers-on-ubuntu-1604-1804-and-1910)
- [Установка драйверов с помощью PHP-FPM в Ubuntu](#installing-the-drivers-with-php-fpm-on-ubuntu)
- [Установка драйверов в Red Hat 7 и 8](#installing-the-drivers-on-red-hat-7-and-8)
- [Установка драйверов в Debian 8, 9 и 10](#installing-the-drivers-on-debian-8-9-and-10)
- [Установка драйверов в Suse 12 и 15](#installing-the-drivers-on-suse-12-and-15)
- [Установка драйверов в Alpine 3.11](#installing-the-drivers-on-alpine-311)
- [Установка драйверов в macOS High Sierra, Mojave и Catalina](#installing-the-drivers-on-macos-high-sierra-mojave-and-catalina)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1910"></a>Установка драйверов в Ubuntu 16.04, 18.04 и 19.10

> [!NOTE]
> Чтобы установить PHP 7.2 или 7.3, замените 7.4 на 7.2 или 7.3 в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Ubuntu, следуя инструкциям в [статье со сведениями об установке в Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

Если в системе только одна версия PHP, последний шаг можно упростить: `phpenmod sqlsrv pdo_sqlsrv`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка загрузки драйвера
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo service apache2 restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-with-php-fpm-on-ubuntu"></a>Установка драйверов с помощью PHP-FPM в Ubuntu

> [!NOTE]
> Чтобы установить PHP 7.2 или 7.3, замените 7.4 на 7.2 или 7.3 в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```bash
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.4 php7.4-dev php7.4-xml php7.4-fpm -y --allow-unauthenticated
```
Проверьте состояние службы PHP-FPM, выполнив следующее:
```
systemctl status php7.4-fpm
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Ubuntu, следуя инструкциям в [статье со сведениями об установке в Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl config-set php_ini /etc/php/7.3/fpm/php.ini
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```
Если в системе только одна версия PHP, последний шаг можно упростить: `phpenmod sqlsrv pdo_sqlsrv`.

Убедитесь, что `sqlsrv.ini` и `pdo_sqlsrv.ini` находятся в `/etc/php/7.4/fpm/conf.d/`:
```
ls /etc/php/7.4/fpm/conf.d/*sqlsrv.ini
```
Перезапустите службу PHP-FPM:
```
sudo systemctl restart php7.4-fpm
```

### <a name="step-4-install-and-configure-nginx"></a>Шаг 4. Установка и настройка nginx
```
sudo apt-get update
sudo apt-get install nginx
sudo systemctl status nginx
```
Чтобы настроить nginx, необходимо изменить файл `/etc/nginx/sites-available/default`. Добавьте `index.php` в список под разделом со следующим текстом: `# Add index.php to the list if you are using PHP`:
```
# Add index.php to the list if you are using PHP
index index.html index.htm index.nginx-debian.html index.php;
```
Затем измените раздел после `# pass PHP scripts to FastCGI server` следующим образом:
```
# pass PHP scripts to FastCGI server
#
location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
}
```
### <a name="step-5-restart-nginx-and-test-the-sample-script"></a>Шаг 5. Перезапуск nginx и тестирование примера скрипта
```
sudo systemctl restart nginx.service
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-red-hat-7-and-8"></a>Установка драйверов в Red Hat 7 и 8

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP

Чтобы установить PHP в Red Hat 7, выполните следующее:
> [!NOTE]
> Чтобы установить PHP 7.2 или 7.3, замените remi-php74 строкой remi-php72 или remi-php73 соответственно в следующих командах.
```
sudo su
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install https://rpms.remirepo.net/enterprise/remi-release-7.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum install yum-utils
yum-config-manager --enable remi-php74
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```

Чтобы установить PHP в Red Hat 8, выполните следующее:
> [!NOTE]
> Чтобы установить PHP 7.2 или 7.3, замените remi-7.4 на remi-7.2 или remi-7.3 соответственно в следующих командах.
```
sudo su
dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
dnf install yum-utils
dnf module reset php
dnf module install php:remi-7.4
subscription-manager repos --enable codeready-builder-for-rhel-8-x86_64-rpms
dnf update
dnf install php-pdo php-pear php-devel
```

### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Red Hat 7 или 8, следуя инструкциям в [статье со сведениями об установке в Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```

Можно также установить их из репозитория Remi:
```
sudo yum install php-sqlsrv
```
### <a name="step-4-install-apache"></a>Шаг 4. Установка Apache
```
sudo yum install httpd
```
SELinux устанавливается по умолчанию и выполняется в принудительном режиме. Чтобы разрешить Apache подключаться к базам данных через SELinux, выполните следующую команду:
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo apachectl restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-debian-8-9-and-10"></a>Установка драйверов в Debian 8, 9 и 10

> [!NOTE]
> Чтобы установить PHP 7.2 или 7.3, замените 7.4 на 7.2 или 7.3 в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.4 php7.4-dev php7.4-xml php7.4-intl
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Debian, следуя инструкциям в [статье со сведениями об установке в Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Кроме того, может потребоваться создать правильный языковой стандарт, чтобы выходные данные PHP правильно отображались в браузере. Например, для языкового стандарта en_US UTF-8 выполните следующие команды:
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```
Может потребоваться добавить `/usr/sbin` в `$PATH`, так как там находится исполняемый файл `locale-gen`.

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.4/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.4/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.4 sqlsrv pdo_sqlsrv
```

Если в системе только одна версия PHP, последний шаг можно упростить: `phpenmod sqlsrv pdo_sqlsrv`. Как и в случае с `locale-gen`, `phpenmod` находится в `/usr/sbin`, поэтому может потребоваться добавить этот каталог в `$PATH`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка загрузки драйвера
```
sudo su
apt-get install libapache2-mod-php7.4 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.4
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo service apache2 restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Установка драйверов в Suse 12 и 15

> [!NOTE]
> В приведенных ниже инструкциях замените `<SuseVersion>` нужной версией Suse. Если вы используете Suse Enterprise Linux 15, используйте значение SLE_15 или SLE_15_SP1. Для SUSE 12 используйте SLE_12_SP4 (или выше, если применимо). Не все версии PHP доступны для всех версий Suse Linux. В `http://download.opensuse.org/repositories/devel:/languages:/php` указано, какие версии Suse имеют доступную версию PHP по умолчанию, а в `http://download.opensuse.org/repositories/devel:/languages:/php:/` — какие еще версии PHP доступны для разных версий Suse.

> [!NOTE]
> Пакеты для PHP 7.4 недоступны для SUSE 12. Чтобы установить PHP 7.2, замените URL-адрес репозитория в команде ниже следующим URL-адресом: `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.
> Чтобы установить PHP 7.3, замените URL-адрес репозитория в команде ниже следующим URL-адресом: `https://download.opensuse.org/repositories/devel:/languages:/php:/php73/<SuseVersion>/devel:languages:php:php73.repo`.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Suse, следуя инструкциям в [статье со сведениями об установке в Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
> [!NOTE]
> Если вы получаете сообщение об ошибке вида `Connection to 'pecl.php.net:443' failed: Unable to find the socket transport "ssl"`, измените скрипт pecl в папке /usr/bin/pecl, удалив аргумент `-n` в последней строке. Этот аргумент запрещает PECL загружать ini-файлы при вызове PHP, что мешает загрузить расширение OpenSSL PECL.

```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка загрузки драйвера
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo systemctl restart apache2
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-alpine-311"></a>Установка драйверов в Alpine 3.11

> [!NOTE]
> Поддержка Alpine находится на этапе эксперимента.

> [!NOTE]
> Версия PHP по умолчанию — 7.3. Альтернативные версии PHP недоступны из других репозиториев для Alpine 3.11. Вместо этого можно скомпилировать PHP из источника.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
Пакеты PHP для Alpine находятся в репозитории `edge/community`. Добавьте следующую строку в `/etc/apt/repositories`, заменив `<mirror>` на URL-адрес зеркального отображения репозитория Alpine:
```
http://<mirror>/alpine/edge/community
```
Далее выполните:
```
sudo su
apk update
apk add php7 php7-dev php7-pear php7-pdo php7-openssl autoconf make g++
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Alpine, следуя инструкциям в [статье со сведениями об установке в Linux](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/10_pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/00_sqlsrv.ini
```
Может потребоваться определить языковой стандарт:
```
export LC_ALL=C
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка загрузки драйвера
```
sudo apk add php7-apache2 apache2
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo rc-service apache2 restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.


## <a name="installing-the-drivers-on-macos-high-sierra-mojave-and-catalina"></a>Установка драйверов в macOS High Sierra, Mojave и Catalina

Установите brew, как описано ниже, если у вас ее еще нет:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Чтобы установить PHP 7.2 или 7.3, замените php@7.4 на php@7.2 или php@7.3, соответственно, в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP

```
brew tap
brew tap homebrew/core
brew install php@7.4
```
PHP теперь будет указана в пути. Запустите `php -v` и убедитесь, что используется правильная версия PHP. Если в пути нет PHP или есть PHP неправильной версии, выполните следующую команду:
```
brew link --force --overwrite php@7.4
```

### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для macOS, следуя инструкциям в [статье со сведениями об установке в macOS](../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md). 

Кроме того, может потребоваться установить средства make для GNU:
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка загрузки драйвера
```
brew install apache2
```
Чтобы найти файл конфигурации Apache (`httpd.conf`) для установки Apache, выполните 
```
/usr/local/bin/apachectl -V | grep SERVER_CONFIG_FILE
``` 
Следующие команды добавляют необходимую конфигурацию в `httpd.conf`. Не забудьте указать путь, возвращенный предыдущей командой, вместо `/usr/local/etc/httpd/httpd.conf`:
```
echo "LoadModule php7_module /usr/local/opt/php@7.4/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo apachectl restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="testing-your-installation"></a>Тестирование установки

Чтобы протестировать этот пример скрипта, создайте файл с именем testsql.php в корневом каталоге документов системы. Это каталог `/var/www/html/` в Ubuntu, Debian и Redhat, `/srv/www/htdocs` в SUSE, `/var/www/localhost/htdocs` в Alpine и `/usr/local/var/www` в macOS. Скопируйте приведенный ниже скрипт, заменив имя сервера, имя базы данных, имя пользователя и пароль правильными значениями. В Alpine 3.11 также может потребоваться указать **CharacterSet** как UTF-8 в массиве `$connectionOptions`.
```
<?php
$serverName = "yourServername";
$connectionOptions = array(
    "database" => "yourDatabase",
    "uid" => "yourUsername",
    "pwd" => "yourPassword"
);

// Establishes the connection
$conn = sqlsrv_connect($serverName, $connectionOptions);
if ($conn === false) {
    die(formatErrors(sqlsrv_errors()));
}

// Select Query
$tsql = "SELECT @@Version AS SQL_VERSION";

// Executes the query
$stmt = sqlsrv_query($conn, $tsql);

// Error handling
if ($stmt === false) {
    die(formatErrors(sqlsrv_errors()));
}
?>

<h1> Results : </h1>

<?php
while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
    echo $row['SQL_VERSION'] . PHP_EOL;
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

function formatErrors($errors)
{
    // Display errors
    echo "Error information: <br/>";
    foreach ($errors as $error) {
        echo "SQLSTATE: ". $error['SQLSTATE'] . "<br/>";
        echo "Code: ". $error['code'] . "<br/>";
        echo "Message: ". $error['message'] . "<br/>";
    }
}
?>
```
Перейдите в браузере на страницу https://localhost/testsql.php (https://localhost:8080/testsql.php в Mac OS). Теперь вы сможете подключиться к базе данных SQL Server или SQL Azure.

## <a name="see-also"></a>См. также:  
[Getting Started with the Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md) (Начало работы с драйверами Майкрософт для PHP для SQL Server)

[Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md)

[Системные требования драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
