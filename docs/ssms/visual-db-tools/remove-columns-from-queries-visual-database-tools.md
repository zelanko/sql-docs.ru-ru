---
title: Удаление столбцов из запросов (визуальные инструменты для базы данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing columns
- queries [SQL Server], columns
- deleting columns
- dropping columns
ms.assetid: 6d9819b8-ee2f-4838-9713-c5e3ad37ab46
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9a59362473ad977da4a29ab03bdd158da7825425
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098140"
---
# <a name="remove-columns-from-queries-visual-database-tools"></a>Удаление столбцов из запросов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Если столбец больше не нужен в запросе, то его можно удалить. При удалении столбца конструктор запросов и представлений удалит ссылки на него в списке выборки, установку сортировки, критерии поиска, **панель SQL**и все спецификации группирования.  
  
> [!NOTE]  
> Если столбец нужно удалить только из выходных данных запроса Select, то это можно сделать без удаления столбца из запроса. Дополнительные сведения см. в разделе [Удаление столбцов из результатов запроса (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/remove-columns-from-query-results-visual-database-tools.md).  
  
### <a name="to-remove-a-column-from-the-query"></a>Удаление столбца из запроса  
  
-   На **панели критериев**выберите строку сетки, содержащую нужный столбец, затем нажмите клавишу DELETE.  
  
    -или-  
  
-   Удалите все ссылки на столбец в [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Добавление столбцов в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
