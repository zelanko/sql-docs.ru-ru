---
title: Урок 1 загрузки образцов данных и скриптов для внедренных R (SQL Server машинного обучения) | Документы Microsoft
description: Руководство для внедрения в SQL Server R хранимые процедуры и функции T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a60a95da4fb701f3862c36e35a4bada6ef933b
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249837"
---
# <a name="lesson-1-download-data-and-scripts"></a>Урок 1: Загрузка данных и сценариев
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника для разработчиков SQL по использованию R в SQL Server.

На этом шаге вы загрузить образец набора данных и [!INCLUDE[tsql](../../includes/tsql-md.md)] файлы, которые используются в этом учебнике сценариев. Совместно используются данные и файлы скриптов в GitHub, но сценарий PowerShell будет загрузить файлы данных и сценариев в локальный каталог, по своему выбору.

## <a name="download-tutorial-files-from-github"></a>Загрузить файлы учебника из Github

1.  Откройте командную консоль Windows PowerShell.
  
    Используйте параметр **Запуск от имени администратора**, если для создания каталога назначения или записи файлов в указанный каталог требуются права администратора.
  
2.  Выполните приведенные ниже команды PowerShell, изменив значение параметра *DestDir* на любой локальный каталог.  Здесь использовано значение по умолчанию **TempRSQL**.
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    Если папка, указанная в параметре *DestDir* , не существует, она будет создана скриптом PowerShell.
  
    > [!TIP]
    > Если возникает ошибка, можно временно задать политику выполнения скриптов PowerShell **без ограничений** только для данного пошагового руководства. Для этого используйте аргумент Bypass и ограничьте изменения текущим сеансом.
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > Выполнение этой команды не приводит к изменению конфигурации.
  
    В зависимости от скорости подключения к Интернету скачивание может занять определенное время.
  
3.  После скачивания всех файлов скрипт PowerShell откроет папку, указанную в параметре  *DestDir*. В командное строке PowerShell выполните приведенную ниже команду и просмотрите скачанные файлы.
  
    ```
    ls
    ```
  
    **Результаты:**
  
    ![Список файлов, скачанных скриптом PowerShell](media/rsql-devtut-filelist.png "Список файлов, скачанных скриптом PowerShell")
  
## <a name="next-lesson"></a>Следующее занятие

[Занятие 2: Импорт данных в SQL Server с помощью PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Внедренные analytics R для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)
