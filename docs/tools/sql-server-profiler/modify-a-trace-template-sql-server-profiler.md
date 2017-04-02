---
title: "редактировать шаблон трассировки (приложение SQL Server Profiler) | Microsoft Docs"
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
  - "шаблоны [SQL Server], трассировки"
  - "шаблоны трассировки [SQL Server]"
  - "изменение трассировок"
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# редактировать шаблон трассировки (приложение SQL Server Profiler)
  В этом подразделе описывается модификация шаблона трассировки с помощью [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Изменение шаблона трассировки  
  
1.  В меню **Файл** выберите **Шаблоны**и затем выберите **Изменить шаблон**.  
  
2.  В диалоговом окне **Свойства шаблона трассировки** на вкладке **Общие** можно изменить тип сервера и имя шаблона или выбрать использование шаблона по умолчанию для типа сервера.  
  
3.  В меню **Выбор событий** используйте сетку для добавления или удаления событий и столбцов данных в файле трассировки следующим образом:  
  
    -   Чтобы добавить событие, разверните соответствующую категорию событий в столбце **События** и выберите имя события.  
  
    -   При добавлении события все относящиеся к нему столбцы данных включаются автоматически. Чтобы удалить столбец данных для события из трассировки, снимите флажок в столбце данных для этого события.  
  
    -   Чтобы добавить фильтры, щелкните имя столбца данных и определите критерии фильтра в диалоговом окне **Изменение фильтра** . Также можно щелкнуть имя столбца данных правой кнопкой мыши и выбрать пункт **Изменить фильтр столбца**, чтобы открыть диалоговое окно **Изменение фильтра**. Нажмите кнопку **ОК** , чтобы добавить фильтр.  
  
4.  Нажмите кнопку **Сохранить**или кнопку **Сохранить As**для сохранения шаблона трассировки под другим именем.  
  
## См. также:  
 [Указание столбцов событий и данных для файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Извлечь шаблон из выполняемой трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Извлечь шаблон из файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  