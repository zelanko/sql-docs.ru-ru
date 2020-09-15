---
description: Суммирование значения или выполнение статистической обработки с помощью пользовательских выражений (визуальные инструменты для баз данных)
title: Суммирование или статистическая обработка значений с помощью пользовательских выражений
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: e71f0ffc06314678becda493f6e45c98060d3a32
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88312550"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a>Суммирование значения или выполнение статистической обработки с помощью пользовательских выражений (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
В дополнение к обработке данных с помощью агрегатных функций можно формировать статистические значения с помощью пользовательских выражений. Эти выражения можно свободно использовать в статистических запросах вместо агрегатных функций.  
  
Например, попробуйте создать в таблице `titles` запрос, отображающий не просто среднюю цену, а среднюю цену при наличии скидки.  
  
В запрос нельзя включать выражения, основанные на вычислении отдельных строк таблицы. Следует создавать выражения на основе статистических значений, поскольку при вычислении выражений доступны только такие значения.  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a>Пользовательское выражение для сводного значения  
  
1.  Укажите группы для запроса. Дополнительные сведения см. в разделе [Группирование строк в результатах запроса (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/group-rows-in-query-results-visual-database-tools.md).  
  
2.  Перейдите к пустой строке на панели критериев и введите выражение в столбце **Столбцы**.  
  
    Чтобы создать полезный заголовок столбца в выходных данных запроса, [конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) автоматически присваивает выражению псевдоним столбца. Дополнительные сведения см. в разделе [Создание псевдонимов столбцов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md).  
  
3.  В столбце **Группировать** выберите **Выражение**.  
  
4.  Выполнение запроса.  
  
## <a name="see-also"></a>См. также:  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
  
