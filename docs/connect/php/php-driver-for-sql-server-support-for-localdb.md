---
title: Поддержка LocalDB | Документы Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: drivers
ms.component: php
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92be589df4038d152f07445d7cd5fa4ffafc935b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="support-for-localdb"></a>Поддержка LocalDB

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB — это облегченная версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] которого был доступен с [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]. В этом разделе обсуждается, как можно установить соединение с базой данных на экземпляре LocalDB.

## <a name="remarks"></a>Замечания

Дополнительные сведения о LocalDB, включая установку и настройку экземпляра LocalDB, разделе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] раздел электронной документации на [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Express LocalDB.

Вкратце LocalDB позволяет:

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

Инструкции по установке LocalDB см. в разделе [документации LocalDB](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). Если изменение данных в экземпляре LocalDB с помощью sqlcmd.exe потребуется [программы sqlcmd](../../tools/sqlcmd-utility.md).

## <a name="see-also"></a>См. также

[Подключение к серверу](../../connect/php/connecting-to-the-server.md)
