---
title: Шаг 1 скачивание образца данных | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 07a9b5219649b370b0a5df1e53cf75765f18ec7f
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888322"
---
# <a name="step-1-download-the-sample-data"></a>Шаг 1: Скачивание образца данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья входит учебник по, [Python в базе данных аналитики для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md). 

Данные и скрипты в этом руководстве используются на сайте Github. На этом шаге используется сценарий PowerShell для загрузки файлов данных и скриптов в локальный каталог по своему выбору.

## <a name="run-the-script"></a>Запустите сценарий

1. Откройте командную консоль Windows PowerShell.

    Используйте параметр **Запуск от имени администратора**, если требуются права администратора для создания каталога назначения или записи файлов в указанное место назначения.

2. Выполните приведенные ниже команды PowerShell, изменив значение параметра *DestDir* на любой локальный каталог.  Значение по умолчанию, мы использовали здесь — `C:\temp\pysql`.

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    Если папка, указанная в параметре *DestDir* , не существует, она будет создана скриптом PowerShell.
    
    Если отобразится сообщение об ошибке, временно задать политику выполнения скриптов PowerShell **Неограниченный** в этом пошаговом руководстве с помощью **обход** аргумент и ограничьте изменения текущим сеансом. Выполнение этой команды не приводит к изменению конфигурации.
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. В зависимости от подключения к Интернету скачивание может занять некоторое время. 

## <a name="view-results"></a>Просмотр результатов

После скачивания всех файлов скрипт PowerShell откроет папку, указанную в параметре  *DestDir*. 

+ В командной строке PowerShell выполните следующую команду, чтобы получить список файлов, которые были загружены.

    ```ps
    ls
    ```

![Список файлов, скачанных скриптом PowerShell](media/sqldev-python-filelist.png "Список файлов, скачанных скриптом PowerShell")

## <a name="next-step"></a>Следующий шаг

[Шаг 2. Импорт данных в SQL Server с помощью PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Предыдущий шаг

[В базе данных аналитики Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>См. также

[Расширение Python в SQL Server](../concepts/extension-python.md)


