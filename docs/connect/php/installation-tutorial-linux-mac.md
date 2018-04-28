---
title: Linux и macOS учебника установки драйвера Microsoft SQL Server для PHP | Документы Microsoft
ms.date: 04/11/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.topic: article
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.workload: Inactive
ms.openlocfilehash: 4ab3f815063a537b25b776b6b98fd26e74b7d2c4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Linux и macOS учебника установки драйвера Microsoft SQL Server для PHP
Следующие инструкции предполагают чистую среду и показано, как установка 7.x PHP, драйвер Microsoft ODBC, Apache и драйверы Майкрософт для PHP для SQL Server на Ubuntu 16.04 и 17.10, RedHat 7, Debian 8 и 9, Suse 12 и macOS X 10.11 и 10.12. Эти инструкции следует рекомендовать Установка драйверов с помощью нагрузка PECL, но можно также загрузить готовых двоичных файлов с [драйверы Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) Github страница проекта и установите их следуйте инструкциям в разделе [ Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md). Описание загрузки расширения и почему мы не добавляйте расширения файл PHP.ini, разделе [загрузка драйверов](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Эти инструкции по установке PHP 7.2 по умолчанию — см. примечания в начале каждого раздела, чтобы установить PHP 7.0 или 7.1.

## <a name="contents-of-this-page"></a>Содержимое этой страницы:

- [Установка драйверов в Ubuntu 16.04 и 17.10](#installing-the-drivers-on-ubuntu-1604-and-1710)
- [Установка драйверов в Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Установка драйверов в Debian 8 и 9](#installing-the-drivers-on-debian-8-and-9)
- [Установка драйверов при Suse 12](#installing-the-drivers-on-suse-12)
- [Установка драйверов на macOS El Capitan и Сьерра](#installing-the-drivers-on-macos-el-capitan-and-sierra)

## <a name="installing-the-drivers-on-ubuntu-1604-and-1710"></a>Установка драйверов в Ubuntu 16.04 и 17.10

> [!NOTE]
> Чтобы установить PHP 7.0 или 7.1, замените 7.2 7.0 или 7.1 в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установить PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.2 php7.2-dev php7.2-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установка драйвера ODBC для Ubuntu, следуя указаниям [Linux и macOS страница установки](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установить драйверы PHP для Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка Загрузка драйвера
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo service apache2 restart
```
Чтобы протестировать установку, в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-red-hat-7"></a>Установка драйверов в Red Hat 7

> [!NOTE]
> Чтобы установить PHP 7.0 или 7.1, замените remi php72 remi php70 или remi-php71 соответственно в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установить PHP

```
sudo su
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
subscription-manager repos --enable=rhel-7-server-optional-rpms
yum-config-manager --enable remi-php72
yum update
yum install php php-pdo php-xml php-pear php-devel re2c gcc-c++ gcc
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установка драйвера ODBC для Red Hat 7, следуя указаниям [Linux и macOS страница установки](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

Компиляция драйверов PHP с нагрузка PECL с PHP 7.2 требует более поздней GCC значения по умолчанию:
```
sudo yum-config-manager --enable rhel-server-rhscl-7-rpms
sudo yum install devtoolset-7
scl enable devtoolset-7 bash
```
### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установить драйверы PHP для Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
Проблемы в нагрузка PECL может препятствовать правильной установке последней версии драйверов, даже если вы обновили GCC. Для установки, загрузите пакеты и скомпилируйте вручную:
```
pecl download sqlsrv
tar xvzf sqlsrv-5.2.0.tgz
cd sqlsrv-5.2.0/
phpize
./configure --with-php-config=/usr/bin/php-config
make
sudo make install
```
В качестве альтернативы можно загрузить предварительно подготовленный двоичные файлы из [странице Github проекта](https://github.com/Microsoft/msphpsql/releases), или установить из репозитория Remi:
```
sudo yum install php-sqlsrv php-pdo_sqlsrv
```
### <a name="step-4-install-apache"></a>Шаг 4. Установка Apache
```
sudo yum install httpd
```
SELinux устанавливается по умолчанию и выполняется в режиме Enforcing. Чтобы разрешить Apache для подключения к базам данных через SELinux, выполните следующую команду:
```
sudo setsebool -P httpd_can_network_connect_db 1
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo apachectl restart
```
Чтобы протестировать установку, в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Установка драйверов в Debian 8 и 9

> [!NOTE]
> Чтобы установить PHP 7.0 или 7.1, замените 7.2 в следующих командах 7.0 или 7.1.

### <a name="step-1-install-php"></a>Шаг 1. Установить PHP
```
sudo su
apt-get install curl apt-transport-https
wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
apt-get update
apt-get install –y php7.2 php7.2-dev php7.2-xml
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установка драйвера ODBC для Debian, следуя указаниям [Linux и macOS страница установки](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Также может потребоваться создать нужный языковой стандарт для получения выходных данных PHP для правильного отображения в браузере. Например для языкового стандарта en_US UTF-8, выполните следующие команды:
```
sudo su
sed -i 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/g' /etc/locale.gen
locale-gen
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установить драйверы PHP для Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/30-pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/20-sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка Загрузка драйвера
```
sudo su
apt-get install libapache2-mod-php7.2 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.2
echo "extension=sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php/7.2/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo service apache2 restart
```
Чтобы протестировать установку, в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-suse-12"></a>Установка драйверов при Suse 12

> [!NOTE]
> Чтобы установить PHP 7.0, пропустить следующую команду Добавление репозитория - 7.0 значение по умолчанию PHP на suse 12.
> Чтобы установить PHP 7.1, замените URL-адрес репозитория ниже следующий URL-адрес: `http://download.opensuse.org/repositories/devel:/languages:/php:/php71/SLE_12/devel:languages:php:php71.repo`

### <a name="step-1-install-php"></a>Шаг 1. Установить PHP
```
sudo su
zypper -n ar -f http://download.opensuse.org/repositories/devel:languages:php/SLE_12/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установка драйвера ODBC для Suse 12, следуя указаниям [Linux и macOS страница установки](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установить драйверы PHP для Microsoft SQL Server
```
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка Загрузка драйвера
```
sudo su
zypper install apache2 apache2-mod_php7
a2enmod php7
echo "extension=sqlsrv.so" >> /etc/php7/apache2/php.ini
echo "extension=pdo_sqlsrv.so" >> /etc/php7/apache2/php.ini
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапустите Apache и протестировать пример сценария
```
sudo systemctl restart apache2
```
Чтобы протестировать установку, в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-macos-el-capitan-and-sierra"></a>Установка драйверов на macOS El Capitan и Сьерра

Если вы еще нет его, установите brew следующим образом:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Чтобы установить PHP 7.0 или 7.1, замените php@7.2 с php@7.0 или php@7.1 соответственно в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установить PHP

```
brew tap
brew tap homebrew/core
brew install php@7.2
```
PHP должна появиться в пути — запустить `php -v` чтобы убедиться, что используется правильная версия PHP. Если не является правильной версии PHP не указан в пути к, выполните следующую команду:
```
brew link --force --overwrite php@7.2
```

### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установка драйвера ODBC для macOS, следуя указаниям [Linux и macOS страница установки](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Кроме того необходимо установить средства убедитесь GNU:
```
brew install autoconf automake libtool
```

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установить драйверы PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
```
### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка Загрузка драйвера
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
Чтобы протестировать установку, в разделе [тестирования установки](#testing-your-installation) в конце этого документа.

## <a name="testing-your-installation"></a>Проверка установки

Чтобы протестировать этот пример скрипта, создайте файл с именем testsql.php в корневой каталог документов вашей системы. Это `/var/www/html/` в Ubuntu, Debian и Redhat, `/srv/www/htdocs` на SUSE, или `/usr/local/var/www` на macOS. Скопируйте следующий скрипт, заменив сервера, базы данных, имя пользователя и пароль, соответствующим образом.
```
<?php
$serverName = "yourServername";
$connectionOptions = array(
    "Database" => "yourDatabase",
    "Uid" => "yourUsername",
    "PWD" => "yourPassword"
);

//Establishes the connection
$conn = sqlsrv_connect($serverName, $connectionOptions);
if( $conn === false ) {
    die( FormatErrors( sqlsrv_errors()));
}

//Select Query
$tsql= "SELECT @@Version as SQL_VERSION";

//Executes the query
$getResults= sqlsrv_query($conn, $tsql);

//Error handling
if ($getResults == FALSE)
    die(FormatErrors(sqlsrv_errors()));
?>

<h1> Results : </h1>

<?php
while ($row = sqlsrv_fetch_array($getResults, SQLSRV_FETCH_ASSOC)) {
    echo ($row['SQL_VERSION']);
    echo ("<br/>");
}

sqlsrv_free_stmt($getResults);

function FormatErrors( $errors )
{
    /* Display errors. */
    echo "Error information: <br/>";
    foreach ( $errors as $error )
    {
        echo "SQLSTATE: ".$error['SQLSTATE']."<br/>";
        echo "Code: ".$error['code']."<br/>";
        echo "Message: ".$error['message']."<br/>";
    }
}
?>
```
Перейдите с помощью обозревателя http://localhost/testsql.php (http://localhost:8080/testsql.php на macOS). Теперь можно подключиться к базе данных SQL Server/Azure SQL.

## <a name="see-also"></a>См. также  
[Начало работы с драйверы Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md)

[Требования к системе для драйвера Microsoft PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)
