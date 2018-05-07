---
title: Загрузка драйверов Майкрософт для PHP для SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7890c38877d05a69118a7c61ffe7261d1c9e91e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Загрузка драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта страница содержит инструкции по загрузке [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] в PHP пространстве процесса.  
  
Можно загрузить предварительно подготовленный драйверы для вашей платформы из [драйверы Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) странице Github проекта. Каждый пакет установки содержит файлы драйвера SQLSRV и PDO_SQLSRV потоками и однопоточных варианты. В Windows они также доступны в виде 32-разрядных и 64-разрядных Variant. В разделе [требования к системе для драйвера Microsoft SQL Server для PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md) список файлов драйверов, которые содержатся в каждом пакете. Файл драйвера должно соответствовать версии PHP, архитектура и threadedness среды PHP.

В Linux и macOS, драйверов можно также установить с помощью нагрузка PECL, обнаруженных в [установки учебника](../../connect/php/installation-tutorial-linux-mac.md).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Перемещение файла драйвера в каталог расширения  
Драйвер должен быть расположен в каталоге, где его сможет найти среда выполнения PHP. Можно легко помещение файла драйвера в каталог расширения PHP по умолчанию — чтобы найти каталог по умолчанию, запустите `php -i | sls extension_dir` в Windows или `php -i | grep extension_dir` на Linux или macOS. Если каталог расширение по умолчанию не используется, укажите каталог, в файле конфигурации PHP (php.ini) с помощью **extension_dir** параметр. Например, в Windows, если вы поместили файла драйвера вашей `c:\php\ext` directory, добавьте следующую строку в файл php.ini:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Загрузка драйвера при запуске PHP  
Чтобы загрузить драйвер SQLSRV, при запуске PHP, сначала переместите файл драйвера в каталог расширения. Затем выполните следующие действия:  
  
1.  Чтобы включить **SQLSRV** изменить драйвер, **php.ini** , добавив следующую строку в раздел расширения, изменив имя файла соответствующим образом:  
  
    В Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    В Linux, если вы скачали готовых двоичных файлов для распространения: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    При компиляции двоичных SQLSRV из источника или с нагрузка PECL получит вместо имя sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  Чтобы включить **PDO_SQLSRV** драйвера, объекты данных PHP (PDO) должен иметь расширение доступно, виде встроенного расширения или динамически загруженного расширения.

    В Windows готовых двоичных файлов PHP поставляются с PDO встроенные, поэтому нет необходимости изменить файл php.ini, чтобы загрузить ее. Если, однако были скомпилированы PHP из источника и указано отдельное расширение PDO для построения, он будет называться `php_pdo.dll`, и скопируйте его в каталог расширения и добавьте следующую строку в файл php.ini должна:  
    ```
    extension=php_pdo.dll  
    ```
    В Linux после установки PHP, с помощью диспетчера пакетов системы, PDO, скорее всего, устанавливается как динамически загружаемые расширения с именем pdo.so. Расширение PDO должны загружаться перед расширением PDO_SQLSRV, иначе произойдет сбой загрузки. Обычно расширения загружаются с помощью отдельного INI-файлов, и эти файлы доступны для чтения после php.ini. Таким образом Если pdo.so загружается через свой собственный INI-файла, не требуется отдельный файл Загрузка драйвера PDO_SQLSRV после PDO. 

    Чтобы определить каталог, которому расположены файлы .ini конкретного расширения, запустите `php --ini` и запишите каталога, выбранного в списке `Scan for additional .ini files in:`. Найдите файл, который загружает pdo.so (скорее всего предваряться число, например 10 pdo.ini). Числовой префикс указывает порядок загрузки INI-файлов, а файлы, которые не имеют числовой префикса загружаются в алфавитном порядке. Создайте файл для загрузки файла драйвера PDO_SQLSRV, называется 30-pdo_sqlsrv.ini (любое число больше, префиксы pdo.ini works) или pdo_sqlsrv.ini (если pdo.ini имеет префикс не число) и добавьте следующую строку, изменение файла как соответствующие:  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Как с SQLSRV, если выполнена компиляция двоичных PDO_SQLSRV из источника или с нагрузка PECL, получит вместо имя pdo_sqlsrv.so:
    ```
    extension=pdo_sqlsrv.so
    ```
    Скопируйте этот файл в каталог, содержащий INI-файлов. 

    Если выполнена компиляция PHP из источника со встроенной поддержкой PDO, отдельного INI-файла не требуется и соответствующую строку выше можно добавить в файл php.ini.
  
3.  Перезапустите веб-сервер.  
  
> [!NOTE]  
> Чтобы определить, был ли драйвер успешно загружен, запустите скрипт, который вызывает [phpinfo()](http://php.net/manual/en/function.phpinfo.php).  
  
Дополнительные сведения о **php.ini** директив, в разделе [описание основных директив php.ini](http://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>См. также  
[Начало работы с драйверы Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Требования к системе для драйвера Microsoft PHP для SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по API для драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
