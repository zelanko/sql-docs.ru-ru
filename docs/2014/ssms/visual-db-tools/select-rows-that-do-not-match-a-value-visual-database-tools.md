---
title: Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f84f4fcc8a6dde7dcf9f556a72c2599356e231f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067540"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных)
  Чтобы найти строки, которые не соответствуют значению, используется оператор NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Поиск строк, не соответствующих значению  
  
1.  Если вы еще не сделали этого, добавьте столбцы или выражения, которые будут использоваться в условии поиска, на [панель критериев](visual-database-tools.md).  
  
2.  Найдите строку, содержащую столбец данных или выражение поиска, и в столбце сетки **Фильтр** введите оператор NOT и затем значение поиска.  
  
 Например, чтобы найти строки в таблице `products` , в которой значения в столбце кода продукта начинаются с символа, отличного от «A», можно ввести такое условие поиска:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>См. также:  
 [Правила ввода значений поиска &#40;визуальных инструментов для баз данных&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Определение критериев поиска (визуальные инструменты для баз данных)](specify-search-criteria-visual-database-tools.md)  
  
  
