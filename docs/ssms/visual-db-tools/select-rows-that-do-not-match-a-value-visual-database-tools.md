---
title: "Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37d9bf886947b98d5f14ec8d67e25c5c5c91e2e9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных)
Чтобы найти строки, которые не соответствуют значению, используется оператор NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Поиск строк, не соответствующих значению  
  
1.  Если это еще не сделано, нужно добавить на [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)столбцы или выражения, которые необходимо использовать в условиях поиска.  
  
2.  Найдите строку, содержащую столбец данных или выражение поиска, и в столбце сетки **Фильтр** введите оператор NOT и затем значение поиска.  
  
Например, чтобы найти строки в таблице `products` , в которой значения в столбце кода продукта начинаются с символа, отличного от «A», можно ввести такое условие поиска:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>См. также:  
[Правила ввода значений для поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
