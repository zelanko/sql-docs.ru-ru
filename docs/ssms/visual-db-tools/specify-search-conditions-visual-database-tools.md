---
title: "Указание условий поиска (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 74105ddfa6aa23367231bedb9aa7b5dffb615687
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="specify-search-conditions-visual-database-tools"></a>Указание условий поиска (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Можно указать строки данных, которые появятся в результате запроса, задав условия поиска. Например, при выполнении запроса к таблице `employee` можно указать, что хотите найти только работников, которые работают в определенной области.  
  
Условия поиска указываются с помощью выражений. Наиболее часто используемое выражение состоит из оператора и искомого значения. Например, чтобы найти работников в определенной области продаж, можно указать следующий критерий поиска для столбца `region` :  
  
```  
='UK'  
```  
  
> [!NOTE]  
> При работе с несколькими таблицами конструктор запросов и представлений проверяет каждое условие поиска, чтобы определить, будет ли соединение результатом сравнения. Если да, то конструктор запросов и представлений автоматически преобразует условие поиска в соединение. Дополнительные сведения см. в статье [Автоматическое соединение таблиц (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md).  
  
### <a name="to-specify-search-conditions"></a>Указание условий поиска  
  
1.  Если это еще не сделано, нужно добавить на панели критериев столбцы или выражения, которые необходимо использовать в условиях поиска.  
  
    Если при создании запроса SELECT нежелательно, чтобы столбцы поиска или выражения появлялись в выходных данных запроса, очистите столбец **Выход** для каждого столбца или выражения, чтобы убрать их из числа выходных столбцов.  
  
2.  Найдите строку, содержащую столбец данных или выражение поиска, и в столбце **Фильтр** введите условие поиска.  
  
    > [!NOTE]  
    > Если не ввести ни одного оператора, конструктор запросов и представлений автоматически вставит оператор равенства «=».  
  
Конструктор запросов и представлений обновляет инструкцию SQL на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) , добавляя или изменяя предложение WHERE.  
  
## <a name="see-also"></a>См. также:  
[Правила ввода значений для поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
