---
title: Определение критериев поиска (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Query Designer [SQL Server], Criteria pane
- queries [Visual Database Tools]
- criteria for search conditions
- search conditions [SQL Server], search criteria
- View Designer, Criteria pane
- row return limitations [SQL Server]
- Criteria pane
- restricting rows returned
- search criteria [SQL Server]
- Visual Database Tools [SQL Server], queries
- limiting rows returned
ms.assetid: 25fb4e31-6dbf-4cf6-8e47-0dd0998c836c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f41f7f80bc0fae960794aa5bf28265e1086c578
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="specify-search-criteria-visual-database-tools"></a>Определение критериев поиска (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Чтобы ограничить количество возвращаемых по запросу строк, можно использовать критерии поиска.  
  
Дополнительные сведения о создании критерия поиска приведены в подразделах, перечисленных в следующей таблице.  
  
## <a name="in-this-section"></a>в этом разделе  
[Правила ввода значений для поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
Разъясняется, как вводить текст, числа, даты и логические значения.  
  
[Обозначения для условий комбинированного поиска на панели критериев (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
Объясняются принципы использования операторов AND и OR.  
  
[Указание условий поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-conditions-visual-database-tools.md)  
Объясняются принципы выбора критерия поиска, обеспечивающего извлечение только необходимых данных.  
  
[Указание нескольких условий поиска для одного столбца (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-multiple-search-conditions-for-one-column-visual-database-tools.md)  
Объясняется, как создавать несколько условий поиска для одного столбца данных.  
  
[Указание нескольких условий поиска для нескольких столбцов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
Объясняется, как включать несколько столбцов данных в условие поиска для запроса.  
  
[Указание предложения TOP в запросах (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-the-top-clause-in-queries-visual-database-tools.md)  
Объясняется, как задать количество или процентное соотношение возвращаемых строк.  
  
[Использование предложения HAVING и WHERE в одном запросе (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/use-having-and-where-clauses-in-the-same-query-visual-database-tools.md)  
Объясняется, как и для чего используются оба представленных предложения в запросе.  
  
[Выбор строк, не соответствующих заданному значению (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/select-rows-that-do-not-match-a-value-visual-database-tools.md)  
Объясняется, как настроить подачу выходной информации таким образом, чтобы в ней не содержалось строк, в которых имеется значение, заданное в инструкции запроса.  
  
[Включение или исключение строк (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/include-or-exclude-rows-visual-database-tools.md)  
Объясняются принципы использования предложений и операторов в запросах.  
  
[Исключение повторяющихся строк (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/exclude-duplicate-rows-visual-database-tools.md)  
Объясняется, как исключить из запросов SELECT повторяющиеся строки.  
  
[Объединение условий, если приоритет имеет оператор AND (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/combine-conditions-when-and-has-precedence-visual-database-tools.md)  
Объясняется, как и для чего используется оператор AND при фильтрации результатов запроса.  
  
[Соединение условий, если приоритет имеет оператор OR (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/combine-conditions-when-or-has-precedence-visual-database-tools.md)  
Объясняется, как и для чего используется оператор OR при фильтрации результатов запроса.  
  
[Создание вложенных запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-subqueries-visual-database-tools.md)  
Объясняется, как создавать вложенные запросы или запросы более низкого уровня.  
  
## <a name="related-sections"></a>См. также  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
Содержит ссылки на подразделы, в которых приводятся пошаговые инструкции по выполнению самых общих задач с запросами.  
  
[Типы запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
Содержит ссылки на подразделы, в которых перечисляются поддерживаемые типы запросов.  
  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
Содержит ссылки на подразделы, в которых приводятся пошаговые инструкции по выполнению сортировки и группировки результатов запроса.  
  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
Содержит ссылки на подразделы, в которых приводятся пошаговые инструкции по выполнению анализа результатов запроса, включая столбцы с пустыми и нечисловыми значениями.  
  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
Содержит ссылки на подразделы, в которых описываются возможные действия над запросами и представлениями при использовании соответствующих конструкторов.  
  
