---
title: "Шаг 1: Загрузите образцы данных | Документы Microsoft"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 147860e9af8cce86d1a7ccbd3e53f20d240fcd49
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="step-1-download-the-sample-data"></a>Шаг 1. Скачивание образца данных

На этом шаге будет загрузить образец набора данных, а также скрипты. Данные и файлы скриптов опубликованы в Github, однако скрипт PowerShell скачает данные и файлы скриптов в выбранный вами локальный каталог.

## <a name="download-the-data-and-scripts"></a>Скачивание образцов данных и скриптов

1. Откройте командную консоль Windows PowerShell.

    Используйте параметр **Запуск от имени администратора**, если права администратора требуются для создания целевой каталог или записывать файлы в указанное назначение.

2. Выполните приведенные ниже команды PowerShell, изменив значение параметра *DestDir* на любой локальный каталог.  Значение по умолчанию, мы используем здесь — **TempPythonSQL**.

    ```
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\tempPythonSQL'
    ```
    
    Если папка, указанная в параметре *DestDir* , не существует, она будет создана скриптом PowerShell.
    
    Возникает сообщение об ошибке можно временно задать политику выполнения скриптов PowerShell для **Неограниченный** только в данном пошаговом руководстве, с помощью **обхода** аргумент и изменения в текущей области видимости сеанс. Выполнение этой команды не приводит к изменению конфигурации.
    
    `Set\-ExecutionPolicy Bypass \-Scope Process`

3. В зависимости от скорости подключения к Интернету скачивание может занять определенное время. После скачивания всех файлов скрипт PowerShell откроет папку, указанную в параметре  *DestDir*. В командное строке PowerShell выполните приведенную ниже команду и просмотрите скачанные файлы.

    ```
    ls
    ```
**Результаты:**

![Список файлов, скачанных скриптом PowerShell](media/sqldev-python-filelist.png "Список файлов, скачанных скриптом PowerShell")

## <a name="next-step"></a>Следующий шаг

[Шаг 2. Импорт данных в SQL Server с помощью PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Предыдущий шаг

[В базе данных аналитики Python для разработчиков SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>См. также:

[Машинного обучения служб с Python](../python/sql-server-python-services.md)



