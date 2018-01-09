---
title: "Шаг 1: Загрузите образцы данных | Документы Microsoft"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: "2"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 69bb2bbbc35bf13c4facc70508bb569714c66488
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="step-1-download-the-sample-data"></a>Шаг 1: Загрузите образец данных

В этой статье является частью учебника [analytics Python в базе данных для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

Данные и скриптов в этом учебнике используются на Github. На этом шаге используется сценарий PowerShell для загрузки файлов данных и сценариев в локальный каталог, по своему выбору.

## <a name="run-the-script"></a>Запустите сценарий

1. Откройте командную консоль Windows PowerShell.

    Используйте параметр **Запуск от имени администратора**, если права администратора требуются для создания целевой каталог или записывать файлы в указанное назначение.

2. Выполните приведенные ниже команды PowerShell, изменив значение параметра *DestDir* на любой локальный каталог.  Значение по умолчанию, мы используем здесь — `C:\temp\pysql`.

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    Если папка, указанная в параметре *DestDir* , не существует, она будет создана скриптом PowerShell.
    
    Возникает сообщение об ошибке, временно задать политику для выполнения скриптов PowerShell **Неограниченный** в данном пошаговом руководстве, с помощью **обхода** аргумент и областей изменения в текущем сеансе. Выполнение этой команды не приводит к изменению конфигурации.
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. В зависимости от подключения к Интернету загрузка может занять некоторое время. 

## <a name="view-the-results"></a>Просмотр результатов

После скачивания всех файлов скрипт PowerShell откроет папку, указанную в параметре  *DestDir*. 

+ В командной строке PowerShell выполните следующую команду, чтобы вывести список файлов, которые были загружены.

    ```ps
    ls
    ```

![Список файлов, скачанных скриптом PowerShell](media/sqldev-python-filelist.png "Список файлов, скачанных скриптом PowerShell")

## <a name="next-step"></a>Следующий шаг

[Шаг 2. Импорт данных в SQL Server с помощью PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Предыдущий шаг

[В базе данных аналитики Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>См. также:

[Машинного обучения служб с Python](../python/sql-server-python-services.md)


