---
title: "Метод (тип данных xml) nodes() | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nodes() method
- nodes method
ms.assetid: 7267fe1b-2e34-4213-8bbf-1c953822446c
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5fbbbd268398ab46b150f647a8d19689d198e6e8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="nodes-method-xml-data-type"></a>Метод nodes() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **Nodes()** метод полезен, когда нужно взять часть **xml** экземпляр типа данных в реляционных данных. Он позволяет идентифицировать узлы, которые будут ставиться в соответствие новой строке.  
  
 Каждый **xml** неявно заданный контекстный узел имеет экземпляр типа данных. Для сохраняемого в столбце или переменной экземпляра XML таким узлом является узел документов. Узел документа является неявным узлом, находящимся в верхней части каждого **xml** экземпляр типа данных.  
  
 Результат **nodes()** метод является набор строк, содержащий логические копии исходных экземпляров XML. В этих логических копиях контекстным узлом каждого экземпляра строки устанавливается один из узлов, идентифицируемых выражением запроса, так что последующие запросы могут перемещаться относительно этих контекстных узлов.  
  
 Из этих наборов строк могут извлекаться несколько значений. Например, можно применить **value()** метод к набору строк, возвращенных **nodes()** и извлечения нескольких значений из исходного экземпляра XML. Обратите внимание, что **value()** , примененный к экземпляру XML, возвращает только одно значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
nodes (XQuery) as Table(Column)  
```  
  
## <a name="arguments"></a>Аргументы  
 *XQuery*  
 Строковый литерал, выражение XQuery. Если выражение запроса конструирует узлы, эти сконструированные узлы представлены в результирующем наборе строк. Если результатом выражения запроса является пустая последовательность, набор строк будет пустым. Если статическим результатом выражения запроса является последовательность, которая вместо узлов содержит атомарные значения, возникает статическая ошибка.  
  
 *Таблица*(*столбца*)  
 Имя таблицы и имя столбца для результирующего набора строк.  
  
## <a name="remarks"></a>Замечания  
 В качестве примера предположим, что имеется следующая таблица:  
  
```  
T (ProductModelID int, Instructions xml)  
```  
  
 В таблице хранится следующее руководство по изготовлению. Здесь показан только фрагмент этого документа. Обратите внимание на то, что в документе указываются три места производства.  
  
```  
<root>  
  <Location LocationID="10"...>  
     <step>...</step>  
     <step>...</step>  
      ...  
  </Location>  
  <Location LocationID="20" ...>  
       ...  
  </Location>  
  <Location LocationID="30" ...>  
       ...  
  </Location>  
</root>  
```  
  
 Вызов метода `nodes()` с выражением запроса `/root/Location` возвращает набор из трех строк, каждая из которых содержит логическую копию исходного XML-документа с контекстным элементом, присвоенным одному из узлов `<Location>`:  
  
```  
Product  
ModelID      Instructions  
----------------------------------  
1       <root>  
             <Location LocationID="20" ... />  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
             <Location LocationID="20" ... />  
             </root>  
```  
  
 Затем можно запросить этот набор строк с помощью **xml** методов типа данных. Следующий запрос извлекает поддерево элемента контекста для каждой сформированной строки:  
  
```  
SELECT T2.Loc.query('.')  
FROM   T  
CROSS APPLY Instructions.nodes('/root/Location') as T2(Loc)   
```  
  
 Результат:  
  
```  
ProductModelID  Instructions  
----------------------------------  
1        <Location LocationID="10" ... />  
1        <Location LocationID="20" ... />  
1        <Location LocationID="30" .../>  
```  
  
 Обратите внимание на то, что в возвращаемом наборе строк сохраняется информация о типе. Можно применить **xml** методы, такие как тип данных **query()**, **value()**, **exist()**, и **nodes()** , чтобы результат **nodes()** метод. Тем не менее, нельзя применить **modify()** метод для изменения экземпляра XML.  
  
 Кроме того, контекстный узел в наборе строк не может быть материализован. Это означает, что он не может использоваться в инструкции SELECT. Однако он может использоваться в выражениях IS NULL и COUNT(*).  
  
 Сценарии использования **nodes()** метод являются так же, как с помощью [OPENXML &#40; Transact-SQL &#41; ](../../t-sql/functions/openxml-transact-sql.md). Тем самым обеспечивается представление набора строк XML. Тем не менее, не нужно использовать курсоры при использовании **nodes()** на таблице, содержащей несколько строк XML-документов.  
  
 Обратите внимание, что в возвращаемом наборе строк с **nodes()** метод является неименованным набором строк. Поэтому он должен быть именован при помощи механизма псевдонимов.  
  
 **Nodes()** функция не может применяться непосредственно к результатам пользовательской функции. Для использования **nodes()** функция с результатом скалярной определяемой пользователем функции, можно присвоить переменной результат определяемой пользователем функции или использовать производную таблицу для назначения псевдонима столбца определяемой пользователем функции Возвращаемое значение и затем использовать CROSS APPLY для выбора из псевдонима.  
  
 В следующем примере показан один из способов использования инструкции `CROSS APPLY` для выборки из результата пользовательской функции.  
  
```  
USE AdventureWorks;  
GO  
  
CREATE FUNCTION XTest()  
RETURNS xml  
AS  
BEGIN  
RETURN '<document/>';  
END;  
GO  
  
SELECT A2.B.query('.')  
FROM  
(SELECT dbo.XTest()) AS A1(X)   
CROSS APPLY X.nodes('.') A2(B);  
GO  
  
