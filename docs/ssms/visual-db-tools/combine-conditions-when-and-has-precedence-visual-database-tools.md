---
title: Объединение условий, если приоритет имеет оператор AND (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 6638b29eb285fc2701a3b09c78bfca85ae2a8f69
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67686266"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a>Объединение условий, если приоритет имеет оператор AND (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Для объединения условий с оператором AND столбец добавляется к запросу дважды для каждого из условий. Для объединения условий с оператором OR первое условие необходимо вставить в столбец "Фильтр", а дополнительные условия — в столбец **Или...**  
  
Предположим, что нужно найти или служащих, проработавших в компании более пяти лет на низкооплачиваемых должностях, или служащих на должностях среднего уровня, независимо от их стажа работы. Этому запросу требуется три условия, два из которых связаны с оператором AND:  
  
-   Служащие со стажем более пяти лет и (AND) уровнем должности 100.  
  
    -или-  
  
-   Служащие с уровнем должности 200.  
  
### <a name="to-combine-conditions-when-and-has-precedence"></a>Сочетание условий, если оператор AND имеет больший приоритет  
  
1.  На [панель критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)добавьте столбцы данных для поиска. Если необходимо выполнить поиск в одном столбце по двум и более условиям, связанным оператором AND, в сетку необходимо добавить имя столбца данных столько раз, сколько имеется искомых значений.  
  
2.  В столбце **Фильтр** введите все условия, которые нужно связать оператором AND. Например, чтобы связать условия поиска в столбцах `hire_date` и `job_lvl` оператором AND, введите в столбец «Фильтр» значения `< '1/1/91'` и `= 100`, соответственно.  
  
    На основании этих строк сетки в инструкции на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)будет сформировано следующее предложение WHERE:  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  В столбце сетки **Или...** введите условия, которые нужно связать оператором OR. Например, чтобы добавить условие, выполняющее поиск другого значения в столбце `job_lvl` , введите дополнительное значение в столбец **Или...** , например `= 200`.  
  
    Ввод еще одного значения в столбце **Или...** добавляет к предложению WHERE в инструкции на панели "SQL" еще одно условие:  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a>См. также:  
[Соединение условий, если приоритет имеет оператор OR (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/combine-conditions-when-or-has-precedence-visual-database-tools.md)  
[Обозначения для условий комбинированного поиска на панели критериев (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
[Правила ввода значений для поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
