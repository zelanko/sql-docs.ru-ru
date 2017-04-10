---
title: "Шаг&#160;1. Скачивание образца данных (учебник по дополнительным аналитическим функциям в базе данных) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 32a5d5ad-c58a-4669-a90d-ef296b48fcd8
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Шаг&#160;1. Скачивание образца данных (учебник по дополнительным аналитическим функциям в базе данных)
В этом шаге вы скачаете образец набора данных и файлы скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)], которые будут использоваться в этом пошаговом руководстве. Данные и файлы скриптов опубликованы в Github, однако скрипт PowerShell скачает данные и файлы скриптов в выбранный вами локальный каталог.  
  
## Скачивание образцов данных и скриптов  
  
1.  Откройте командную консоль Windows PowerShell.  
  
    Используйте параметр **Запуск от имени администратора**, если для создания каталога назначения или записи файлов в указанный каталог требуются права администратора.  
  
2.  Выполните приведенные ниже команды PowerShell, изменив значение параметра *DestDir* на любой локальный каталог.  Здесь использовано значение по умолчанию **TempRSQL**.  
  
    ```  
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”  
    $wc = New-Object System.Net.WebClient  
    $wc.DownloadFile($source, $ps1_dest)  
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’  
  
    ```  
  
    Если папка, указанная в параметре *DestDir*, не существует, она будет создана скриптом PowerShell.  
  
    > [!TIP]  
    > Если возникает ошибка, можно временно задать политику выполнения скриптов PowerShell **без ограничений** только для данного пошагового руководства. Для этого используйте аргумент Bypass и ограничьте изменения текущим сеансом.  
    >   
    >````  
    > Set\-ExecutionPolicy Bypass \-Scope Process  
    >````   
    > Выполнение этой команды не приводит к изменению конфигурации.  
  
    В зависимости от скорости подключения к Интернету скачивание может занять определенное время.  
  
3.  После скачивания всех файлов скрипт PowerShell откроет папку, указанную в параметре *DestDir*. В командное строке PowerShell выполните приведенную ниже команду и просмотрите скачанные файлы.  
  
    ```  
    ls  
    ```  
  
    **Результаты:**  
  
    ![list of files downloaded by PowerShell script](../../advanced-analytics/r-services/media/rsql-devtut-filelist.PNG "list of files downloaded by PowerShell script")  
  
## Следующий шаг  
[Шаг 2. Импорт данных в SQL Server с помощью PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## Предыдущий шаг  
[Дополнительные аналитические функции в базе данных для разработчиков SQL (учебник)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
## См. также:  
[Учебники по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
