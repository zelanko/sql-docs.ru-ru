---
description: Удаление столбцов из результатов запроса (визуальные инструменты для баз данных)
title: Удаление столбцов из результатов запроса
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- result sets [SQL Server], queries
- removing columns
- results [SQL Server], query
- deleting columns
- queries [SQL Server], results
ms.assetid: a7de7a87-4249-49bd-863d-dc0b40a49e78
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 04543311664ff4b4988cdf03486103721f821346
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491662"
---
# <a name="remove-columns-from-query-results-visual-database-tools"></a>Удаление столбцов из результатов запроса (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Если столбец используется в запросе SELECT, однако его отображение в результирующем наборе нежелательно (то есть если его не следует выводить в списке выборки), столбец можно убрать из вывода запроса. После удаления столбца из вывода запроса его все еще можно использовать в условиях поиска или как поле сортировки.  
  
> [!NOTE]  
> Чтобы получить сведения о полном удалении столбца из запроса, см. раздел [Удаление столбцов из запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/remove-columns-from-queries-visual-database-tools.md).  
  
### <a name="to-remove-a-column-from-the-query-output"></a>Удаление столбца из вывода запроса  
  
-   На **панели критериев**снимите флажок в столбце **Выход** для столбца данных, который необходимо удалить. (Если понадобится вернуть столбец в вывод запроса, можно снова установить флажок в столбце **Вывод** .)  
  
    -или-  
  
-   Удалите столбец из списка вывода на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Добавление столбцов в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[Удаление столбцов из запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/remove-columns-from-queries-visual-database-tools.md)  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
