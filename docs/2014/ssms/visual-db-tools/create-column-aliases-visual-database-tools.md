---
title: Создание псевдонимов столбцов (визуальные инструменты для баз данных) | Документация Майкрософт
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
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1c317fd581c97d8c48a5ccd92a0010c45be24493
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098322"
---
# <a name="create-column-aliases-visual-database-tools"></a>Создание псевдонимов столбцов (визуальные инструменты для баз данных)
  Для имен столбцов можно создать псевдонимы, чтобы облегчить работу с ними, подсчеты и суммирования значений. Например, можно создать псевдоним столбца для:  
  
-   создания именованного столбца, например «Общий итог», для выражения типа `(quantity * unit_price)` или агрегатной функции.  
  
-   создания сокращенной формы имени столбца, например `"d_id"` для `"discounts.stor_id."`  
  
 После того, как псевдоним столбца определен, можно использовать его в запросе, чтобы указать данные, выбираемые запросом.  
  
### <a name="to-create-a-column-alias"></a>Создание псевдонима столбца  
  
1.  На **панели критериев**укажите строку, содержащую столбец данных, для которого нужно создать псевдоним и, если необходимо, пометьте ее как выходные данные. Если столбца данных нет в сетке, добавьте его.  
  
2.  В столбце **Псевдоним** для этой строки введите псевдоним. Этот псевдоним должен соответствовать всем соглашениям об именах для SQL. Если введенное имя псевдонима содержит пробелы, конструктор запросов и представлений автоматически ставит вокруг них разделители.  
  
## <a name="see-also"></a>См. также  
 [Добавление столбцов в запросы &#40;визуальные средства базы данных&#41;](visual-database-tools.md)   
 [Сортировать и группировать результаты запроса &#40;визуальные средства базы данных&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Резюмирование результатов запросов &#40;визуальные средства базы данных&#41;](summarize-query-results-visual-database-tools.md)   
 [Выполнение основных операций с запросами (визуальные инструменты для баз данных)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  