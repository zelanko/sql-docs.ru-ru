---
title: "В драйвере PHP для SQL Server Support for LocalDB | Документы Microsoft"
ms.custom: 
ms.date: 02/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.prod_service: drivers
ms.component: php
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4dcf9e36eb3928bc606053bdfda441520155864a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="php-driver-for-sql-server-support-for-localdb"></a>PHP Driver for SQL Server Support for LocalDB (Поддержка драйвера PHP для SQL Server для LocalDB)

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)], облегченная версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], именуемая LocalDB, будут доступны. В этом разделе обсуждается, как можно установить соединение с базой данных на экземпляре LocalDB.

## <a name="remarks"></a>Remarks

Дополнительные сведения о LocalDB, включая установку и настройку экземпляра LocalDB, разделе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] раздел электронной документации на [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Express LocalDB.

LocalDB позволяет выполнять следующие действия.

-   Использовать программу **sqllocaldb.exe i** для поиска имени экземпляра по умолчанию.

-   Использовать ключевое слово строки подключения **AttachDBFilename** для указания файла базы данных, который сервер должен присоединить. Если при использовании **AttachDBFilename**не указано имя базы данных в ключевом слове строки подключения **Database** , то база данных будет удалена из экземпляра LocalDB при закрытии приложения.

-   Укажите экземпляр LocalDB в строке подключения. Например ниже приведен пример строки подключения SQLSRV:

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    Далее следует пример строки подключения PDO_SQLSRV:  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

При необходимости можно создать экземпляр LocalDB с помощью программы sqllocaldb.exe. Для добавления и изменения баз данных в локальном экземпляре LocalDB можно также воспользоваться программой sqlcmd.exe. Например, `sqlcmd -S (localdb)\v11.0`. (При работе в IIS, необходимо запустить использованием правильной учетной записи, чтобы получить те же результаты, что при запуске из командной строки; в разделе [с помощью LocalDB с полнофункциональными службами IIS, часть 2: владельцем экземпляра](http://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx) подробнее.)

Ниже приведены примеры строк подключения с помощью драйвера SQLSRV, подключающихся к базе данных в LocalDB, с именем экземпляра myInstance.

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Ниже приведены примеры строк подключения с помощью драйвера PDO_SQLSRV, подключающихся к базе данных в LocalDB, с именем экземпляра myInstance.  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Вы LocalDB можно загрузить из [страницы пакета дополнительных компонентов SQL Server 2012](http://go.microsoft.com/fwlink/?LinkID=236805), или из [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] экспресс-выпуск. Если вы будете использовать sqlcmd.exe для изменения данных в экземпляре LocalDB, вам потребуется sqlcmd из [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)], который можно получить из загрузки служебные программы командной строки в [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] страницы пакета дополнительных компонентов.

## <a name="see-also"></a>См. также:

[Подключение к серверу](../../connect/php/connecting-to-the-server.md)
