---
title: "Создание самосоединения вручную (визуальные инструменты для баз данных) | Документация Майкрософт"
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
- self-joins
- manual joins [SQL Server]
- joins [SQL Server], self
ms.assetid: 910ed516-cb84-481b-95d0-cba3e89afdba
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a44398daffbf1ab25f52430d2b27a0e822427db1
ms.lasthandoff: 04/11/2017

---
# <a name="create-self-joins-manually-visual-database-tools"></a>Создание самосоединения вручную (визуальные инструменты для баз данных)
Самосоединение таблицы может быть создано даже в случае отсутствия рефлексивной связи таблица — база данных. Например, самосоединение может быть использовано для извлечения сведений о парах авторов, живущих в одном городе.  
  
Как и для любого другого соединения, для самосоединения требуется не менее двух таблиц. Различие состоит в том, что при самосоединении в роли второй таблицы выступает копия первой таблицы. Таким образом можно сравнивать столбцы двух экземпляров одной таблицы, что позволяет сравнивать значения элементов одного столбца друг с другом. [Конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) присваивает второму экземпляру таблицы псевдоним.  
  
Например, если создается самосоединение для получения всех пар авторов, живущих в г. Беркли, необходимо сравнить столбец `city` первого экземпляра таблицы со столбцом `city` второго экземпляра таблицы. Результирующий запрос может выглядеть так:  
  
```  
SELECT   
         authors.au_fname,   
         authors.au_lname,   
         authors1.au_fname AS Expr2,   
         authors1.au_lname AS Expr3  
      FROM   
         authors   
            INNER JOIN  
            authors authors1   
               ON authors.city   
                = authors1.city  
      WHERE  
         authors.city = 'Berkeley'  
```  
  
Для создания самосоединения часто требуется вводить несколько условий соединения. Упомянутая особенность поясняется в представленном ниже примере:  
  
```  
Cheryl Carson       Cheryl Carson  
   Abraham Bennet      Abraham Bennet  
   Cheryl Carson       Abraham Bennet  
   Abraham Bennet      Cheryl Carson  
```  
  
Первая строка бесполезна, поскольку в ней указано, что Cheryl Carson живет в том же городе, что и Cheryl Carson. Во второй строке также содержатся бесполезные данные. Чтобы исключить указанные бесполезные данные, необходимо добавить условие, обеспечивающее вывод только тех строк, которые содержат данные о разных авторах. Результирующий запрос может выглядеть так:  
  
```  
SELECT   
         authors.au_fname,   
         authors.au_lname,   
         authors1.au_fname AS Expr2,   
         authors1.au_lname AS Expr3  
      FROM   
         authors   
            INNER JOIN  
            authors authors1   
               ON authors.city   
                = authors1.city  
               AND authors.au_id  
                <> authors1.au_id  
      WHERE  
         authors.city = 'Berkeley'  
```  
  
Результирующий набор улучшен:  
  
```  
Cheryl Carson       Abraham Bennet  
   Abraham Bennet      Cheryl Carson  
```  
  
Однако две результирующие строки содержат избыточные данные. В первой строке указано, что автор с именем Carson проживает в одном городе с Bennet, а вторая строка говорит о том, что автор с именем «Bennet» проживает в одном городе с Carson. Подобного дублирования данных можно избежать, если во втором условии соединения заменить оператор «не равно» на «меньше». Результирующий запрос может выглядеть так:  
  
```  
SELECT   
         authors.au_fname,   
         authors.au_lname,   
         authors1.au_fname AS Expr2,   
         authors1.au_lname AS Expr3  
      FROM   
         authors   
            INNER JOIN  
            authors authors1   
               ON authors.city   
                = authors1.city  
               AND authors.au_id  
                < authors1.au_id  
      WHERE  
         authors.city = 'Berkeley'  
```  
  
Результирующий набор имеет следующий вид:  
  
```  
Cheryl Carson       Abraham Bennet  
```  
  
### <a name="to-create-a-self-join-manually"></a>Создание самосоединения вручную  
  
1.  На [панель диаграммы](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) добавьте необходимую таблицу или возвращающий табличное значение объект.  
  
2.  Затем еще раз добавьте эту таблицу, чтобы на панели диаграмм отображалось два экземпляра одной таблицы или возвращающего табличное значение объекта.  
  
    Конструктор запросов и представлений присваивает второму экземпляру псевдоним, добавляя порядковый номер к имени таблицы. Кроме того, конструктор запросов и представлений создает внутри панели диаграмм соединение указанных экземпляров таблицы или возвращающего табличное значение объекта.  
  
3.  Щелкните правой кнопкой мыши указанное соединение и в контекстном меню выберите **Свойства** .  
  
4.  В окне "Свойства" выберите вкладку **Условие и тип соединения** и нажмите кнопку с многоточием **(...)** справа от нужного свойства.  
  
5.  В [диалоговом окне "Соединение"](../../ssms/visual-db-tools/join-dialog-box-visual-database-tools.md) измените оператор сравнения первичных ключей. Например, можно выбрать оператор «меньше» (<).  
  
6.  Создайте дополнительное условие соединения, например authors.zip = authors1.zip, перетащив имя основного столбца соединения в первом экземпляре таблицы или возвращающего табличное значение объекта в область соответствующего столбца второго экземпляра.  
  
7.  Задайте другие параметры запроса, например выходные столбцы, условия поиска и порядок сортировки.  
  
## <a name="see-also"></a>См. также:  
[Автоматическое создание самосоединения (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-self-joins-automatically-visual-database-tools.md)  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  

