---
title: "Определение нескольких условий поиска для нескольких столбцов | Документация Майкрософт"
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
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 041d9a3c2a204d8413d755ec69946859195b5c0a
ms.lasthandoff: 04/11/2017

---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a>Указание нескольких условий поиска для нескольких столбцов (визуальные инструменты для баз данных)
Можно расширить или сузить область видимости, включив несколько столбцов данных в качестве части условия поиска. Например, может понадобиться:  
  
-   Выполнить поиск сотрудников, которые либо проработали в компании более пяти лет, либо занимают определенные должности.  
  
-   Выполнить поиск книги, которая опубликована указанным издательством и имеет отношение к кулинарии.  
  
Чтобы создать запрос, осуществляющий поиск значений в каком-либо из двух (или более) столбцов, необходимо указать условие OR. Чтобы создать запрос, который должен отвечать условиям в двух (или более) столбцах, необходимо указать условие AND.  
  
## <a name="specifying-an-or-condition"></a>Указание условия OR  
Чтобы создать несколько условий, связанных оператором OR, необходимо поместить каждое отдельное условие в отдельный столбец на панели критериев.  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a>Указание условия OR для двух различных столбцов  
  
1.  В [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)добавьте столбцы для поиска.  
  
2.  В столбце **Фильтр** для первого столбца, подлежащего поиску, укажите первое условие.  
  
3.  В столбце **Или...** для второго столбца данных, подлежащего поиску, укажите второе условие, оставив столбец **Фильтр** пустым.  
  
    Конструктор запросов и представлений создает предложение WHERE, содержащее условие OR, подобное следующему:  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  Повторите шаги 2 и 3 для каждого дополнительного условия, которое нужно добавить. Используйте отдельный столбец **Или...** для каждого нового условия.  
  
## <a name="specifying-an-and-condition"></a>Указание условия AND  
Чтобы выполнить поиск разных столбцов данных с использованием условий, связанных оператором AND, необходимо поместить все условия в столбец **Фильтр** в сетке.  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a>Указание условия AND для двух различных столбцов  
  
1.  В [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)добавьте столбцы для поиска.  
  
2.  В столбце **Фильтр** для первого столбца данных, подлежащего поиску, укажите первое условие.  
  
3.  В столбце **Фильтр** для второго столбца данных укажите второе условие.  
  
    Конструктор запросов и представлений создает предложение WHERE, которое содержит предложение AND, подобное следующему:  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  Повторите шаги 2 и 3 для каждого дополнительного условия, которое нужно добавить.  
  
## <a name="see-also"></a>См. также:  
[Объединение условий, если приоритет имеет оператор AND (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/combine-conditions-when-and-has-precedence-visual-database-tools.md)  
[Соединение условий, если приоритет имеет оператор OR (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/combine-conditions-when-or-has-precedence-visual-database-tools.md)  
[Обозначения для условий комбинированного поиска на панели критериев (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  

