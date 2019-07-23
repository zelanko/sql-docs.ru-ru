---
title: Поддержка LocalDB | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6da7f1aed956c8b2f5c71496c9c121f6006eabb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935951"
---
# <a name="support-for-localdb"></a>Поддержка LocalDB

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB — это упрощенная версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая была доступна с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]момента. В этом разделе обсуждается, как можно установить соединение с базой данных на экземпляре LocalDB.

## <a name="remarks"></a>Remarks

Дополнительные сведения о LocalDB, в том числе Установка LocalDB и настройка экземпляра LocalDB, см. в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разделе электронной документации по [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Экспресс-LocalDB.

Вкратце, LocalDB позволяет выполнять следующие задачи:

-   Использовать программу **sqllocaldb.exe i** для поиска имени экземпляра по умолчанию.

-   Использовать ключевое слово строки подключения **AttachDBFilename** для указания файла базы данных, который сервер должен присоединить. Если при использовании **AttachDBFilename**не указано имя базы данных в ключевом слове строки подключения **Database** , то база данных будет удалена из экземпляра LocalDB при закрытии приложения.

-   Чтобы указать экземпляр LocalDB в строке подключения, выполните указанные ниже действия. Например, Вот пример строки подключения SQLSRV:

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    Далее приведен пример строки подключения PDO_SQLSRV:  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

При необходимости можно создать экземпляр LocalDB с помощью программы sqllocaldb.exe. Для добавления и изменения баз данных в локальном экземпляре LocalDB можно также воспользоваться программой sqlcmd.exe. Например, `sqlcmd -S (localdb)\v11.0`. (При запуске в службах IIS необходимо запустить с использованием правильной учетной записи, чтобы получить те же результаты, что и при выполнении в командной строке; дополнительные сведения см. в разделе [Использование LocalDB с полными службами IIS, часть 2. владение экземпляром](https://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx) .)

Ниже приведены примеры строк подключения с помощью драйвера SQLSRV, который подключается к базе данных в именованном экземпляре LocalDB с именем myInstance:

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Ниже приведены примеры строк подключения с помощью драйвера PDO_SQLSRV, который подключается к базе данных в именованном экземпляре LocalDB с именем myInstance:  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Инструкции по установке LocalDB см. в [документации по LocalDB](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). При использовании программы sqlcmd. exe для изменения данных в экземпляре LocalDB необходима [служебная программа sqlcmd](../../tools/sqlcmd-utility.md).

## <a name="see-also"></a>См. также:

[Подключение к серверу](../../connect/php/connecting-to-the-server.md)
