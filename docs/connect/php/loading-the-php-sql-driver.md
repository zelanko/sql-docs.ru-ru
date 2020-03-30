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
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67936385"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Загрузка драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья содержит инструкции по загрузке [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] в пространство процессов PHP.  
  
Предварительно созданные драйверы для платформы можно загрузить на странице [драйверов Майкрософт для PHP в SQL Server](https://github.com/Microsoft/msphpsql/releases) на сайте GitHub. Каждый пакет установки содержит файлы драйверов SQLSRV и PDO_SQLSRV в потоковых и отдельных вариантах. В Windows они также доступны в 32-разрядных и 64-разрядных версиях. Список файлов драйверов, содержащихся в каждом пакете, см. в статье [System Requirements for the Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md) (Системные требования драйверов Майкрософт для PHP для SQL Server). Файл драйвера должен соответствовать версии PHP, архитектуре и потоковости среды PHP.

В Linux и macOS драйверы можно также установить с помощью PECL, как описано в [учебнике по установке](../../connect/php/installation-tutorial-linux-mac.md).

Вы также можете создать драйверы из источника при разработке PHP или с помощью `phpize`. Если вы решили создать драйверы из источника, можно создать их статически в PHP, а не в качестве общих расширений, добавив `--enable-sqlsrv=static --with-pdo_sqlsrv=static` (в Linux и macOS) или `--enable-sqlsrv=static --with-pdo-sqlsrv=static` (в Windows) в команду `./configure` при компиляции PHP. Дополнительные сведения о системе сборки PHP и `phpize` см. в [документации по PHP](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Перемещение файла драйвера в каталог расширения  
Файл драйвера должен размещаться в каталоге, где среда выполнения PHP сможет его найти. Проще всего разместить файл драйвера в каталоге расширений PHP по умолчанию. Чтобы найти каталог по умолчанию, запустите `php -i | sls extension_dir` в Windows или `php -i | grep extension_dir` в Linux/macOS. Если вы не используете каталог расширений по умолчанию, укажите каталог в файле конфигурации PHP (php.ini) с помощью параметра **extension_dir**. Например, в Windows, если вы поместили файл драйвера в каталог `c:\php\ext`, добавьте следующую строку в файл php.ini:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Загрузка драйвера при запуске PHP  
Чтобы загружать драйвер SQLSRV при запуске PHP, сначала поместите файл драйвера в свой каталог расширений. Затем выполните следующие действия:  
  
1.  Чтобы включить драйвер **SQLSRV**, добавьте в файле **php.ini** следующую строку в раздел расширения и измените имя файла соответствующим образом:  
  
    В Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    В Linux, если вы скачали предварительно созданные двоичные файлы для вашего дистрибутива, запустите следующий код: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Если вы выполнили компиляцию двоичного файла SQLSRV из источника или с помощью PECL, файл получит имя sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  Чтобы включить драйвер **PDO_SQLSRV**, расширение PHP Data Objects (PDO) должно быть доступно либо как встроенное расширение, либо как динамически загружаемое.

    В Windows предварительно созданные двоичные файлы PHP поставляются со встроенным PDO, поэтому не нужно изменять файл php.ini для его загрузки. Если вы скомпилировали PHP из источника и указали отдельное расширение PDO для сборки, оно будет называться `php_pdo.dll`. Необходимо скопировать его в каталог расширения и добавить следующую строку в файл php.ini:  
    ```
    extension=php_pdo.dll  
    ```
    В Linux, если вы установили PHP с помощью диспетчера пакетов системы, PDO, скорее всего, установится как динамически загруженное расширение с именем pdo.so. Расширение PDO нужно загрузить перед расширением PDO_SQLSRV, иначе загрузка завершится ошибкой. Расширения обычно загружаются с использованием отдельных INI-файлов, и эти файлы считываются после файла php.ini. Таким образом, если файл pdo.so загружается с использованием собственного INI-файла, то после PDO понадобится отдельный файл, загружающий драйвер PDO_SQLSRV. 

    Чтобы узнать, в каком каталоге находятся INI-файлы, относящиеся к расширению, запустите `php --ini` и обратите внимание на каталог, указанный в разделе `Scan for additional .ini files in:`. Найдите файл, загружающий pdo.so. Возможно, он имеет числовой префикс, например 10-pdo.ini. Числовой префикс указывает порядок загрузки INI-файлов. Файлы, не имеющие числового префикса, загружаются в алфавитном порядке. Создайте файл для загрузки файла драйвера PDO_SQLSRV с именем 30-pdo_sqlsrv.ini (подойдет любое число, большее, чем pdo.ini) или pdo_sqlsrv.ini (если у pdo.ini нет числового префикса) и добавьте в него следующую строку, изменив имя файла на подходящее.  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Как и в случае с SQLSRV, если вы выполнили компиляцию двоичного файла PDO_SQLSRV из источника или с помощью PECL, файл получит имя pdo_sqlsrv.so:
    ```
    extension=pdo_sqlsrv.so
    ```
    Скопируйте этот файл в каталог, содержащий другие INI-файлы. 

    Если вы скомпилировали PHP из источника со встроенной поддержкой PDO, то отдельный INI-файл не требуется и можно добавить в файл php.ini соответствующую указанную выше строку.
  
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
  
