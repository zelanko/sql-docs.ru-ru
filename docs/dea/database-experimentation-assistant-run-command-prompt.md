---
title: Запустить помощник базы данных службы "Экспериментирование" в командной строке для обновления до SQL Server
description: Запустить помощник базы данных службы "Экспериментирование" в командной строке
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
manager: jroth
ms.openlocfilehash: c4603bf5fec8f1df8ae1e7fe0e711bf7b6e8f1e9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794427"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>Запустить помощник базы данных службы "Экспериментирование" в командной строке

В этой статье описывается, как использовать окно командной строки для захвата трассировки в базе данных службы "Экспериментирование" Assistant (веб), а затем проанализировать результаты. 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Запуск новой записи рабочей нагрузки с помощью команды Инициатив

Для начала новой записи рабочей нагрузки, выполните следующую команду:

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Пример**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>Воспроизводить рабочую нагрузку

1.  Войдите в компьютер контроллера распределенного воспроизведения.
2.  Преобразуйте трассировку рабочей нагрузки, которые собраны с помощью команды Инициатив в файл IRF:

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  Запуск записи трассировки на целевом компьютере под управлением SQL Server с помощью StartReplayCaptureTrace.sql.
       
    1\.  В SQL Server Management Studio (SSMS), откройте < Dea_InstallPath\>\Scripts\StartReplayCaptureTrace.sql.
    
    2\.  Запустите `Set @durationInMins=0` , чтобы запись данных трассировки не останавливается автоматически после указанного времени.
    
    В.  Чтобы задать максимальный размер файла для файла трассировки, выполните `Set @maxfilesize`. Рекомендуемый размер — 200 (в МБ).
    
    Г.  Изменить `@Tracefile` присвоить уникальное имя для файла трассировки.
    
    Д.  Изменить `@dbname` для указания имени базы данных, если необходимо записать рабочую нагрузку только для конкретной базы данных. По умолчанию регистрируются рабочей нагрузки на всем сервере. 
4.  Воспроизводить файл IRF на целевом экземпляре SQL Server.

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    1\.  Для проверки состояния, откройте окно командной строки и выполните `DReplay status -f 1`.
        
    2\.  Чтобы остановить воспроизведение, такие как, если вы увидите, что pass % ниже, чем ожидается, откройте окно командной строки и запустите `DReplay cancel`.

5.  Остановите запись трассировки на целевом экземпляре SQL Server.
6.  Откройте `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7.  Изменить `@Tracefile` сопоставляемый путь к файлу трассировки на целевом компьютере под управлением SQL Server.
8.  Запустите сценарий для целевого компьютера под управлением SQL Server.

## <a name="analyze-traces-by-using-the-dea-command"></a>Анализ трассировок с помощью команды Инициатив

Чтобы начать новый анализ трассировки, выполните следующую команду:

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Пример**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>Следующие шаги

19-минутный введение Инициатив и демонстрации в следующем видео:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
