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
manager: craigg
ms.openlocfilehash: e62fc14eff52fa64e9e9f9dc041cc3c8601230e5
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744614"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Загрузка драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья содержит инструкции по загрузке [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] в пространство процессов PHP.  
  
Можно загрузить предварительно созданные драйверы для своей платформы из [драйверы Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) странице проекта в Github. Каждый пакет установки содержит файлы драйвера SQLSRV и PDO_SQLSRV потоками и однопоточных варианта. В Windows они также доступны в 32-разрядных и 64-разрядных вариантов. См. в разделе [требования к системе для драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md) список файлов драйверов, которые содержатся в каждом пакете. Файл драйвера должно соответствовать версии PHP, архитектура и threadedness среду PHP.

В Linux и macOS, драйверы можно также установить с помощью PECL, обнаруженных в [учебник по установке](../../connect/php/installation-tutorial-linux-mac.md).

Вы также можете создавать драйверы из источника, при построении PHP или с помощью `phpize`. Если вы решили создать драйверы из источника, у вас есть возможность создавать их статически в PHP вместо создания расширения как общий, добавив `--enable-sqlsrv=static --with-pdo_sqlsrv=static` (в Linux и macOS) или `--enable-sqlsrv=static --with-pdo-sqlsrv=static` (в Windows) для `./configure` при использовании команды Построение PHP. Дополнительные сведения о PHP система сборки и `phpize`, см. в разделе [документации по PHP](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Перемещение файла драйвера в каталог расширения  
Драйвер должен находиться в каталоге, где его можно найти в среде выполнения PHP. Проще всего поместить файл драйвера в каталог расширения PHP по умолчанию — чтобы найти каталог по умолчанию, запустите `php -i | sls extension_dir` на Windows или `php -i | grep extension_dir` в Linux и Mac OS. Если не используется расширение каталога по умолчанию, указать каталог, в файле конфигурации PHP (php.ini) с помощью **extension_dir** параметр. Например, в Windows, если вы поместили файл драйвера вашей `c:\php\ext` directory, добавьте следующую строку в файл php.ini:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Загрузка драйвера при запуске PHP  
Чтобы загружать драйвер SQLSRV при запуске PHP, сначала поместите файл драйвера в свой каталог расширений. Затем выполните следующие действия:  
  
1.  Чтобы включить **SQLSRV** изменить драйвер, **php.ini** , добавив следующую строку в раздел расширения, изменив имя файла соответствующим образом:  
  
    В Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    В Linux, если вы скачали предварительно созданные двоичные файлы для распространения: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Если была выполнена компиляция двоичного SQLSRV из источника или с PECL, она будет вместо называться sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  Чтобы включить **PDO_SQLSRV** драйвера, расширение объектов данных PHP (PDO) должна быть доступна, виде встроенного расширения или динамически загруженного расширения.

    В Windows предварительно созданные двоичные файлы PHP поставляются с PDO встроенными, поэтому нет необходимости, чтобы изменить файл php.ini для загрузки в нее. Если, однако вы бы PHP из источника и указано использовать отдельное расширение PDO для построения, он будет называться `php_pdo.dll`, также необходимо скопировать его в каталог расширения и добавьте следующую строку в файл php.ini:  
    ```
    extension=php_pdo.dll  
    ```
    В Linux после установки PHP, используя диспетчер пакетов системы PDO, вероятно, устанавливается как расширение динамически загружаемые с именем pdo.so. Расширение PDO должны загружаться перед расширение PDO_SQLSRV или загрузка завершится ошибкой. Расширения обычно загружаются с помощью отдельного INI-файлов, и эти файлы доступны для чтения после php.ini. Таким образом Если pdo.so загружается через свой собственный INI-файла, не требуется отдельный файл Загрузка драйвера PDO_SQLSRV после PDO. 

    Чтобы определить каталог, в котором находятся файлы, относящихся к модулю INI-файле, запустите `php --ini` и запишите этот каталог, в списке `Scan for additional .ini files in:`. Найти файл, который загружает pdo.so (скорее всего предшествует число, например 10 pdo.ini). Числовой префикс указывает порядок загрузки INI-файлов, пока файлы, которые не имеют числовой префикса загружаются в алфавитном порядке. Создайте файл для загрузки файла драйвера PDO_SQLSRV, называется 30-pdo_sqlsrv.ini (любое число больше, чем тот, который снабжает pdo.ini works) или pdo_sqlsrv.ini (если pdo.ini без префикса в число) и добавьте следующую строку, изменив имя файла как соответствующие:  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Как с SQLSRV, если была выполнена компиляция двоичного PDO_SQLSRV из источника или с PECL, она будет вместо называться pdo_sqlsrv.so:
    ```
    extension=pdo_sqlsrv.so
    ```
    Скопируйте этот файл в каталог, содержащий INI-файлов. 

    Если была выполнена компиляция PHP из источника, со встроенной поддержкой PDO, отдельного INI-файла не требуется, и соответствующую строку выше можно добавить в файл php.ini.
  
3.  Перезапустите веб-сервер.  
  
> [!NOTE]  
> Чтобы проверить, загружен ли драйвер, запустите сценарий, который вызывает [phpinfo()](https://php.net/manual/en/function.phpinfo.php).  
  
Дополнительные сведения о директивах **php.ini** см. в статье [Описание встроенных директив php.ini](https://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>См. также:  
[Приступая к работе с драйверами Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Системные требования драйверов Майкрософт для PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по API драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
