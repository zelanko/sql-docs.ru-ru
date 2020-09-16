---
description: Получение диагностических данных после аварийного завершения работы SQL Server Management Studio (SSMS)
title: Устранение неполадок с зависаниями системы или сбоями в SSMS
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.reviewer: dnethi
ms.custom: seo-lt-2019
ms.date: 09/18/2019
ms.openlocfilehash: 2a6f7d1ac44b40b1b58ebe0a2a595e9f69f1ab63
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480067"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>Получение диагностических данных после аварийного завершения работы SQL Server Management Studio (SSMS)

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

## <a name="get-full-memory-dump-after-an-unresponsive-system-or-crash"></a>Получение полного дампа памяти после зависания или сбоя системы

Вы можете создать полный дамп памяти для устранения неполадок с SQL Server Management Studio (SSMS), когда программа перестает отвечать на запросы или аварийно завершает работу.

Чтобы получить диагностические сведения для устранения неполадок, при которых SSMS перестает отвечать на запросы или аварийно завершает работу, выполните следующие действия.

1. Скачайте [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Распакуйте файл в папку.

3. Откройте окно командной строки и выполните следующую команду.

    ```console
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    При появлении запроса на предоставление согласия с условиями лицензионного соглашения выберите *Принимаю*.

4. Запустите среду SSMS, если она еще не запущена.

5. Воспроизведите проблему.

6. В окне командной строки отобразится текст о записи файла дампа. Дождитесь завершения процедуры.

7. Создайте папку и скопируйте в нее созданный DMP-файл.

8. Скопируйте в эту же папку следующие файлы:

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Запакуйте папку в ZIP-архив.

## <a name="get-full-memory-dump-for-an-outofmemoryexception"></a>Получение полного дампа памяти для исключения OutOfMemoryException

Получите полный дамп памяти SSMS при возникновении исключения OutOfMemoryException.

Полный дамп памяти можно получить для любого управляемого исключения.

Чтобы получить диагностические сведения для устранения неполадок, связанных с исключением OutOfMemoryException в SSMS, выполните указанные ниже действия.

1. Скачайте [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Распакуйте файл в папку.

3. Откройте окно командной строки и выполните следующую команду.

    ```console
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    При появлении запроса на предоставление согласия с условиями лицензионного соглашения выберите *Принимаю*.

4. Запустите SQL Server Management Studio, если программа еще не запущена.

5. Воспроизведите проблему.

6. В окне командной строки отобразится текст о записи файла дампа. Дождитесь завершения процедуры.

7. Создайте папку и скопируйте в нее созданный DMP-файл.

8. Скопируйте в эту же папку следующие файлы:

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Запакуйте папку в ZIP-архив.
