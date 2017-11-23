---
title: "Урок 1: Загрузите образцы данных | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 32a5d5ad-c58a-4669-a90d-ef296b48fcd8
caps.latest.revision: "10"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59934357ad7f1a8f52a893209d0394760418d386
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-1-download-the-sample-data"></a>Урок 1: Загрузите образец данных

В этой статье является частью учебника для разработчиков SQL по использованию R в SQL Server.

На этом шаге вы загрузить образец набора данных и [!INCLUDE[tsql](../../includes/tsql-md.md)] файлы, которые используются в этом учебнике сценариев. Совместно используются данные и файлы скриптов в GitHub, но сценарий PowerShell будет загрузить файлы данных и сценариев в локальный каталог, по своему выбору.

## <a name="download-the-data-and-scripts"></a>Загрузка данных и сценариев

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

[Аналитика в базе данных R для разработчиков SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)
