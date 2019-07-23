---
title: Руководство по установке драйверов Майкрософт для PHP для SQL Server в Linux и MacOS | Документация Майкрософт
ms.date: 06/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: ulvii
ms.author: v-ulibra
manager: v-mabarw
ms.openlocfilehash: 7a2312a4ff6af5a11825274e3e010873ef2d3bd9
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68256707"
---
# <a name="linux-and-macos-installation-tutorial-for-the-microsoft-drivers-for-php-for-sql-server"></a>Руководство по установке драйверов Майкрософт для PHP для SQL Server в Linux и MacOS
Следующие инструкции описывают, как установить PHP 7.x, драйвер Microsoft ODBC, Apache и драйверы Майкрософт для PHP для SQL Server в чистом окружении Ubuntu 16.04, 18.04 и 18.10, RedHat 7, Debian 8 и 9, Suse 12 и 15 или macOS 10.12, 10.13 и 10.14. В этих инструкциях рекомендуется установка драйверов с помощью PECL, но вы можете скачать предварительно созданные двоичные файлы со страницы проекта [драйверов Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) на сайте GitHub и установить их по инструкциям из статьи [Loading the Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md) (Загрузка драйверов Майкрософт для PHP для SQL Server). Описание процесса загрузки расширений и причины, по которым расширения не добавляются в файл php.ini, см. в статье [о загрузке драйверов](../../connect/php/loading-the-php-sql-driver.md##loading-the-driver-at-php-startup).

Эти инструкции по умолчанию устанавливают PHP 7.3. Обратите внимание, что некоторые поддерживаемые дистрибутивы Linux по умолчанию используют PHP 7.0 или более раннюю версию, которые не поддерживаются драйвером для PHP для SQL Server. Изучите рекомендации в начале каждого раздела, чтобы установить вместо них версию PHP 7.1 или 7.2.

## <a name="contents-of-this-page"></a>Содержимое этой страницы:

- [Установка драйверов в Ubuntu 16.04, 18.04 и 18.10](#installing-the-drivers-on-ubuntu-1604-1804-and-1810)
- [Установка драйверов в Red Hat 7](#installing-the-drivers-on-red-hat-7)
- [Установка драйверов в Debian 8 и 9](#installing-the-drivers-on-debian-8-and-9)
- [Установка драйверов в Suse 12 и 15](#installing-the-drivers-on-suse-12-and-15)
- [Установка драйверов в macOS Sierra, High Sierra и Mojave](#installing-the-drivers-on-macos-sierra-high-sierra-and-mojave)

## <a name="installing-the-drivers-on-ubuntu-1604-1804-and-1810"></a>Установка драйверов в Ubuntu 16.04, 18.04 и 18.10

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените 7.3 на 7.1 или 7.2 в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```
sudo su
add-apt-repository ppa:ondrej/php -y
apt-get update
apt-get install php7.3 php7.3-dev php7.3-xml -y --allow-unauthenticated
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Ubuntu, следуя инструкциям на [странице установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.3/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.3/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.3 sqlsrv pdo_sqlsrv
```

Если в системе имеется только одна версия PHP, последний шаг можно упростить до `phpenmod sqlsrv pdo_sqlsrv`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка загрузки драйвера
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
exit
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo service apache2 restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-red-hat-7"></a>Установка драйверов в Red Hat 7

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените remi-php73 строкой remi-php71 или remi-php72, соответственно, в следующих командах.

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
Установите драйвер ODBC для Red Hat 7, следуя инструкциям на [странице установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="step-3-install-the-php-drivers-for-microsoft-sql-server"></a>Шаг 3. Установка драйверов PHP для Microsoft SQL Server
```
sudo pecl install sqlsrv
sudo pecl install pdo_sqlsrv
sudo su
echo extension=pdo_sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/pdo_sqlsrv.ini
echo extension=sqlsrv.so >> `php --ini | grep "Scan for additional .ini files" | sed -e "s|.*:\s*||"`/sqlsrv.ini
exit
```

Кроме того, вы можете скачать предварительно созданные двоичные файлы со страницы [проекта на сайте GitHub](https://github.com/Microsoft/msphpsql/releases) или установить их из репозитория Remi.
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

## <a name="installing-the-drivers-on-debian-8-and-9"></a>Установка драйверов в Debian 8 и 9

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените 7.3 на 7.1 или 7.2 в следующих командах.

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
Установите драйвер ODBC для Debian, следуя инструкциям на [странице установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

Кроме того, может потребоваться создать правильный языковой стандарт, чтобы выходные данные PHP правильно отображались в браузере. Например, для языкового стандарта en_US UTF-8 выполните следующие команды:
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
printf "; priority=20\nextension=sqlsrv.so\n" > /etc/php/7.3/mods-available/sqlsrv.ini
printf "; priority=30\nextension=pdo_sqlsrv.so\n" > /etc/php/7.3/mods-available/pdo_sqlsrv.ini
exit
sudo phpenmod -v 7.3 sqlsrv pdo_sqlsrv
```

Если в системе имеется только одна версия PHP, последний шаг можно упростить до `phpenmod sqlsrv pdo_sqlsrv`.

### <a name="step-4-install-apache-and-configure-driver-loading"></a>Шаг 4. Установка Apache и настройка загрузки драйвера
```
sudo su
apt-get install libapache2-mod-php7.3 apache2
a2dismod mpm_event
a2enmod mpm_prefork
a2enmod php7.3
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo service apache2 restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="installing-the-drivers-on-suse-12-and-15"></a>Установка драйверов в Suse 12 и 15

> [!NOTE]
> В приведенных ниже инструкциях замените <SuseVersion> нужной версией Suse. Если вы используете Suse Enterprise Linux 15, используйте значение SLE_15 или SLE_15_SP1, и аналогично для других версий. Не все версии PHP доступны для всех версий Suse Linux. В `http://download.opensuse.org/repositories/devel:/languages:/php` указано, какие версии Suse имеют доступную версию PHP по умолчанию, а в `http://download.opensuse.org/repositories/devel:/languages:/php:/` — какие еще версии PHP доступны для разных версий Suse.

> [!NOTE]
> Пакеты для PHP 7.3 недоступны для Suse 12. Чтобы установить PHP 7.1, замените URL-адрес репозитория в команде ниже следующим URL-адресом: `https://download.opensuse.org/repositories/devel:/languages:/php:/php71/<SuseVersion>/devel:languages:php:php71.repo`.
> Чтобы установить PHP 7.2, замените URL-адрес репозитория в команде ниже следующим URL-адресом: `https://download.opensuse.org/repositories/devel:/languages:/php:/php72/<SuseVersion>/devel:languages:php:php72.repo`.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP
```
sudo su
zypper -n ar -f https://download.opensuse.org/repositories/devel:languages:php/<SuseVersion>/devel:languages:php.repo
zypper --gpg-auto-import-keys refresh
zypper -n install php7 php7-pear php7-devel php7-openssl
```
### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для Suse, следуя инструкциям на [странице установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

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

## <a name="installing-the-drivers-on-macos-sierra-high-sierra-and-mojave"></a>Установка драйверов в macOS Sierra, High Sierra и Mojave

Установите brew, как описано ниже, если у вас ее еще нет:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

> [!NOTE]
> Чтобы установить PHP 7.1 или 7.2, замените php@7.3 на php@7.1 или php@7.2, соответственно, в следующих командах.

### <a name="step-1-install-php"></a>Шаг 1. Установка PHP

```
brew tap
brew tap homebrew/core
brew install php@7.3
```
PHP теперь будет указана в пути. Запустите `php -v` и убедитесь, что используется правильная версия PHP. Если в пути нет PHP или есть PHP неправильной версии, выполните следующую команду:
```
brew link --force --overwrite php@7.3
```

### <a name="step-2-install-prerequisites"></a>Шаг 2. Установка необходимых компонентов
Установите драйвер ODBC для macOS, следуя инструкциям на [странице установки Linux и macOS](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md). 

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
Чтобы найти файл конфигурации Apache для установки Apache, выполните 
```
apachectl -V | grep SERVER_CONFIG_FILE
``` 
и замените путь к `httpd.conf` в следующих командах:
```
echo "LoadModule php7_module /usr/local/opt/php@7.3/lib/httpd/modules/libphp7.so" >> /usr/local/etc/httpd/httpd.conf
(echo "<FilesMatch .php$>"; echo "SetHandler application/x-httpd-php"; echo "</FilesMatch>";) >> /usr/local/etc/httpd/httpd.conf
```
### <a name="step-5-restart-apache-and-test-the-sample-script"></a>Шаг 5. Перезапуск Apache и тестирование примера скрипта
```
sudo apachectl restart
```
Чтобы протестировать установку, воспользуйтесь разделом [Тестирование установки](#testing-your-installation) в конце этого документа.

## <a name="testing-your-installation"></a>Тестирование установки

Чтобы протестировать этот пример скрипта, создайте файл с именем testsql.php в корневом каталоге документов системы. Это каталог `/var/www/html/` на Ubuntu, Debian и Redhat, `/srv/www/htdocs` в SUSE и `/usr/local/var/www` в macOS. Скопируйте приведенный ниже скрипт, заменив имя сервера, имя базы данных, имя пользователя и пароль правильными значениями.
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
