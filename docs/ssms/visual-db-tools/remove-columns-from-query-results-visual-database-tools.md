---
title: Удаление столбцов из результатов запроса (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e403f86116522f582253ad6c75556db09b0e270e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774922"
---
# <a name="remove-columns-from-query-results-visual-database-tools"></a>Удаление столбцов из результатов запроса (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
