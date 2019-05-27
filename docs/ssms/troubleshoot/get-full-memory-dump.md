---
title: Создание полного дампа памяти для устранения неполадок с SQL Server Management Studio (SSMS)
Description: Устранение неполадок, при которых SSMS перестает отвечать на запросы или аварийно завершает работу, путем сбора полного дампа памяти
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: how-to
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: dineth, sstein
ms.custom: ''
ms.date: 05/17/2019
ms.openlocfilehash: ff78af4ffcfe530ba28d47ec57852486523f859a
ms.sourcegitcommit: c29150492383f48ef484fa02a483cde1cbc68aca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65822512"
---
# <a name="get-full-memory-dump"></a>Создать полный дамп памяти

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Из этой статьи вы узнаете, как собирать диагностические сведения для устранения неполадок, при которых SQL Server Management Studio (SSMS) перестает отвечать на запросы или аварийно завершает работу.

Чтобы получить диагностические сведения для устранения неполадок, выполните следующие действия:

1. Скачайте [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Распакуйте файл в папку.

3. Откройте окно командной строки и выполните следующую команду.

    ```cmd
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    При появлении запроса на предоставление согласия с условиями лицензионного соглашения выберите **Принимаю**.

4. Запустите SQL Server Management Studio (SSMS), если программа еще не запущена.

5. Воспроизведите условия, при которых возникает проблема.

6. В окне командной строки отобразится текст о записи файла дампа. Дождитесь завершения процедуры.

7. Создайте папку и скопируйте в нее созданный DMP-файл.

8. Скопируйте в эту же папку следующие файлы:

    * C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll
    * C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll
    * C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll

9. Запакуйте папку в ZIP-архив.

## <a name="outofmemoryexception"></a>OutOfMemoryException

Вы также можете получить полный дамп памяти SSMS при возникновении исключения OutOfMemoryException (или любого другого управляемого исключения).

Чтобы получить диагностические сведения для устранения неполадок, связанных с исключением OutOfMemoryException в SSMS, выполните следующие действия:

1. Скачайте [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Распакуйте файл в папку.

3. Откройте окно командной строки и выполните следующую команду.

    ```cmd
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    При появлении запроса на предоставление согласия с условиями лицензионного соглашения выберите **Принимаю**.

4. Запустите SQL Server Management Studio, если программа еще не запущена.

5. Воспроизведите условия, при которых возникает проблема.

6. В окне командной строки отобразится текст о записи файла дампа. Дождитесь завершения процедуры.

7. Создайте папку и скопируйте в нее созданный DMP-файл.

8. Скопируйте в эту же папку следующие файлы:

    * C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll
    * C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll
    * C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll

9. Запакуйте папку в ZIP-архив.

## <a name="next-steps"></a>Следующие шаги

[Среда SQL Server Management Studio](../sql-server-management-studio-ssms.md)