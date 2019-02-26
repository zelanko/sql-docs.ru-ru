---
title: Linux и macOS учебник по установке драйверов Майкрософт для PHP для SQL Server | Документация Майкрософт
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: a31b17b8fbe2130b84b27be08d1a6218d697f9f2
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744634"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux и macOS учебник по установке драйверов Майкрософт для PHP для SQL Server
Следующие инструкции предполагают чистую среду и показано, как установить PHP 7.x, драйвер Microsoft ODBC, Apache и драйверов Майкрософт для PHP для SQL Server на Ubuntu 16.04, 18.04 и 18.10, RedHat 7, Debian 8 и 9, Suse 12 и 15 и macOS 10.12 , 10.13 и 10.14. Эти инструкции уведомить, установка драйверов с помощью PECL, но вы также можете скачать предварительно созданные двоичные файлы из [драйверы Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) Github страница проекта и установите их инструкциям из раздела [ Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md). Описание расширения загрузки и почему мы не добавляйте расширения в файл php.ini, см. в разделе на [загрузка драйверов](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Эти инструкции установки PHP 7.3 по умолчанию. Обратите внимание, что некоторые поддерживается по умолчанию дистрибутивов Linux для PHP 7.0 или более ранней версии, который не поддерживается для драйверов PHP для SQL Server — см. примечания в начале каждого раздела, чтобы вместо этого установить PHP 7.1 или 7.2.

## <a name="contents-of-this-page"></a>Содержимое этой страницы:

- [Установка драйверов в Ubuntu 16.04, 18.04 и 18.10](#installing-the-drivers-on-ubuntu-1604-1804-and-1810)
- [Установка драйверов в Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Установка драйверов в Debian 8 и 9](#installing-the-drivers-on-debian-8-and-9)
- [Установка драйверов в Suse 12 и 15](#installing-the-drivers-on-suse-12-and-15)
- [Установка драйверов в macOS Sierra High Sierra и Mojave](#installing-the-drivers-on-macos-sierra-high-sierra-and-mojave)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1810"></a>Установка драйверов в Ubuntu 16.04, 18.04 и 18.10

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените 7.3 7.1 или 7.2 в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.3 php7.3-dev php7.3-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Драйвер ODBC для Ubuntu, следуя инструкциям [страница установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настроить загрузку драйвера
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo service apache2 restart
```
Чтобы протестировать установку, см. в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-red-hat-7"></a>Установка драйверов в Red Hat 7

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените remi php73 remi php71 или remi-php72 соответственно в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget https://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum install yum-utils
yum-config-manager --enable remi-php73
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Драйвер ODBC для Red Hat 7, следуя инструкциям [страница установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

Компиляция драйверов PHP с PECL с PHP 7.2 и 7.3 требует более поздней GCC, чем значение по умолчанию:
```
sudo yum-config-manager --enable rhel-server-rhscl-7-rpms
sudo yum install devtoolset-7
scl enable devtoolset-7 bash
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
Проблема в PECL может препятствовать правильной установки драйверов последней версии, даже если вы обновили GCC. Для установки, загрузите пакеты и скомпилировать вручную (аналогичные действия для pdo_sqlsrv):
```
pecl download sqlsrv
tar xvzf sqlsrv-5.6.0.tgz
cd sqlsrv-5.6.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
Кроме того, можно загрузить предварительно созданные двоичные файлы из [странице проекта Github](https://github.com/Microsoft/msphpsql/releases), или установить из репозитория Remi:
```
sudo yum install php-sqlsrv
```
### <a name="step-4-install-apache"></a>Шаг 4. Установка Apache
```
sudo yum install httpd
```
SELinux устанавливается по умолчанию и выполняется в режиме Enforcing. Чтобы разрешить Apache подключаться к базам данных через SELinux, выполните следующую команду:
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo apachectl restart
```
Чтобы протестировать установку, см. в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Установка драйверов в Debian 8 и 9

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените 7.3 в следующих командах 7.1 или 7.2.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install -y php7.3 php7.3-dev php7.3-xml
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Драйвер ODBC для Debian, следуя инструкциям [страница установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Кроме того, может потребоваться создать нужный языковой стандарт для получения выходных данных PHP для правильного отображения в браузере. Например для языкового стандарта UTF-8 en_US, выполните следующие команды:
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настроить загрузку драйвера
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/30-pdo_sqlsrv.ini
echo "extension=sqlsrv.so" >> /etc/php/7.3/apache2/conf.d/20-sqlsrv.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo service apache2 restart
```
Чтобы протестировать установку, см. в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Установка драйверов в Suse 12 и 15

> [!NOTE]
> В приведенных ниже инструкциях замените <SuseVersion> с версией Suse — Если вы используете Suse Enterprise Linux 15, она будет SLE_15 или SLE_15_SP1 и аналогично для других версий. Все версии Suse Linux - вы найдете доступны не все версии PHP `http://download.opensuse.org/repositories/devel:/languages:/php` чтобы увидеть, какие версии Suse имеют версию по умолчанию доступны, PHP или `http://download.opensuse.org/repositories/devel:/languages:/php:/` также просмотреть, какие доступны другие версии PHP для каких версий Suse.

> [!NOTE]
> Пакеты для PHP 7.3 недоступны для Suse 12. Чтобы установить PHP 7.1, замените URL-адрес репозитория ниже следующий URL-адрес: `https://download.opensuse.org/repositories/devel:/languages:/php:/php71/<SuseVersion>/devel:languages:php:php71.repo`.
> Чтобы установить PHP 7.2, замените URL-адрес репозитория ниже следующий URL-адрес: `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Драйвер ODBC для Suse, следуя инструкциям [страница установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
> [!NOTE]
> Если вы получаете сообщение об `Connection to 'pecl.php.net:443' failed: Unable to find the socket transport "ssl"`, измените сценарий pecl в /usr/bin/pecl и удалять `-n` переключиться в последней строке. Этот параметр предотвращает загрузку ini-файлы, когда вызывается PHP, который запрещает загрузку расширение OpenSSL PECL.

```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настроить загрузку драйвера
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo systemctl restart apache2
```
Чтобы протестировать установку, см. в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-macos-sierra-high-sierra-and-mojave"></a>Установка драйверов в macOS Sierra High Sierra и Mojave

Если у вас еще нет ее, установите brew следующим образом:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените php@7.3 с php@7.1 или php@7.2 соответственно в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP

```
brew tap
brew tap homebrew/core
brew install php@7.3
```
PHP теперь должен находиться в пути — запустить `php -v` для убедитесь, что используется правильная версия PHP. Если он не имеет требуемую версию PHP не указан в пути, используйте следующую команду:
```
brew link --force --overwrite php@7.3
```

### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установка драйвера ODBC для macOS, следуя инструкциям [страница установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Кроме того необходимо установить средства make GNU:
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настроить загрузку драйвера
```
brew install apache2
```
Чтобы найти файл конфигурации для установки Apache Apache, выполните 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
и замените путь к `httpd.conf` в следующих командах:
```
echo "LoadModule php7_module /usr/local/opt/php@7.2/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo apachectl restart
```
Чтобы протестировать установку, см. в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="testing-your-installation"></a>Тестирование установки

Чтобы протестировать этот пример сценария, создайте файл с именем testsql.php в корневой каталог документов системы. Это `/var/www/html/` на Ubuntu, Debian и Redhat, `/srv/www/htdocs` в SUSE, или `/usr/local/var/www` в macOS. Скопируйте приведенный ниже сценарий, заменив сервера, базы данных, имя пользователя и пароль, соответствующим образом.
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
Введите в браузере https://localhost/testsql.php (https://localhost:8080/testsql.php в Mac OS). Теперь можно подключиться к базе данных SQL Server и SQL Azure.

## <a name="see-also"></a>См. также:  
[Приступая к работе с драйверами Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md)

[Системные требования драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
