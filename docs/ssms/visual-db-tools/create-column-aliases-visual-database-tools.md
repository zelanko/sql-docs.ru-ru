---
title: "Создание псевдонимов столбцов (визуальные инструменты для баз данных) | Документация Майкрософт"
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
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bbbf69c55fcd0225583c43b3b4ae4089cc2f40ea
ms.contentlocale: ru-ru
ms.lasthandoff: 08/18/2017

---
# <a name="create-column-aliases-visual-database-tools"></a>Создание псевдонимов столбцов (визуальные инструменты для баз данных)
Для имен столбцов можно создать псевдонимы, чтобы облегчить работу с ними, подсчеты и суммирования значений. Например, можно создать псевдоним столбца для:  
  
-   создания именованного столбца, например «Общий итог», для выражения типа `(quantity * unit_price)` или агрегатной функции.  
  
-   создания сокращенной формы имени столбца, например `"d_id"` для `"discounts.stor_id."`  
  
После того, как псевдоним столбца определен, можно использовать его в запросе, чтобы указать данные, выбираемые запросом.  
  
### <a name="to-create-a-column-alias"></a>Создание псевдонима столбца  
  
1.  На **панели критериев**укажите строку, содержащую столбец данных, для которого нужно создать псевдоним и, если необходимо, пометьте ее как выходные данные. Если столбца данных нет в сетке, добавьте его.  
  
2.  В столбце **Псевдоним** для этой строки введите псевдоним. Этот псевдоним должен соответствовать всем соглашениям об именах для SQL. Если введенное имя псевдонима содержит пробелы, конструктор запросов и представлений автоматически ставит вокруг них разделители.  
  
## <a name="see-also"></a>См. также:  
[Добавление столбцов в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

