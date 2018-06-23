---
title: Получение суммарных или статистических значений с помощью выражений (визуальные инструменты баз данных) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7d1619f794ee3bdec67ec24a46dec81645b6b6fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192351"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a>Суммирование значения или выполнение статистической обработки с помощью пользовательских выражений (визуальные инструменты для баз данных)
  В дополнение к обработке данных с помощью агрегатных функций можно формировать статистические значения с помощью пользовательских выражений. Эти выражения можно свободно использовать в статистических запросах вместо агрегатных функций.  
  
 Например, попробуйте создать в таблице `titles` запрос, отображающий не просто среднюю цену, а среднюю цену при наличии скидки.  
  
 В запрос нельзя включать выражения, основанные на вычислении отдельных строк таблицы. Следует создавать выражения на основе статистических значений, поскольку при вычислении выражений доступны только такие значения.  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a>Пользовательское выражение для сводного значения  
  
1.  Укажите группы для запроса. Дополнительные сведения см. в разделе [Группирование строк в результатах запроса (визуальные инструменты для баз данных)](visual-database-tools.md).  
  
2.  Перейдите к пустой строке на панели критериев и введите выражение в столбце **Столбцы**.  
  
     Чтобы создать полезный заголовок столбца в выходных данных запроса, [конструктор запросов и представлений](query-and-view-designer-tools-visual-database-tools.md) автоматически присваивает выражению псевдоним столбца. Дополнительные сведения см. в разделе [Создание псевдонимов столбцов (визуальные инструменты для баз данных)](create-column-aliases-visual-database-tools.md).  
  
3.  В столбце **Группировать** выберите **Выражение**.  
  
4.  Выполните запрос.  
  
## <a name="see-also"></a>См. также  
 [Сортировать и группировать результаты запроса &#40;визуальные средства базы данных&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Резюмирование результатов запросов (визуальные инструменты для баз данных)](summarize-query-results-visual-database-tools.md)  
  
  