---
title: Система типов (XQuery) | Документация Майкрософт
description: Сведения о системе типов XQuery, которая включает встроенные типы схемы XML и типы, определенные в пространстве имен XPath-данных.
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sequence [XQuery]
- type system [XQuery]
- typed values [XQuery]
- XQuery, sequence
- string values [XQuery]
- XQuery, XPath data type namespace
- xdt prefix [XML in SQL Server]
- XQuery, type system
- built-in XML schema types [SQL Server]
- xs prefix [XML in SQL Server]
ms.assetid: 22d6f861-d058-47ee-b550-cbe9092dcb12
author: rothja
ms.author: jroth
ms.openlocfilehash: cb0b853b83fc65d8faddc341f9f0249debc2d2c1
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915280"
---
# <a name="type-system-xquery"></a>Система типов (XQuery)
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]

  XQuery является строго типизированным языком для типов схемы и слабо типизированным языком для нетипизированных данных. Ниже приведены стандартные типы данных языка XQuery:  
  
-   Встроенные типы схемы XML в **http://www.w3.org/2001/XMLSchema** пространстве имен.  
  
-   Типы, определенные в **http://www.w3.org/2004/07/xpath-datatypes** пространстве имен.  
  
 В этом разделе также описано следующее:  
  
-   Сравнение типизированных и строковых значений узла.  
  
