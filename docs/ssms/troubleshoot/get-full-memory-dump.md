---
description: Создать полный дамп памяти
title: Получение полного дампа памяти для устранения неполадок в SSMS
Description: Соберите диагностические данные из SQL Server Management Studio (SSMS), чтобы устранить неполадки, связанные с аварийным завершением работы или зависанием системы.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.reviewer: drskwier, sstein
ms.custom: seo-lt-2019
ms.date: 05/17/2019
ms.openlocfilehash: d6055d14fd6edbc711c950aa194cd9b553cb3b78
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92035922"
---
# <a name="get-full-memory-dump"></a>Создать полный дамп памяти

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Из этой статьи вы узнаете, как собирать диагностические сведения для устранения неполадок, при которых SQL Server Management Studio (SSMS) перестает отвечать на запросы или аварийно завершает работу.

Чтобы получить диагностические сведения для устранения неполадок, выполните следующие действия:

1. Скачайте [ProcDump](/sysinternals/downloads/procdump).

2. Распакуйте файл в папку.

3. Откройте окно командной строки (например, `cmd.exe`) и выполните следующую команду:

    ```console
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

1. Скачайте [ProcDump](/sysinternals/downloads/procdump).

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

## <a name="share-the-information"></a>Обмен информацией

1. Чтобы передать сведения команде SSMS, зарегистрируйте проблему по адресу https://aka.ms/sqlfeedback.

2. Затем отправьте файл дампа памяти в OneDrive (или его эквивалент), откуда его можно получить.

    > [!Important]
    > Файлы дампа памяти могут содержать конфиденциальные сведения.

## <a name="next-steps"></a>Дальнейшие действия

[Среда SQL Server Management Studio](../sql-server-management-studio-ssms.md)