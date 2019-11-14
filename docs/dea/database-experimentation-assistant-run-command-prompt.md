---
title: Запуск Database Experimentation Assistant из командной строки
description: Запуск Database Experimentation Assistant из командной строки
ms.custom: seo-lt-2019
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
ms.openlocfilehash: c3b87eafa460cfef69666a3837f56626dab81d47
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056576"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt-sql-server"></a>Запуск Database Experimentation Assistant из командной строки (SQL Server)

В этой статье описывается, как использовать окно командной строки для записи трассировки в Database Experimentation Assistant (ДЕА), а затем анализировать результаты. 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Запуск новой записи рабочей нагрузки с помощью команды ДЕА

Чтобы начать новую запись рабочей нагрузки, выполните следующую команду:

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Пример**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>Воспроизведение рабочей нагрузки

1.  Войдите на компьютер контроллера распределенное воспроизведение.
2.  Преобразуйте трассировку рабочей нагрузки, которая была захвачена, с помощью команды ДЕА в файл ИРФ:

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  Запустите запись трассировки на целевом компьютере, на котором работает SQL Server с помощью Стартреплайкаптуретраце. SQL.
       
    а.  В SQL Server Management Studio (SSMS) откройте < Dea_InstallPath\>\Скриптс\стартреплайкаптуретраце.скл.
    
    б.  Запустите `Set @durationInMins=0`, чтобы запись трассировки не была автоматически прервана через указанное время.
    
    в.  Чтобы задать максимальный размер для каждого файла трассировки, выполните `Set @maxfilesize`. Рекомендуемый размер — 200 (в МБ).
    
    г.  Измените `@Tracefile`, чтобы задать уникальное имя для файла трассировки.
    
    Д.  Измените `@dbname`, чтобы указать имя базы данных, если Рабочая нагрузка должна быть захвачена только в определенной базе данных. По умолчанию записывается Рабочая нагрузка на весь сервер. 
4.  Воспроизводить файл ИРФ на целевом экземпляре SQL Server:

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    а.  Чтобы отслеживать состояние, откройте окно командной строки и запустите `DReplay status -f 1`.
        
    б.  Чтобы прерывать воспроизведение, например, если вы видите, что уровень% ниже ожидаемого, откройте окно командной строки и запустите `DReplay cancel`.

5.  Останавливает запись трассировки на целевом экземпляре SQL Server.
6.  В SSMS откройте `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7.  Измените `@Tracefile` в соответствии с путем к файлу трассировки на целевом компьютере, на котором работает SQL Server.
8.  Запустите сценарий на целевом компьютере с SQL Server.

## <a name="analyze-traces-by-using-the-dea-command"></a>Анализ трассировок с помощью команды ДЕА

Чтобы запустить новый анализ трассировки, выполните следующую команду:

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Пример**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>Следующие шаги

Чтобы получить 19-минутное введение в ДЕА и демонстрацию, просмотрите следующее видео:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
