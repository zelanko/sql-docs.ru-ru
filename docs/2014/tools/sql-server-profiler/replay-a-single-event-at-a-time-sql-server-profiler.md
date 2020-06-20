---
title: Воспроизведение одного события за раз (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 457bc94d9d8eae470fb60b450d30441c07e676df
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85040231"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a>воспроизвести одиночное событие за раз (приложение SQL Server Profiler)
  В данном разделе описывается, как с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]воспроизвести одно событие за раз в файл трассировки воспроизведения или таблицу.  
  
### <a name="to-replay-a-single-event-at-a-time"></a>Вспроизведение одиночное события за раз  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в разделе [Replay Requirements](replay-requirements.md).  
  
2.  В меню **Воспроизведение** выберите **Шаг**и подключитесь к экземпляру сервера, на котором предстоит воспроизвести трассировку.  
  
3.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**. Дополнительные сведения о задании параметров в диалоговом окне **Конфигурация воспроизведения** см. в разделе [Воспроизведение файла трассировки (SQL Server Profiler)](replay-a-trace-file-sql-server-profiler.md) или [Воспроизведение таблицы трассировки (SQL Server Profiler)](replay-a-trace-table-sql-server-profiler.md).  
  
4.  Чтобы воспроизвести первое событие, нажмите кнопку **OK** в диалоговом окне **Конфигурация воспроизведения** .  
  
5.  Чтобы воспроизвести следующие события, в меню **Воспроизведение** выберите **Шаг**или нажмите клавишу F10. Повторно нажимайте **Шаг** или клавишу F10 для каждого события.  
  
## <a name="see-also"></a>См. также:  
 [Воспроизведение трассировок](replay-traces.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
