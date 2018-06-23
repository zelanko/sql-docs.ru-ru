---
title: Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных) | Документация Майкрософт
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
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c0bfc7ef077a3e968ec418430a5b4213c4ef552b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094946"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных)
  Чтобы найти строки, которые не соответствуют значению, используется оператор NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Поиск строк, не соответствующих значению  
  
1.  Если это еще не сделано, нужно добавить на [панели критериев](visual-database-tools.md)столбцы или выражения, которые необходимо использовать в условиях поиска.  
  
2.  Найдите строку, содержащую столбец данных или выражение поиска, и в столбце сетки **Фильтр** введите оператор NOT и затем значение поиска.  
  
 Например, чтобы найти строки в таблице `products` , в которой значения в столбце кода продукта начинаются с символа, отличного от «A», можно ввести такое условие поиска:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>См. также  
 [Правила ввода для поиска значений &#40;визуальные средства базы данных&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Определение критериев поиска (визуальные инструменты для баз данных)](specify-search-criteria-visual-database-tools.md)  
  
  