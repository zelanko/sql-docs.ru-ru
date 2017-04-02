---
title: "воспроизвести одиночное событие за раз (приложение SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "события [SQL Server], воспроизведение одиночного события за раз"
  - "трассировки [SQL Server], воспроизведение"
  - "воспроизведение трассировок"
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# воспроизвести одиночное событие за раз (приложение SQL Server Profiler)
  В данном разделе описывается, как с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]воспроизвести одно событие за раз в файл трассировки воспроизведения или таблицу.  
  
### Вспроизведение одиночное события за раз  
  
1.  Откройте файл трассировки или таблицу трассировки, которые необходимо воспроизвести. Дополнительные сведения см. в разделах [Открытие файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или [Открытие таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Убедитесь, что открытый файл трассировки или открытая таблица содержат классы событий, которые необходимо воспроизвести. Дополнительные сведения см. в разделе [Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  В меню **Воспроизведение** выберите **Шаг**и подключитесь к экземпляру сервера, на котором предстоит воспроизвести трассировку.  
  
3.  В диалоговом окне **Конфигурация воспроизведения** проверьте настройки и нажмите кнопку **ОК**. Дополнительные сведения о задании параметров в диалоговом окне **Конфигурация воспроизведения** см. в разделе [Воспроизведение файла трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) или [Воспроизведение таблицы трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md).  
  
4.  Чтобы воспроизвести первое событие, нажмите кнопку **OK** в диалоговом окне **Конфигурация воспроизведения** .  
  
5.  Чтобы воспроизвести следующие события, в меню **Воспроизведение** выберите **Шаг**или нажмите клавишу F10. Повторно нажимайте **Шаг** или клавишу F10 для каждого события.  
  
## См. также:  
 [Воспроизведение трассировок](../../tools/sql-server-profiler/replay-traces.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  