---
title: "Поддерживаемые типы запросов (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ed5c567b380c476f571b4ba96d834d482ecd9c3c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="supported-query-types-visual-database-tools"></a>Поддерживаемые типы запросов (визуальные инструменты для баз данных)
На панелях диаграммы и критериев (графические области) [конструктора запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) можно создать запросы следующих типов:  
  
-   **Запрос SELECT** . Получает данные из одной или нескольких таблиц или представлений. Запрос этого типа создает инструкцию SQL SELECT.  
  
-   **Вставить результаты** . Создает новые строки копированием существующих строк из одной таблицы в другую или в ту же самую таблицу в качестве новых строк. Запрос этого типа создает инструкцию SQL INSERT INTO...SELECT.  
  
-   **Вставить значения** . Создает новую строку и вставляет значения в заданные столбцы. Запрос этого типа создает инструкцию SQL INSERT INTO...VALUES.  
  
-   **Запрос на обновление** . Изменяет значения отдельных столбцов в одной или нескольких существующих строках таблицы. Запрос этого типа создает инструкцию SQL UPDATE...SET.  
  
-   **Запрос на удаление** . Удаляет одну или несколько строк из таблицы. Запрос этого типа создает инструкцию SQL DELETE.  
  
    > [!NOTE]  
    > Запрос «Удаление» удаляет строки из таблицы целиком. Если необходимо удалить значения из отдельных столбцов данных, используйте запрос «Обновление».  
  
-   **Запрос на создание таблицы** . Создает новую таблицу и строки в этой таблице, копируя в нее результаты запроса. Запрос этого типа создает инструкцию SQL SELECT...INTO.  
  
В дополнение к этим запросам, создаваемым при помощи графических панелей, на панель SQL можно ввести любую инструкцию SQL, например запросы объединения.  
  
При создании запросов при помощи инструкций SQL, которые не могут быть представлены на графических панелях, конструктор запросов и представлений затемняет эти панели, указывая тем самым, что они не отражают создаваемый вами запрос. Однако затемненные панели остаются активными, и во многих случаях на этих панелях можно производить изменения запросов. Если выполняемые изменения приводят к запросу, который может быть представлен на графических панелях, эти панели перестают затемняться.  
  
## <a name="see-also"></a>См. также:  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Типы запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
  