-   [Функция data &#40;&#41;XQuery](../xquery/data-accessor-functions-data-xquery.md) и [строковая функция &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md).  
  
-   Сопоставление типов последовательности, возвращаемой выражением.  
  
## <a name="built-in-types-of-xml-schema"></a>Встроенные типы XML-схемы  
 Встроенные типы XML-схемы обозначаются в пространстве имен стандартным префиксом xs. К некоторым из этих типов относятся **xs: integer** и **xs: String**. Поддерживаются все встроенные типы данных. Эти типы могут быть использованы при создании коллекции XML-схем.  
  
 При обращении к типизированному XML статические и динамические типы узлов определяются коллекцией XML-схем, связанной со столбцом, к которому происходит обращение. Дополнительные сведения о статических и динамических типах см. в статьях [контекст выражения и вычисление запросов &#40;XQuery&#41;](../xquery/expression-context-and-query-evaluation-xquery.md). Например, следующий запрос задается для типизированного **XML-** столбца ( `Instructions` ). В выражении `instance of` используется для проверки того, что типизированное значение возвращенного атрибута `LotSize` имеет тип данных `xs:decimal`.  
  
```  
SELECT Instructions.query('  
   DECLARE namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   data(/AWMI:root[1]/AWMI:Location[@LocationID=10][1]/@LotSize)[1] instance of xs:decimal  
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Эти типизированные данные предоставляются коллекцией XML-схем, связанной с указанным столбцом.  
  
## <a name="types-defined-in-xpath-data-types-namespace"></a>Типы, определенные в пространстве имен типов данных XPath  
 Типы, определенные в **http://www.w3.org/2004/07/xpath-datatypes** пространстве имен, имеют предопределенный префикс **xdt**. Эти типы обладают следующими свойствами:  
  
-   Они не могут использоваться при создании коллекции XML-схем. Эти типы используются в системе типов XQuery и используются для [XQuery и статической типизации](../xquery/xquery-and-static-typing.md). Можно привести к атомарным типам, например **xdt: untypedAtomic**, в пространстве имен **xdt** .  
  
-   При запросе нетипизированного XML статический и динамический тип узлов элементов имеет тип **xdt: untypeed**, а тип значений атрибута — **xdt: untypedAtomic**. Результат выполнения метода **query ()** создает нетипизированный XML. Это означает, что узлы XML возвращаются как **xdt: untypeed** и **xdt: untypedAtomic**соответственно.  
  
-   Типы **xdt: dayTimeDuration** и **xdt: еармонсдуратион** не поддерживаются.  
  
 В следующем примере запрос задается на нетипизированной переменной XML. Выражение `data(/a[1]`) возвращает последовательность атомарных значений. Функция `data()` возвращает типизированное значение элемента `<a>`. Так как запрашиваемые XML не типизированы, возвращенное значение имеет тип `xdt:untypedAtomic`. Следовательно, выражение `instance of` возвращает значение True.  
  
```  
DECLARE @x xml  
SET @x='<a>20</a>'  
SELECT @x.query( 'data(/a[1]) instance of xdt:untypedAtomic' )  
```  
  
 Вместо извлечения типизированного значения выражение (`/a[1]`) в следующем примере возвращает последовательность, состоящую из одного элемента `<a>`. Выражение `instance of` использует проверку элементов для контроля того, что возвращаемое выражением значение является элементом узла типа `xdt:untyped type`.  
  
```  
DECLARE @x xml  
SET @x='<a>20</a>'  
-- Is this an element node whose name is "a" and type is xdt:untyped.  
SELECT @x.query( '/a[1] instance of element(a, xdt:untyped?)')  
-- Is this an element node of type xdt:untyped.  
SELECT @x.query( '/a[1] instance of element(*, xdt:untyped?)')  
-- Is this an element node?  
SELECT @x.query( '/a[1] instance of element()')  
```  
  
> [!NOTE]  
>  Если при обращении к типизированным XML-экземплярам в выражении запроса содержится родительская ось, сведения о статических типах результирующих узлов становятся недоступными. Однако динамические типы все равно остаются связанными с узлами.  
  
## <a name="typed-value-vs-string-value"></a>Сравнение типизированных и строковых значений  
 Каждый узел содержит типизированное и строковое значение. Для типизированных XML-данных тип значения определяется коллекцией XML-схем, связанной со столбцом или переменной, к которым происходит обращение. Для нетипизированных XML-данных типом типизированного значения является **xdt: untypedAtomic**.  
  
 Для получения значения узла можно использовать функцию **Data ()** или **String ()** :  
  
-   [Функция data &#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md) возвращает типизированное значение узла.  
  
-   [Строковая функция &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md) возвращает строковое значение узла.  
  
 В следующей коллекции XML-схем `root` определен элемент <> целочисленного типа:  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
      <element name="root" type="integer"/>  
</schema>'  
GO  
```  
  
 В следующем примере выражение вначале получает типизированное значение `/root[1]`, а затем добавляет к нему `3`.  
  
```  
DECLARE @x xml(SC)  
SET @x='<root>5</root>'  
SELECT @x.query('data(/root[1]) + 3')  
```  
  
 В следующем примере выражение завершается ошибкой, так как функция `string(/root[1])` возвращает значение строкового типа. Затем указанное значение передается арифметическому оператору, который может работать только с числовыми операндами.  
  
```  
-- Fails because the argument is string type (must be numeric primitive type).  
DECLARE @x xml(SC)  
SET @x='<root>5</root>'  
SELECT @x.query('string(/root[1]) + 3')  
```  
  
 В следующем примере производится вычисление общей суммы атрибутов `LaborHours`. `data()`Функция получает типизированные значения `LaborHours` атрибутов из всех `Location` элементов> <для модели продукта. В соответствии со схемой XML, связанной со `Instruction` столбцом, `LaborHours` имеет тип **xs: decimal** .  
  
```  
SELECT Instructions.query('   
DECLARE namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
             sum(data(//AWMI:Location/@LaborHours))   
') AS Result   
FROM Production.ProductModel   
WHERE ProductModelID=7  
```  
  
 Этот запрос возвращает значение 12,75.  
  
> [!NOTE]  
>  В этом примере явное использование функции **Data ()** используется только для иллюстрации. Если он не указан, функция **Sum ()** неявно применяет функцию **Data ()** для извлечения типизированных значений узлов.  
  
## <a name="see-also"></a>См. также:  
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Основы языка XQuery](../xquery/xquery-basics.md)  
  
  
