---
title: "Категория событий Performance | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "классы событий SQL Server, категория событий Performance"
  - "Performance, категория событий [SQL Server]"
  - "классы событий [SQL Server], категория событий Performance"
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
caps.latest.revision: 32
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 32
---
# Категория событий Performance
  Категория событий **Performance** используется для контроля классов событий **Showplan** и классов событий, формируемых при выполнении операторов SQL языка DML.  
  
## В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Класс событий Auto Stats](../../relational-databases/event-classes/auto-stats-event-class.md)|Указывает, что произошло автоматическое обновление статистики индекса и столбца.|  
|[Класс событий Degree of Parallelism (используется с версией 7.0)](../../relational-databases/event-classes/degree-of-parallelism-7-0-insert-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкции SELECT, INSERT, UPDATE или DELETE были выполнены с использованием последовательного или параллельного плана. В отчет также включается количество ЦП, использованных для выполнения операции.|  
|[Класс событий Performance Statistics](../../relational-databases/event-classes/performance-statistics-event-class.md)|Наблюдает за производительностью выполняемых запросов.|  
|[Класс событий Showplan All](../../relational-databases/event-classes/showplan-all-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL.|  
|[Класс событий Showplan All for Query Compile](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** .|  
|[Класс событий Showplan Statistics Profile](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md)|Отображает предполагаемую стоимость запроса.|  
|[Класс событий Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md)|Идентифицирует операторы **Showplan** в инструкции SQL. Класс событий хранит описание каждого события как правильный XML-документ.|  
|[Класс событий Showplan XML for Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)|Отображает данные компиляции для операторов **Showplan** в формате XML.|  
|[Класс событий Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)|Идентифицирует операторы **Showplan** , связанные с инструкцией SQL. Выходом является XML-документ.|  
|[Класс событий SQL:FullTextQuery](../../relational-databases/event-classes/sql-fulltextquery-event-class.md)|Указывает на то, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершил выполнение полнотекстового запроса.|  
|[Класс событий Plan Guide Successful](../../relational-databases/event-classes/plan-guide-successful-event-class.md)|Указывает, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] успешно создан план выполнения для запроса или пакета, в котором содержится структура плана.|  
|[Класс событий Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md)|Указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось создать план выполнения для запроса или пакета, в котором содержится структура плана.|  
  
## См. также:  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  