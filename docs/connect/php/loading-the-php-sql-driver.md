---
title: Загрузка драйверов Майкрософт для PHP для SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e3c6614425cf8796bd7ec462a62f9410b9ca5857
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936385"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Загрузка драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья содержит инструкции по загрузке [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] в пространство процессов PHP.  
  
Предварительно созданные драйверы для платформы можно скачать на странице проекта [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) GitHub. Каждый пакет установки содержит файлы драйверов SQLSRV и PDO_SQLSRV в потоковых и непотоковых вариантах. В Windows они также доступны в 32-разрядных и 64-разрядных вариантах. Список файлов драйверов, содержащихся в каждом пакете, см. в разделе [требования к системе для драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md) . Файл драйвера должен соответствовать версии PHP, архитектуре и среадеднесс среды PHP.

В Linux и macOS драйверы можно также установить с помощью PECL, как описано в [руководстве по установке](../../connect/php/installation-tutorial-linux-mac.md).

Можно также создать драйверы из источника при создании PHP или с помощью `phpize`. Если вы решили собрать драйверы из источника, вы можете создать их статически в PHP, а не создавать их как общие расширения, добавив `--enable-sqlsrv=static --with-pdo_sqlsrv=static` (в Linux и macOS) или `--enable-sqlsrv=static --with-pdo-sqlsrv=static` (в Windows) в команду, `./configure` если сборка PHP. Дополнительные сведения о системе сборки PHP и `phpize`см. в [документации по PHP](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Перемещение файла драйвера в каталог расширения  
Файл драйвера должен находиться в каталоге, где среда выполнения PHP может ее найти. Проще всего разместить файл драйвера в каталоге расширений PHP по умолчанию, чтобы найти каталог по умолчанию, запустить `php -i | sls extension_dir` в Windows или `php -i | grep extension_dir` Linux/macOS. Если вы не используете каталог расширений по умолчанию, укажите каталог в файле конфигурации PHP (PHP. ini) с помощью параметра **extension_dir** . Например, в Windows, если вы поместили файл драйвера в `c:\php\ext` каталог, добавьте следующую строку в PHP. ini:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Загрузка драйвера при запуске PHP  
Чтобы загружать драйвер SQLSRV при запуске PHP, сначала поместите файл драйвера в свой каталог расширений. Затем выполните следующие действия:  
  
1.  Чтобы включить драйвер **sqlsrv** , измените файл **PHP. ini** , добавив следующую строку в раздел Extension, изменив имя файла соответствующим образом:  
  
    В Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    В Linux, если вы скачали предварительно созданные двоичные файлы для распространения, выполните следующие действия. 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Если вы выполнили компиляцию файла SQLSRV binary из источника или с помощью PECL, вместо него будет использоваться имя sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  Чтобы включить драйвер **PDO_SQLSRV** , должно быть доступно расширение "объекты данных PHP (PDO)" либо в виде встроенного расширения, либо в виде динамически загружаемого расширения.

    В Windows предварительно созданные двоичные файлы PHP поставляются со встроенным PDO, поэтому нет необходимости изменять PHP. ini для его загрузки. Однако если вы откомпилированы PHP из источника и указали отдельное расширение PDO для сборки, оно будет называться `php_pdo.dll`, а необходимо скопировать его в каталог расширения и добавить следующую строку в PHP. ini:  
    ```
    extension=php_pdo.dll  
    ```
    В Linux, если вы установили PHP с помощью диспетчера пакетов системы, PDO, скорее всего, устанавливается как динамически загруженное расширение с именем pdo.so. Расширение PDO должно быть загружено до расширения PDO_SQLSRV, иначе загрузка завершится ошибкой. Расширения обычно загружаются с помощью отдельных ini-файлов, и эти файлы считываются после PHP. ini. Таким образом, если pdo.so загружается через собственный ini-файл, то после PDO требуется отдельный файл, загружающий драйвер PDO_SQLSRV. 

    Чтобы узнать, в каком каталоге находятся ini-файлы, относящиеся к расширению, `php --ini` выполните команду и обратите внимание `Scan for additional .ini files in:`на каталог, указанный в разделе. Найдите файл, загружающий pdo.so--возможно, он имеет префикс с номером, например 10-PDO. ini. Числовой префикс указывает порядок загрузки ini-файлов, а файлы, не имеющие числового префикса, загружаются в алфавитном порядке. Создайте файл для загрузки файла драйвера PDO_SQLSRV с именем 30-PDO_SQLSRV. ini (любое число, большее, чем имя, которое работает с префиксом PDO. ini Works) или PDO_SQLSRV. ini (если PDO. ini не предшествует номеру), и добавьте в него следующую строку, изменив имя файла на подходят  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Как и в случае с SQLSRV, если двоичный файл PDO_SQLSRV был скомпилирован из источника или с помощью PECL, вместо него будет использоваться имя PDO_SQLSRV. Поэтому:
    ```
    extension=pdo_sqlsrv.so
    ```
    Скопируйте этот файл в каталог, содержащий другие ini-файлы. 

    Если вы откомпилированы PHP из источника со встроенной поддержкой PDO, то не требуется отдельный ini-файл, и вы можете добавить соответствующую строку выше в PHP. ini.
  
3.  Перезапустите веб-сервер.  
  
> [!NOTE]  
> Чтобы проверить, загружен ли драйвер, запустите сценарий, который вызывает [phpinfo()](https://php.net/manual/en/function.phpinfo.php).  
  
Дополнительные сведения о директивах **php.ini** см. в статье [Описание встроенных директив php.ini](https://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>См. также:  
[Getting Started with the Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md) (Начало работы с драйверами Майкрософт для PHP для SQL Server)

[Системные требования драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по API драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