DROP FUNCTION XTest;  
GO  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="using-nodes-method-against-a-variable-of-xml-type"></a>Применение метода nodes() к переменной типа данных xml  
 В этом примере имеется XML-документ с элементом верхнего уровня <`Root`> и тремя дочерними элементами <`row`>. Запрос использует метод `nodes()` для разделения контекстных узлов, по одному для каждого элемента <`row`>. Метод `nodes()` возвращает набор из трех строк. Каждая строка имеет логическую копию исходного XML, с контекстными узлами, идентифицирующими разные элементы <`row`> исходного документа.  
  
 Запрос возвращает контекстный узел из каждой строки:  
  
```  
DECLARE @x xml   
SET @x='<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>'  
SELECT T.c.query('.') AS result  
FROM   @x.nodes('/Root/row') T(c)  
GO  
```  
  
 Ниже показан результат. В этом примере метод запроса возвращает элемент контекста и его содержимое:  
  
```  
<row id="1"><name>Larry</name><oflw>some text</oflw></row>  
<row id="2"><name>moe</name></row>  
<row id="3"/>  
```  
  
 Применение родительского метода доступа на контекстных узлах возвращает элемент <`Root`> для всех трех узлов:  
  
```  
SELECT T.c.query('..') AS result  
FROM   @x.nodes('/Root/row') T(c)  
go  
```  
  
 Результат:  
  
```  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
```  
  
### <a name="specifying-the-nodes-method-against-a-column-of-xml-type"></a>Задание метода nodes() для столбца типа данных xml  
 В этом примере используются по производству велосипедов и хранится в столбце Instructions **xml** в столбце Тип **ProductModel** таблицы.  
  
 В следующем примере `nodes()` адресован метод `Instructions` столбец **xml** введите `ProductModel` таблицы.  
  
 Метод `nodes()` устанавливает элементы <`Location`> как контекстные узлы, задавая путь `/MI:root/MI:Location`. Результирующий набор строк включает в себя логические копии исходного документа, одну для каждого узла <`Location`> в документе, с контекстным узлом, установленным в элемент <`Location`>. Таким образом, функция `nodes()` выдает набор контекстных узлов <`Location`>.  
  
 Метод `query()`, применяемый к этому набору строк, запрашивает `self::node` и возвращает элемент `<Location>` для каждой строки.  
  
 В этом примере запрос устанавливает каждый элемент <`Location`> как контекстный узел в руководстве по изготовлению определенной производственной модели. Эти контекстные узлы можно использовать для извлечения значений следующим образом:  
  
-   Найти идентификаторы LocationID в каждом <`Location`>  
  
-   Получить этапы производства (<`step`> дочерних элементов) в каждом <`Location`>  
  
 Этот запрос возвращает контекстный элемент, у которого в методе `'.'` используется сокращенный синтаксис `self::node()` для `query()`.  
  
 Следует отметить следующее.  
  
-   Метод `nodes()` применяется к столбцу Instructions и возвращает набор строк `T (C)`. Этот набор строк содержит логические копии исходного руководства по изготовлению с `/root/Location` в качестве контекстного элемента.  
  
-   Инструкция CROSS APPLY применяет метод `nodes()` к каждой строке в таблице `Instructions` и возвращает только строки, образующие результирующий набор.  
  
    ```  
    SELECT C.query('.') as result  
    FROM Production.ProductModel  
    CROSS APPLY Instructions.nodes('  
    declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /MI:root/MI:Location') as T(C)  
    WHERE ProductModelID=7  
    ```  
  
     Частичный результат:  
  
    ```  
    <MI:Location LocationID="10"  ...>  
       <MI:step ... />  
          ...  
    </MI:Location>  
    <MI:Location LocationID="20"  ... >  
        <MI:step ... />  
          ...  
    </MI:Location>  
    ...  
    ```  
  
### <a name="applying-nodes-to-the-rowset-returned-by-another-nodes-method"></a>Применение метода nodes() к набору строк, возвращенному другим методом nodes()  
 В следующем коде из столбца `Instructions` таблицы `ProductModel` запрашиваются XML-документы, составляющие руководство по изготовлению. Запрос возвращает набор строк, содержащий идентификатор производственной модели, места производства и шаги производства.  
  
 Следует отметить следующее.  
  
-   Метод `nodes()` применяется к столбцу `Instructions` и возвращает набор строк `T1 (Locations)`, Этот набор строк содержит логические копии исходного руководства по изготовлению с `/root/Location` в качестве контекстного элемента.  
  
-   Метод `nodes()` применяется к набору строк `T1 (Locations)` и возвращает набор строк `T2 (steps)`. Этот набор строк содержит логические копии исходного руководства по изготовлению с `/root/Location/step` в качестве контекстного элемента.  
  
```  
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO         
```  
  
 Результат:  
  
```  
ProductModelID LocID Step         
----------------------------         
7      10   <step ... />         
7      10   <step ... />         
...         
7      20   <step ... />         
7      20   <step ... />         
7      20   <step ... />         
...         
```  
  
 В запросе префикс `MI` объявляется два раза. Вместо этого можно воспользоваться `WITH XMLNAMESPACES`, чтобы объявить этот префикс один раз и использовать его в запросе:  
  
```  
WITH XMLNAMESPACES (  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions'  AS MI)  
  
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO    
```  
  
## <a name="see-also"></a>См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [Методы для типа данных XML](../../t-sql/xml/xml-data-type-methods.md)  
  
  

