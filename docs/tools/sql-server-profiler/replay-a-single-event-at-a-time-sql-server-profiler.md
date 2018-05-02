---
title: Воспроизведение одного события за раз (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5adf34336a36eb64368c0a70a58813d886b9c3e3
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a>воспроизвести одиночное событие за раз (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается, как с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]воспроизвести одно событие за раз в файл трассировки воспроизведения или таблицу.  
  
### <a name="to-replay-a-single-event-at-a-time"></a>Вспроизведение одиночное события за раз  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  В меню **Воспроизведение** выберите **Шаг**и подключитесь к экземпляру сервера, на котором предстоит воспроизвести трассировку.  
  
3.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**. Дополнительные сведения о задании параметров в диалоговом окне **Конфигурация воспроизведения** см. в разделе [Воспроизведение файла трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) или [Воспроизведение таблицы трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md).  
  
4.  Чтобы воспроизвести первое событие, нажмите кнопку **OK** в диалоговом окне **Конфигурация воспроизведения** .  
  
5.  Чтобы воспроизвести следующие события, в меню **Воспроизведение** выберите **Шаг**или нажмите клавишу F10. Повторно нажимайте **Шаг** или клавишу F10 для каждого события.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
