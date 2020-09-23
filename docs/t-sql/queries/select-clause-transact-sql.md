---
description: Выражение SELECT (Transact-SQL)
title: Предложение SELECT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SELECT Clause
- SELECT_Clause_TSQL
- DISTINCT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- parentheses [SQL Server]
- identity columns [SQL Server], SELECT clause
- SELECT clause
- $IDENTITY keyword
- user-defined types [SQL Server], invoking methods and properties
- SELECT statement [SQL Server], processing orders
- clauses [SQL Server], SELECT
- $ROWGUID keyword
- queries [SQL Server], results
ms.assetid: 2616d800-4853-4cf1-af77-d32d68d8c2ef
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 84099c48344e27070433483eeac829640c3ce4c2
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91115900"
---
# <a name="select-clause-transact-sql"></a>Выражение SELECT (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Указывает столбцы, возвращаемые запросом.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
SELECT [ ALL | DISTINCT ]  
[ TOP ( expression ) [ PERCENT ] [ WITH TIES ] ]   
<select_list>   
<select_list> ::=   
    {   
      *   
      | { table_name | view_name | table_alias }.*   
      | {  
          [ { table_name | view_name | table_alias }. ]  
               { column_name | $IDENTITY | $ROWGUID }   
          | udt_column_name [ { . | :: } { { property_name | field_name }   
            | method_name ( argument [ ,...n] ) } ]  
          | expression  
          [ [ AS ] column_alias ]   
         }  
      | column_alias = expression   
    } [ ,...n ]   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 **ALL**  
 Указывает, что в результирующем наборе могут появиться повторяющиеся строки. ALL является параметром по умолчанию.  
  
 DISTINCT  
 Указывает, что в результирующем наборе могут появиться только уникальные строки. Значения NULL считаются равными для ключевого слова DISTINCT.  
  
 TOP (*expression* ) [ PERCENT ] [ WITH TIES ]  
 Указывает на то, что только заданное число или процент строк будет возвращен из результирующего набора запроса. *expression* может быть либо числом, либо процентом от числа строк.  
  
 В целях обратной совместимости использование TOP *expression* без скобок в инструкциях SELECT поддерживается, но не рекомендуется. Дополнительные сведения см. в разделе [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md).  
  
\< select_list > Столбцы, выбираемые в результирующий набор. Список выбора представляет собой серию выражений, отделяемых запятыми. Максимальное число выражений, которое можно задать в списке выбора — 4 096.  
  
 \*  
 Указывает на то, что все столбцы из всех таблиц и представлений в предложении FROM должны быть возвращены. Столбцы возвращаются таблицей или представлением, как указано в предложении FROM, и в порядке, в котором они находятся в таблице или представлении.  
  
 *table_name* | *view_name* | *table*_*alias*.*  
 Ограничивает область \* указанной таблицей или представлением.  
  
 *column_name*  
 Имя возвращаемого столбца. Указывайте квалификатор для аргумента *column_name* во избежание неоднозначных ссылок, которые могут возникнуть, если в двух таблицах из предложения FROM содержатся столбцы с повторяющимися именами. Например, таблицы SalesOrderHeader и SalesOrderDetail в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] содержат столбцы с именем ModifiedDate. Если в запросе соединяются две таблицы, то данные о дате изменения из таблицы SalesOrderDetail могут быть заданы в списке выбора как SalesOrderDetail.ModifiedDate.  
  
 *expression*  
 Является константой, функцией, любым сочетанием имен столбцов, констант и функций, соединенных оператором (операторами) или вложенным запросом.  
  
 $IDENTITY  
 Возвращает столбец идентификатора. Дополнительные сведения см. в статьях [IDENTITY (Property) (Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md), [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md) и [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).  
  
 Если более чем одна таблица из предложения FROM содержит столбец со свойством IDENTITY, $IDENTITY должно быть задано с определенным именем таблицы, например T1.$IDENTITY.  
  
 $ROWGUID  
 Возвращает столбец с идентификаторами GUID строки.  
  
 Если более чем одна таблица из предложения FROM содержит столбец со свойством ROWGUIDCOL, $ROWGUIDCOL должно быть задано с определенным именем таблицы, например T1.$IDENTITY.  
  
 *udt_column_name*  
 Имя возвращаемого, определяемого пользователем типа данных CLR столбца.  
  
> [!NOTE]  
>  Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] возвращает значения определяемого пользователем типа в двоичном представлении. Чтобы вернуть значения пользовательского типа в виде строки или в формате XML, используйте функцию [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) или [CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 { . | :: }  
 Указывает метод, свойство или поле пользовательского типа CLR. Используйте . для метода экземпляра (нестатического), свойства или поля. Используйте :: для статического метода, свойства или поля. Для обращения к методу, свойству или полю определяемого пользователем типа среды CLR необходимо разрешение EXECUTE для этого типа.  
  
 *property_name*  
 Открытое свойство столбца *udt_column_name*.  
  
 *field_name*  
 Открытый элемент данных столбца *udt_column_name*.  
  
 *method_name*  
 Открытый метод столбца *udt_column_name*, принимающий один или несколько аргументов. Метод *method_name* не может быть методом мутатора.  
  
 В следующем примере выбираются значения столбца `Location`, определенного типом `point`, из таблицы `Cities` путем обращения к методу типа, названного `Distance`:  
  
```sql
CREATE TABLE dbo.Cities (  
     Name VARCHAR(20),  
     State VARCHAR(20),  
     Location POINT);  
GO  
DECLARE @p POINT (32, 23), @distance FLOAT;  
GO  
SELECT Location.Distance (@p)  
FROM Cities;  
```  
  
 *column_ alias*  
 Альтернативное имя, которым можно заменить имя столбца в результирующем наборе запроса. Например, для столбца «quantity» может быть указан псевдоним «Quantity», «Quantity to Date» или «Qty».  
  
 Кроме того, псевдонимы используются для указания имен для результатов выражений, например:  
  
 ```sql
 USE AdventureWorks2012;  
 GO  
 SELECT AVG(UnitPrice) AS [Average Price]  
 FROM Sales.SalesOrderDetail;
 ```  
  
 *column_alias* может использоваться в предложении ORDER BY. Однако он не может быть использован в предложениях WHERE, GROUP BY или HAVING. Если выражение запроса является частью инструкции DECLARE CURSOR, *column_alias* не может использоваться в предложении FOR UPDATE.  
  
## <a name="remarks"></a>Remarks  
 Длина возвращаемых данных для столбцов типа **text** или **ntext**, включенных в список выбора, устанавливается в минимальное значение из следующих: фактический размер столбца **text**, значение настройки TEXTSIZE сеанса по умолчанию или жестко заданное в приложении ограничение. Чтобы изменить длину возвращаемого текста для сеанса, используйте инструкцию SET. По умолчанию ограничение на длину возвращаемых при помощи инструкции SELECT текстовых данных равно 4 000 байт.  
  
 Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] вызывает исключение номер 511 и осуществляет откат транзакции до момента выполнения текущей инструкции, если наблюдается одно из следующих явлений.  
  
-   Следствием инструкции SELECT является строка результата или строка промежуточной таблицы, превышающая 8 060 байт.  
  
-   Инструкции DELETE, INSERT или UPDATE производят действия со строкой, превышающей 8 060 байт.  
  
 Ошибка возникает в случае, если не указано имя столбца, созданного при помощи инструкции SELECT INTO или CREATE VIEW.  
  
## <a name="see-also"></a>См. также:  
 [Примеры использования инструкции SELECT (Transact-SQL)](../../t-sql/queries/select-examples-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  
