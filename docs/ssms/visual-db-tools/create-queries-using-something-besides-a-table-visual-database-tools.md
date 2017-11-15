---
title: "Создание запросов, использующих не только таблицу | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-defined functions [SQL Server], queries
- queries [SQL Server], creating
ms.assetid: 8e4a1f0a-8a42-4733-be8d-e21d6dbddb33
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca9ab6532c1a83be15b1b9a80c0e96ef051fac27
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="create-queries-using-something-besides-a-table-visual-database-tools"></a>Создание запросов, использующих не только таблицу (визуальные инструменты для баз данных)
При написании запроса разработчик указывает, какие требуются столбцы, как отбираются строки и откуда обработчик запросов получает исходные данные. Обычно исходные данные поступают из таблицы или нескольких таблиц, участвующих в соединении. Однако исходные данные могут поступать не только из таблиц. Источниками данных могут служить представления, запросы, синонимы или определяемые пользователем функции, которые возвращают таблицу.  
  
## <a name="using-a-view-in-place-of-a-table"></a>Использование представления вместо таблицы  
Допускается выбор строк из представления. Например, предположим, что база данных содержит представление с именем «ExpensiveBooks», строки в котором описывают книги с ценой, превышающей 19,99. Определение представления может выглядеть следующим образом:  
  
```  
SELECT *  
FROM titles  
WHERE price > 19.99  
```  
  
Можно отобрать дорогие книги по психологии, выбирая их из представления ExpensiveBooks. Конечный код SQL может выглядеть следующим образом:  
  
```  
SELECT *  
FROM ExpensiveBooks  
WHERE type = 'psychology'  
```  
  
Допускается включение представления в операцию JOIN. Например, можно получить данные по продажам дорогих книг, соединив таблицу продаж с представлением ExpensiveBooks. Конечный код SQL может выглядеть следующим образом:  
  
```  
SELECT *  
FROM sales   
         INNER JOIN   
         ExpensiveBooks   
         ON sales.title_id   
         =  ExpensiveBooks.title_id  
```  
  
Дополнительные сведения о добавлении представления в запрос см. в разделе [Добавление таблиц в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md).  
  
## <a name="using-a-query-in-place-of-a-table"></a>Использование запроса вместо таблицы  
Допускается выбор строк из запроса. Предположим, что имеется запрос, возвращающий названия и идентификаторы для книг, написанных соавторами, т.е. имеющих более одного автора. Код SQL может выглядеть следующим образом:  
  
```  
SELECT   
     titles.title_id, title, type  
FROM   
     titleauthor   
         INNER JOIN  
         titles   
         ON titleauthor.title_id   
         =  titles.title_id   
GROUP BY   
     titles.title_id, title, type  
HAVING COUNT(*) > 1  
```  
  
После этого можно написать другой запрос, использующий этот результат. Например, запрос, возвращающий книги по психологии, написанные соавторами, будет использовать существующий запрос как источник данных. Конечный код SQL может выглядеть следующим образом:  
  
```  
SELECT   
    title  
FROM   
    (  
    SELECT   
        titles.title_id,   
        title,   
        type  
    FROM   
        titleauthor   
            INNER JOIN  
            titles   
            ON titleauthor.title_id   
            =  titles.title_id   
    GROUP BY   
        titles.title_id,   
        title,   
        type  
    HAVING COUNT(*) > 1  
    )   
    co_authored_books  
WHERE     type = 'psychology'  
```  
  
Полужирным шрифтом выделен существующий запрос, используемый как источник данных нового запроса. Следует отметить, что в новом запросе для существующего запроса используется псевдоним (co_authored_books). Дополнительные сведения о псевдонимах см. в разделах [Создание псевдонимов таблицы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md) и [Создание псевдонимов столбцов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md).  
  
Допускается включение запроса в операцию JOIN. Например, можно получить данные по продажам дорогих книг, написанных соавторами, соединив представление ExpensiveBooks с существующим запросом. Конечный код SQL может выглядеть следующим образом:  
  
```  
SELECT   
    ExpensiveBooks.title  
FROM   
    ExpensiveBooks   
        INNER JOIN  
        (  
        SELECT   
            titles.title_id,   
            title,   
            type  
        FROM   
            titleauthor   
                INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
        GROUP BY   
            titles.title_id,   
            title,   
            type  
        HAVING COUNT(*) > 1  
        )  
```  
  
Дополнительные сведения о добавлении запроса в запрос см. в разделе [Добавление таблиц в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md).  
  
## <a name="using-a-user-defined-function-in-place-of-a-table"></a>Использование определяемых пользователем функций вместо таблицы  
В SQL Server 2000 или более поздних версиях поддерживается создание определяемой пользователем функции, возвращающей таблицу. Такие функции полезны при использовании сложной или процедурной логики.  
  
Предположим, что таблица сотрудников содержит дополнительный столбец employee.manager_emp_id и что существует внешний ключ от столбца manager_emp_id к столбцу employee.emp_id. В каждой строке таблицы сотрудников столбец manager_emp_id указывает начальника конкретного сотрудника. Точнее, указывается код emp_id начальника конкретного сотрудника. Можно создать определяемую пользователем функцию, которая возвращает таблицу, содержащую одну строку для каждого сотрудника, работающего в иерархии подчиненности для руководителя высшего уровня. Функцию можно назвать fn_GetWholeTeam и определить так, чтобы входной переменной был идентификатор руководителя, сведения о подчиненных которого требуется получить.  
  
Затем можно написать запрос, использующий функцию fn_GetWholeTeam как источник данных. Конечный код SQL может выглядеть следующим образом:  
  
```  
SELECT *   
FROM   
     fn_GetWholeTeam ('VPA30890F')  
```  
  
«VPA30890F» представляет код emp_id руководителя, сведения о подчиненных которого требуется получить. Дополнительные сведения о добавлении пользовательской функции в запрос см. в разделе [Добавление таблиц в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md). Подробное описание определяемых пользователем функций см. в разделе [Определяемые пользователем функции](http://msdn.microsoft.com/en-us/d7ddafab-f5a6-44b0-81d5-ba96425aada4).  
  
