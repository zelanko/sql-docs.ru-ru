---
title: Примеры использования инструкции SELECT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- parentheses [SQL Server]
- GROUP BY clause, SELECT statement
- query hints [SQL Server]
- ALL keyword
- ROLLUP operator
- SELECT statement [SQL Server], examples
- correlated subqueries, SELECT statement
- SELECT INTO statement
- ORDER BY clause [Transact-SQL]
- GROUPING function
- index hints [SQL Server]
- HAVING clause, SELECT statement
- DISTINCT keyword
- CUBE operator
- UNION operator [SQL Server]
- computed sums
- WHERE clause, SELECT statement
ms.assetid: 9b9caa3d-e7d0-42e1-b60b-a5572142186c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e3d7c9b661a69f4a575a18aae03f9eb5e601b69b
ms.sourcegitcommit: ba44730f5cc33295ae2ed1f281186dd266bad4ef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2019
ms.locfileid: "74191089"
---
# <a name="select-examples-transact-sql"></a>Примеры использования инструкции SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  В этом разделе приведены примеры применения инструкции [SELECT](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="a-using-select-to-retrieve-rows-and-columns"></a>A. Использование SELECT для получения строк и столбцов  
 В следующем примере приведены три примера кода. В ходе выполнения первого примера кода возвращаются все строки (предложение WHERE не указано), а также все столбцы (используется звездочка, `*`) таблицы `Product` базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 [!code-sql[Select#SelectExamples1](../../t-sql/queries/codesnippet/tsql/select-examples-transact_1.sql)]  
  
 В ходе выполнения данного примера кода происходит выдача всех строк (предложение WHERE не задано) и подмножества столбцов (`Name`, `ProductNumber`, `ListPrice`) таблицы `Product` базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Дополнительно выведено название столбца.  
  
 [!code-sql[Select#SelectExamples2](../../t-sql/queries/codesnippet/tsql/select-examples-transact_2.sql)]  
  
 В ходе выполнения данного примера кода происходит выдача всех строк таблицы `Product`, для которых линейки продуктов начинаются символом `R` и для которых длительность изготовления не превышает `4` дней.  
  
 [!code-sql[Select#SelectExamples3](../../t-sql/queries/codesnippet/tsql/select-examples-transact_3.sql)]  
  
## <a name="b-using-select-with-column-headings-and-calculations"></a>Б. Использование SELECT с заголовками столбцов и вычислениями  
 В ходе выполнения следующего примера возвращаются все строки таблицы `Product`. В результате выполнения первого примера выдаются все объемы продаж и скидки по всем продуктам. Во втором примере вычисляется годовой доход от продажи каждого вида продукции.  
  
 [!code-sql[Select#SelectExamples4](../../t-sql/queries/codesnippet/tsql/select-examples-transact_4.sql)]  
  
 Данный запрос вычисляет доход от продажи по каждому виду продукции для каждого заказа.  
  
 [!code-sql[Select#SelectExamples5](../../t-sql/queries/codesnippet/tsql/select-examples-transact_5.sql)]  
  
## <a name="c-using-distinct-with-select"></a>В. Совместное использование DISTINCT и SELECT  
 В приведенном ниже примере для предотвращения получения повторяющихся заголовков используется оператор `DISTINCT`.  
  
 [!code-sql[Select#SelectExamples6](../../t-sql/queries/codesnippet/tsql/select-examples-transact_6.sql)]  
  
## <a name="d-creating-tables-with-select-into"></a>Г. Создание таблиц с помощью SELECT INTO  
 В следующем примере в базе данных `#Bicycles` создается временная таблица `tempdb`.  
  
 [!code-sql[Select#SelectExamples7](../../t-sql/queries/codesnippet/tsql/select-examples-transact_7.sql)]  
  
 В данном примере создается постоянная таблица `NewProducts`.  
  
 [!code-sql[Select#SelectExamples8](../../t-sql/queries/codesnippet/tsql/select-examples-transact_8.sql)]  
  
## <a name="e-using-correlated-subqueries"></a>Д. Использование связанных вложенных запросов
Коррелированный запрос — это запрос, зависящий от результатов выполнения другого запроса. Он может повторно выполняться для каждой строки, выбранной с помощью другого запроса.

В первом примере представлены семантически эквивалентные запросы для демонстрации различий в использовании ключевых слов `EXISTS` и `IN`. В обоих примерах приведены допустимые вложенные запросы, извлекающие по одному экземпляру продукции каждого наименования, для которых модель продукта — «long sleeve logo jersey» (кофта с длинными рукавами, с эмблемой), а значения столбцов `ProductModelID` таблиц `Product` и `ProductModel` совпадают.  
  
 [!code-sql[Select#SelectExamples9](../../t-sql/queries/codesnippet/tsql/select-examples-transact_9.sql)]  
  
 Следующий пример использует `IN` и получает имена и фамилии сотрудников, для которых значение премии в таблице `SalesPerson` составляет `5000.00`, а соответствующие им идентификационные номера в таблицах `Employee` и `SalesPerson` совпадают.  
  
 [!code-sql[Select#SelectExamples10](../../t-sql/queries/codesnippet/tsql/select-examples-transact_10.sql)]  
  
 Предыдущий вложенный запрос данной инструкции не может быть выполнен независимо от внешнего запроса. Требуется значение параметра `Employee.EmployeeID`, однако в процессе обработки строк `Employee` компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] указанное значение меняется.  
  
 Коррелированный вложенный запрос также может использоваться в предложении `HAVING` внешнего запроса. В данном примере осуществляется поиск моделей продуктов, для которых максимальная цена в каталоге в два раза превышает среднюю цену по нему.  
  
 [!code-sql[Select#SelectExamples11](../../t-sql/queries/codesnippet/tsql/select-examples-transact_11.sql)]  
  
 В данном примере с помощью двух коррелированных запросов осуществляется поиск сотрудников, продавших определенную продукцию.  
  
 [!code-sql[Select#SelectExamples12](../../t-sql/queries/codesnippet/tsql/select-examples-transact_12.sql)]  
  
## <a name="f-using-group-by"></a>Е. Использование GROUP BY  
 В следующем примере находится общий объем продаж для каждого заказа в базе данных.  
  
 [!code-sql[Select#SelectExamples13](../../t-sql/queries/codesnippet/tsql/select-examples-transact_13.sql)]  
  
 Так как в запросе используется предложение `GROUP BY`, то для каждого заказа выводится только одна строка, содержащая общий объем продаж.  
  
## <a name="g-using-group-by-with-multiple-groups"></a>Ж. Использование GROUP BY с несколькими группами  
 В данном примере вычисляются средние цены и объемы продаж за последний год, сгруппированные по коду продукта и идентификатору специального предложения.  
  
 [!code-sql[Select#SelectExamples14](../../t-sql/queries/codesnippet/tsql/select-examples-transact_14.sql)]  
  
## <a name="h-using-group-by-and-where"></a>З. Использование GROUP BY и WHERE  
 В следующем примере после извлечения строк, содержащих цены каталога, превышающие `$1000`, происходит их разделение на группы.  
  
 [!code-sql[Select#SelectExamples15](../../t-sql/queries/codesnippet/tsql/select-examples-transact_15.sql)]  
  
## <a name="i-using-group-by-with-an-expression"></a>И. Использование GROUP BY с выражением  
 В следующем примере производится группировка с помощью выражения. Группировку можно производить только с помощью выражения, не содержащего агрегатных функций.  
  
 [!code-sql[Select#SelectExamples16](../../t-sql/queries/codesnippet/tsql/select-examples-transact_16.sql)]  
  
## <a name="j-using-group-by-with-order-by"></a>К. Использование GROUP BY с ORDER BY  
 В следующем примере для каждого типа продуктов вычисляется средняя цена, а также осуществляется сортировка полученных результатов по возрастанию.  
  
 [!code-sql[Select#SelectExamples18](../../t-sql/queries/codesnippet/tsql/select-examples-transact_17.sql)]  
  
## <a name="k-using-the-having-clause"></a>Л. Использование предложения HAVING  
 В первом из приведенных ниже примеров показывается использование предложения `HAVING` с агрегатной функцией. В нем производится группировка строк таблицы `SalesOrderDetail` по коду продукта, а также удаляются строки, соответствующие продуктам, для которых средний объем заказа не превышает пяти. Во втором примере показывается использование предложения `HAVING` без агрегатной функции.  
  
 [!code-sql[Select#SelectExamples19](../../t-sql/queries/codesnippet/tsql/select-examples-transact_18.sql)]  
  
 В данном запросе внутри предложения `LIKE` используется предложение `HAVING`.  
  
```sql
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, CarrierTrackingNumber   
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID, CarrierTrackingNumber  
HAVING CarrierTrackingNumber LIKE '4BD%'  
ORDER BY SalesOrderID ;  
GO  
```  
  
## <a name="l-using-having-and-group-by"></a>М. Использование HAVING с GROUP BY  
 В следующем примере показано использование предложений `GROUP BY`, `HAVING`, `WHERE` и `ORDER BY` в одной инструкции `SELECT`. В результате его выполнения в группах и сводных значениях не учитываются строки, соответствующие продуктам с ценами выше $25 и средним объемом заказов ниже 5. Также осуществляется сортировка результатов по `ProductID`.  
  
 [!code-sql[Select#SelectExamples21](../../t-sql/queries/codesnippet/tsql/select-examples-transact_19.sql)]  
  
## <a name="m-using-having-with-sum-and-avg"></a>Н. Использование HAVING с SUM и AVG  
 В следующем примере производится группировка строк таблицы `SalesOrderDetail` по коду продукта, а затем выводятся только те группы, для которых общий объем продаж составляет более `$1000000.00`, а средний объем заказа не превышает `3`.  
  
 [!code-sql[Select#SelectExamples22](../../t-sql/queries/codesnippet/tsql/select-examples-transact_20.sql)]  
  
 Чтобы вывести список продуктов, для которых общий объем продаж составляет более `$2000000.00`, необходимо использовать следующий запрос:  
  
 [!code-sql[Select#SelectExamples23](../../t-sql/queries/codesnippet/tsql/select-examples-transact_21.sql)]  
  
 Если необходимо убедиться в том, что в вычислениях для каждого продукта используется не менее 1500 элементов, используется инструкция `HAVING COUNT(*) > 1500`, которая удаляет строки для продуктов с объемами продаж менее `1500`. Этот запрос выглядит следующим образом.  
  
 [!code-sql[Select#SelectExamples24](../../t-sql/queries/codesnippet/tsql/select-examples-transact_22.sql)]  
  
## <a name="n-using-the-index-optimizer-hint"></a>О. Использование указания оптимизатора INDEX  
 В следующем примере показаны два способа использования указания оптимизатора `INDEX`. В первом примере показано, как настроить оптимизатор на использование некластеризованного индекса для получения строк из таблицы. Во втором примере при использовании индекса 0 запускается просмотр таблицы.  
  
 [!code-sql[Select#SelectExamples45](../../t-sql/queries/codesnippet/tsql/select-examples-transact_23.sql)]  
  
## <a name="m-using-option-and-the-group-hints"></a>Н. Использование указаний OPTION и GROUP  
 В следующем примере демонстрируется совместное использование предложений `OPTION (GROUP)` и `GROUP BY`.  
  
 [!code-sql[Select#SelectExamples46](../../t-sql/queries/codesnippet/tsql/select-examples-transact_24.sql)]  
  
## <a name="o-using-the-union-query-hint"></a>П. Использование указания запроса UNION  
 В следующем примере используется указание запроса `MERGE UNION`.  
  
 [!code-sql[Select#SelectExamples47](../../t-sql/queries/codesnippet/tsql/select-examples-transact_25.sql)]  
  
## <a name="p-using-a-simple-union"></a>Т. Использование простого UNION  
 При выполнении следующего примера в результирующий набор включается содержимое столбцов `ProductModelID` и `Name` таблиц `ProductModel` и `Gloves`.  
  
 [!code-sql[Select#SelectExamples48](../../t-sql/queries/codesnippet/tsql/select-examples-transact_26.sql)]  
  
## <a name="q-using-select-into-with-union"></a>У. Использование SELECT INTO с UNION  
 При выполнении следующего примера предложение `INTO` во второй инструкции `SELECT` указывает, что в таблице с именем `ProductResults` содержится итоговый результирующий набор объединения заданных столбцов таблиц `ProductModel` и `Gloves`. Заметим, что таблица `Gloves` была создана в результате выполнения первой инструкции `SELECT`.  
  
 [!code-sql[Select#SelectExamples49](../../t-sql/queries/codesnippet/tsql/select-examples-transact_27.sql)]  
  
## <a name="r-using-union-of-two-select-statements-with-order-by"></a>Ф. Использование UNION двух инструкций SELECT с ORDER BY  
 При использовании предложения UNION необходимо соблюдать порядок следования определенных параметров. В следующем примере показаны случаи правильного и неверного использования `UNION` в двух инструкциях `SELECT`, в которых необходимо переименовать столбцы на выходе.  
  
 [!code-sql[Select#SelectExamples50](../../t-sql/queries/codesnippet/tsql/select-examples-transact_28.sql)]  
  
## <a name="s-using-union-of-three-select-statements-to-show-the-effects-of-all-and-parentheses"></a>Х. Использование UNION трех инструкций SELECT для демонстрации эффекта от использования скобок и ALL  
 В следующих примерах предложение `UNION` используется для комбинирования результатов из трех таблиц, содержащих по 5 одинаковых строк данных. В первом примере используется предложение `UNION ALL`, в результате чего выдаются все 15 строк. Во втором примере предложение `UNION` используется без ключевого слова `ALL`, что позволяет удалить повторяющиеся строки из комбинированного результата выполнения трех инструкций `SELECT` и вывести только 5 строк.  
  
 В третьем примере с первым предложением `ALL` используется ключевое слово `UNION`, а во втором предложении `UNION` вместо ключевого слова `ALL` используются скобки. Сначала выполняется второе предложение `UNION`, которое заключено в скобки. В результате возвращаются 5 строк, так как параметр `ALL` не используется и все повторяющиеся строки удаляются. Полученные 5 строк совмещаются с результатами выполнения первой инструкции `SELECT` с помощью ключевого слова `UNION ALL`. В данном случае повторяющиеся строки двух множеств не удаляются. Окончательный результат состоит из 10 строк.  
  
 [!code-sql[Select#SelectExamples51](../../t-sql/queries/codesnippet/tsql/select-examples-transact_29.sql)]  
  
## <a name="see-also"></a>См. также:  
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md)   
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [UNION (Transact-SQL)](../../t-sql/language-elements/set-operators-union-transact-sql.md)   
 [EXCEPT и INTERSECT (Transact-SQL)](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)   
 [PathName (Transact-SQL)](../../relational-databases/system-functions/pathname-transact-sql.md)   
 [Предложение INTO (Transact-SQL)](../../t-sql/queries/select-into-clause-transact-sql.md)  
  
  
