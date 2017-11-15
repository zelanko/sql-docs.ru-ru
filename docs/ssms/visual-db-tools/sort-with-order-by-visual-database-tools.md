---
title: "Сортировка с помощью предложения ORDER BY (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 071a989f1703eff5f89a3695c3575b01d9b47132
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sort-with-order-by-visual-database-tools"></a>Произведение сортировки с помощью предложения ORDER BY (визуальные инструменты для баз данных)
Предложение ORDER BY позволяет сортировать результаты запроса по одному или нескольким столбцам. Его можно определить, выбрав параметры на панели «Подробности критериев».  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>Для сортировки результатов запроса с помощью предложения ORDER BY:  
  
1.  Откройте запрос или создайте новый.  
  
2.  На [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)щелкните в столбце **Тип сортировки** строку, соответствующую столбцу, по которому нужно отсортировать результаты запроса.  
  
3.  В раскрывающемся списке выберите *По возрастанию* или *По убыванию* .  
  
> [!NOTE]  
> Очистка элемента **Тип сортировки** для столбца удаляет этот столбец из предложения ORDER BY.  
  
Обратите внимание, что во время работы с панелью критериев предложение UNION запроса изменяется в соответствии с последними действиями.  
  
> [!NOTE]  
> При сортировке результатов по нескольким столбцам в столбце **Порядок сортировки** укажите порядок, в котором будут просматриваться столбцы при сортировке. Дополнительные сведения см. в разделе **Как производить сортировку нескольких столбцов в запросе**.  
  
## <a name="see-also"></a>См. также:  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
