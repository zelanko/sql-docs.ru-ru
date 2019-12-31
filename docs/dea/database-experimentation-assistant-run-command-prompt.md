---
title: Запуск Database Experimentation Assistant из командной строки
description: Запуск Database Experimentation Assistant из командной строки
ms.custom: seo-lt-2019
ms.date: 11/22/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: f5a0f7441dd17aec2587c772a678a3681fd3b423
ms.sourcegitcommit: 9e026cfd9f2300f106af929d88a9b43301f5edc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74317721"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>Запуск Database Experimentation Assistant из командной строки

В этой статье описывается, как записать трассировку в Database Experimentation Assistant (ДЕА), а затем анализировать результаты из командной строки.

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Запуск новой записи рабочей нагрузки с помощью команды ДЕА

Чтобы начать новую запись рабочей нагрузки, в командной строке выполните следующую команду:

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Например**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload-capture"></a>Воспроизведение записи рабочей нагрузки

1. Войдите на компьютер контроллера распределенное воспроизведение.
2. Чтобы преобразовать трассировку рабочей нагрузки, захваченную с помощью команды Деа, в файл ИРФ, в командной строке выполните следующую команду:

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3. Запустите запись трассировки на целевом компьютере, на котором работает SQL Server с помощью Стартреплайкаптуретраце. SQL.

    a.  В SQL Server Management Studio (SSMS) откройте <Dea_InstallPath\>\скриптс\стартреплайкаптуретраце.скл.

    b.  Запустите `Set @durationInMins=0` , чтобы запись трассировки не была автоматически прервана через указанное время.

    c.  Чтобы задать максимальный размер файла для каждого файла трассировки, выполните `Set @maxfilesize`команду. Рекомендуемый размер — 200 (в МБ).

    d.  Измените `@Tracefile` , чтобы задать уникальное имя для файла трассировки.

    д.  Измените `@dbname` , чтобы указать имя базы данных, если Рабочая нагрузка должна быть захвачена только в определенной базе данных. По умолчанию записывается Рабочая нагрузка на весь сервер.

4. Чтобы воспроизвести файл ИРФ на целевом экземпляре SQL Server, в командной строке выполните следующую команду:

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`

    a.  Чтобы отслеживать состояние, в командной строке выполните `DReplay status -f 1`команду.

    b.  Чтобы прерывать воспроизведение, например, если вы видите, что уровень прохождения% ниже ожидаемого, в командной строке выполните `DReplay cancel`команду.

5. Останавливает запись трассировки на целевом экземпляре SQL Server.
6. В среде SSMS откройте `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7. Измените `@Tracefile` в соответствии с путем к файлу трассировки на целевом компьютере, на котором работает SQL Server.
8. Запустите сценарий на целевом компьютере с SQL Server.

## <a name="analyze-traces-using-the-dea-command"></a>Анализ трассировок с помощью команды ДЕА

Чтобы запустить новый анализ трассировки, в командной строке выполните следующую команду:

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Например**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="see-also"></a>См. также:

- Дополнительные сведения об использовании ДЕА см. в разделе [обзор Database experimentation Assistant](database-experimentation-assistant-overview.md).
