---
title: "Загрузка драйвера PHP SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cb2200b2c5d151981e9dcdf8322dd7c43b91c6ee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="loading-the-php-sql-driver"></a>Загрузка драйвера SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья содержит инструкции по загрузке [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] в пространстве процесса PHP.  
  
Существует два способа загрузки драйвера. Драйвер можно загрузить при запуске PHP или во время выполнения скрипта PHP.  
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Перемещение файла драйвера в каталог расширения  
Независимо от используемой процедуры первым шагом является помещение файла драйвера в каталог, где его сможет найти среда выполнения PHP. Поэтому поместите файл драйвера в каталог расширения PHP. Список файлов драйверов, которые устанавливаются вместе с [, см. в статье](../../connect/php/system-requirements-for-the-php-sql-driver.md) Требования к системе (драйверы Майкрософт для PHP для SQL Server) [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
При необходимости укажите расположение каталога файла драйвера в файле конфигурации PHP (php.ini) с помощью **extension_dir** параметр. Например, при помещении файла драйвера в каталог c:\php\ext, используйте следующий параметр:  
  
```  
extension_dir = "c:\PHP\ext"  
```  
  
## <a name="loading-the-driver-at-php-startup"></a>Загрузка драйвера при запуске PHP  
Чтобы загрузить [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] при запуске PHP, сначала переместите файл драйвера в каталог расширения. Затем выполните следующие действия:  
  
1.  Чтобы включить **SQLSRV** изменить драйвер, **php.ini** , добавив следующую строку в раздел расширения или изменив строку, которая уже существует:  
  
    В Windows (этот пример использует драйвер поток версии 4.0 для PHP 7): 
    ```  
    extension=php_sqlsrv_7_ts.dll  
    ```  
    В системе Linux (этот пример использует версию установки нагрузка PECL): 
    ```  
    extension=sqlsrv.so  
    ```  
    Чтобы включить **PDO_SQLSRV** изменить драйвер, **php.ini** , добавив следующую строку в раздел расширения или изменив строку, которая уже существует:  
  
    В Windows (этот пример использует драйвер поток версии 4.0 для PHP 7):
    ```  
    extension=php_pdo_sqlsrv_7_ts.dll  
    ```  
    В системе Linux (этот пример использует версию установки нагрузка PECL):
    ```  
    extension=pdo_sqlsrv.so  
    ```  
  
2.  Если вы хотите использовать **PDO_SQLSRV** драйвера, объекты данных PHP (PDO) должен иметь расширение доступно, виде встроенного расширения или динамически загруженного расширения. Если необходимо загрузить драйвер PDO_SQLSRV динамически, библиотека php_pdo.dll (или pdo.so в Linux) должен находиться в каталоге расширения и должен находиться в php.ini следующую строку:

    В Windows:  
    ```
    extension=php_pdo.dll  
    ```  
    На платформе Linux:  
    ```
    extension=pdo.so  
    ```  
  
3.  Перезапустите веб-сервер.  
  
> [!NOTE]  
> Чтобы определить, был ли драйвер успешно загружен, запустите скрипт, который вызывает [phpinfo()](http://go.microsoft.com/fwlink/?LinkId=108678).  
  
Дополнительные сведения о директивах **php.ini** см. в статье [Описание основных директив php.ini](http://go.microsoft.com/fwlink/?LinkId=105817).  
  
## <a name="loading-the-driver-at-php-script-runtime"></a>Загрузка драйвера во время выполнения скрипта PHP  
Чтобы загрузить [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] во время выполнения скрипта, сначала переместите файл драйвера в каталог расширения. Затем добавьте следующую строку в начало скрипта PHP, который соответствует имени файла драйвера:  
  
```  
dl('php_pdo_sqlsrv_7_ts.dll');  
```  
  
Дополнительные сведения о функциях PHP, связанных с динамически загружаемыми расширениями см. в разделе [dl](http://go.microsoft.com/fwlink/?LinkId=105818) и [extension_loaded.](http://go.microsoft.com/fwlink/?LinkId=105819)  
  
## <a name="see-also"></a>См. также:  
[Приступая к работе с драйвером PHP SQL](../../connect/php/getting-started-with-the-php-sql-driver.md)
[, см. в статье](../../connect/php/system-requirements-for-the-php-sql-driver.md)
[Руководство по программированию для драйвера PHP SQL](../../connect/php/programming-guide-for-php-sql-driver.md)
[Справочник по API драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  

