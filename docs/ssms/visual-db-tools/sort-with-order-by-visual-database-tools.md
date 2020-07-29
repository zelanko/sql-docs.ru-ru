---
title: Сортировка с помощью предложения ORDER BY
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 840ceec41624cf11604d4db2b2eb90f9b4c03c53
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999311"
---
# <a name="sort-with-order-by-visual-database-tools"></a>Произведение сортировки с помощью предложения ORDER BY (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
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
  
