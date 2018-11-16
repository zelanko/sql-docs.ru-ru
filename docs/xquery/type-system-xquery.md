---
title: Тип системы (XQuery) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: e8b4680532843b9f60b6cdab3c0c528aab719dbf
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668674"
---
# <a name="type-system-xquery"></a>Система типов (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XQuery является строго типизированным языком для типов схемы и слабо типизированным языком для нетипизированных данных. Ниже приведены стандартные типы данных языка XQuery:  
  
-   Встроенные типы XML-схем в **https://www.w3.org/2001/XMLSchema** пространства имен.  
  
-   Типы, определенные в **https://www.w3.org/2004/07/xpath-datatypes** пространства имен.  
  
 В этом разделе также описано следующее:  
  
-   Сравнение типизированных и строковых значений узла.  
  
-   [Данных функция &#40;XQuery&#41; ](../xquery/data-accessor-functions-data-xquery.md) и [строку функция &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md).  
  
-   Сопоставление типов последовательности, возвращаемой выражением.  
  
## <a name="built-in-types-of-xml-schema"></a>Встроенные типы XML-схемы  
 Встроенные типы XML-схемы обозначаются в пространстве имен стандартным префиксом xs. Ниже перечислены некоторые из этих типов **xs: Integer** и **xs: String**. Поддерживаются все встроенные типы данных. Эти типы могут быть использованы при создании коллекции XML-схем.  
  
 При обращении к типизированному XML статические и динамические типы узлов определяются коллекцией XML-схем, связанной со столбцом, к которому происходит обращение. Дополнительные сведения о статических и динамических типах см. в разделе [контекст выражения и вычисление запросов &#40;XQuery&#41;](../xquery/expression-context-and-query-evaluation-xquery.md). Например, следующий запрос указывается к типизированному **xml** столбца (`Instructions`). В выражении `instance of` используется для проверки того, что типизированное значение возвращенного атрибута `LotSize` имеет тип данных `xs:decimal`.  
  
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
 Типы, определенные в **https://www.w3.org/2004/07/xpath-datatypes** пространство имен обязательно стандартным префиксом **xdt**. Эти типы обладают следующими свойствами:  
  
-   Они не могут использоваться при создании коллекции XML-схем. Эти типы используются в системе типов XQuery и используются для [XQuery и Статическая типизация](../xquery/xquery-and-static-typing.md). Могут быть приведены к атомарным типам, например, **xdt: untypedAtomic**в **xdt** пространства имен.  
  
-   При обращении к нетипизированным XML, является статическим и динамическим типом узловых элементов **xdt: нетипизированный**, и имеет тип значения атрибутов **xdt: untypedAtomic**. Результат **query()** метод создает нетипизированного XML. Это означает, что XML-узлы возвращаются в виде **xdt: нетипизированный** и **xdt: untypedAtomic**, соответственно.  
  
-   **Xdt: daytimeduration** и **xdt: yearmonthduration** типы не поддерживаются.  
  
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
  
## <a name="typed-value-vs-string-value"></a>Введенное значение Строковое значение  
 Каждый узел содержит типизированное и строковое значение. Для типизированных XML-данных тип значения определяется коллекцией XML-схем, связанной со столбцом или переменной, к которым происходит обращение. Для нетипизированных XML-данных, типом значения является **xdt: untypedAtomic**.  
  
 Можно использовать **data()** или **string()** функции для получения значения узла:  
  
-   [Данных функция &#40;XQuery&#41; ](../xquery/data-accessor-functions-data-xquery.md) возвращает типизированное значение узла.  
  
-   [Строку функция &#40;XQuery&#41; ](../xquery/data-accessor-functions-string-xquery.md) возвращает строковое значение узла.  
  
 В представленной ниже коллекции XML-схем определяется целочисленный элемент <`root`>:  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema">  
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
  
 В следующем примере производится вычисление общей суммы атрибутов `LaborHours`. `data()` Функция получает типизированные значения `LaborHours` атрибуты из всех <`Location`> элементы для модели продукта. В соответствии со схемой XML, связанный с `Instruction` столбце `LaborHours` имеет **xs: decimal** типа.  
  
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
>  Явное использование **data()** функции в этом примере приведен исключительно для иллюстрации. Если он не указан, **sum()** неявно применяет **data()** функция для извлечения типизированных значений узлов.  
  
## <a name="see-also"></a>См. также  
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Основы XQuery](../xquery/xquery-basics.md)  
  
  
