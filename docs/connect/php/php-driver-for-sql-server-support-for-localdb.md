---
title: Поддержка LocalDB | Документация Майкрософт
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
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67935951"
---
# <a name="support-for-localdb"></a>Поддержка LocalDB

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB — это упрощенная версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], доступная начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. В этом разделе обсуждается, как можно установить соединение с базой данных на экземпляре LocalDB.

## <a name="remarks"></a>Remarks

Дополнительные сведения о LocalDB, включая сведения о способах его установки и настройки экземпляра LocalDB, см. в разделах электронной документации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express LocalDB.

Если коротко, то LocalDB позволяет выполнять следующие действия.

-   Использовать программу **sqllocaldb.exe i** для поиска имени экземпляра по умолчанию.

-   Использовать ключевое слово строки подключения **AttachDBFilename** для указания файла базы данных, который сервер должен присоединить. Если при использовании **AttachDBFilename**не указано имя базы данных в ключевом слове строки подключения **Database** , то база данных будет удалена из экземпляра LocalDB при закрытии приложения.

-   Чтобы указать экземпляр LocalDB в строке подключения, выполните указанные ниже действия. Например, вот пример строки подключения SQLSRV:

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

При необходимости можно создать экземпляр LocalDB с помощью программы sqllocaldb.exe. Для добавления и изменения баз данных в локальном экземпляре LocalDB можно также воспользоваться программой sqlcmd.exe. Например, `sqlcmd -S (localdb)\v11.0`. (При выполнении в службах IIS службы необходимо запустить с правильной учетной записью, чтобы получить те же результаты, что и при запуске из командной строки; см. статью [Archived MSDN and TechNet Blogs ](https://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx)(Архивированные MSDN и блоги TechNet).

Ниже приведены примеры строк подключения с использованием драйвера SQLSRV, который подключается к базе данных в именованном экземпляре myInstance LocalDB:

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Ниже приведены примеры строк подключения с использованием драйвера PDO_SQLSRV, который подключается к базе данных в именованном экземпляре myInstance LocalDB:  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Инструкции по установке LocalDB см. в [документации по LocalDB](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). При использовании sqlcmd.exe для изменения данных в экземпляре LocalDB потребуется [служебная программа sqlcmd](../../tools/sqlcmd-utility.md).

## <a name="see-also"></a>См. также:

[Подключение к серверу](../../connect/php/connecting-to-the-server.md)
