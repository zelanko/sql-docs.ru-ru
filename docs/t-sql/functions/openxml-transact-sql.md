---
title: OPENXML (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/20/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OPENXML_TSQL
- OPENXML
dev_langs:
- TSQL
helpviewer_keywords:
- OPENXML statement
- rowsets [SQL Server], XML documents
- XML [SQL Server], rowset views
ms.assetid: 8088b114-7d01-435a-8e0d-b81abacc86d6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac5e76c2d6e93bb8eb2fe334f38a22325e74d37f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62520710"
---
# <a name="openxml-transact-sql"></a>OPENXML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  OPENXML предоставляет представление набора строк XML-документа. Так как OPENXML является поставщиком наборов строк, он может применяться в инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)], в которых могут быть использованы такие поставщики наборов строк, как таблицы, представления или функция OPENROWSET.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPENXML( idoc int [ in] , rowpattern nvarchar [ in ] , [ flags byte [ in ] ] )   
[ WITH ( SchemaDeclaration | TableName ) ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *idoc*  
 Дескриптор документа внутреннего представления XML-документа. Внутреннее представление XML-документа создается путем вызова процедуры **sp_xml_preparedocument**.  
  
 *rowpattern*  
 Шаблон XPath, используемый для указания узлов, которые будут обработаны в качестве строк. Узлы поступают из XML-документа, дескриптор которого передается в параметре *idoc*.
  
 *flags*  
 Указывает на сопоставление, используемое между XML-данными и реляционным набором строк, а также на порядок заполнения переполненного столбца. Аргумент *flags* является необязательным входным параметром и может принимать одно из указанных ниже значений.  
  
|Байтовое значение|Описание|  
|----------------|-----------------|  
|**0**|По умолчанию используется **атрибутивная модель** сопоставления.|  
|**1**|Использовать **атрибутивную модель** сопоставления. Может быть совмещено с XML_ELEMENTS. В этом случае сначала применяется **атрибутивная модель сопоставления**. Затем для всех остальных столбцов применяется **элементная модель сопоставления**.|  
|**2**|Использовать сопоставление **с использованием элементов**. Может быть совмещено с XML_ATTRIBUTES. В этом случае сначала применяется **атрибутивная модель сопоставления**. Затем для всех остальных столбцов применяется **элементная модель сопоставления**.|  
|**8**|Может быть совмещено (логическое OR) с XML_ATTRIBUTES или XML_ELEMENTS. В контексте получения этот флаг указывает, что используемые данные не должны копироваться в свойство переполнения **\@mp:xmltext**.|  
  
 _SchemaDeclaration_  
 Имеет ли определение схемы следующую форму: _ColName_*ColType* [_ColPattern_ | _MetaProperty_] [ **,** _ColNameColType_ [_ColPattern_ | _MetaProperty_]...]  
  
 _ColName_  
 Название столбца в наборе строк.  
  
 *ColType*  
 Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца в наборе строк. Если типы столбцов отличаются от базовых типов данных **xml** атрибута, происходит приведение типов.  
  
 *ColPattern*  
 Необязательный общий шаблон XPath, который описывает, как узлы XML должны быть сопоставлены столбцам. Если аргумент *ColPattern* не указан, применяется сопоставление по умолчанию (**атрибутивная** или **элементная модель сопоставления**, как указано в аргументе *flags*).  
  
 Шаблон XPath, заданный как *ColPattern*, используется для указания специального порядка сопоставления (для **атрибутивной** и **элементной моделей сопоставления**), которое переопределяет или расширяет сопоставление по умолчанию, указанное в аргументе *flags*.  
  
 Общий шаблон XPath, заданный как аргумент *ColPattern*, также поддерживает метасвойства.  
  
 *MetaProperty*  
 Одно из метасвойств, предоставляемых OPENXML. Если задано свойство *MetaProperty*, столбец содержит сведения, предоставленные метасвойством. Метасвойства позволяют извлекать сведения (такие как относительное положение и сведения о пространстве имен) об узлах XML. По сравнению с текстовым представлением эти метасвойства позволяют увидеть больше сведений.  
  
 *TableName*  
 Имя таблицы, которое может быть указано (вместо аргумента *SchemaDeclaration*), если таблица с необходимой схемой уже существует и не требует никаких шаблонов столбцов.  
  
## <a name="remarks"></a>Remarks  
 Предложение WITH предоставляет формат набора строк (и дополнительные сведения о сопоставлении, если необходимо), используя либо аргумент *SchemaDeclaration*, либо указывая существующее значение аргумента *TableName*. Если необязательное предложение WITH не задано, результаты возвращаются в формате **граничной** таблицы. Краевые таблицы представляют собой структуру мелкогранулированного XML-документа (имена элементов/атрибутов, иерархия документа, пространства имен, и т. д.) в одной таблице.  
  
 В представленной ниже таблице описывается структура **граничной** таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**bigint**|Уникальный идентификатор узла документов.<br /><br /> Корневой элемент имеет значение 0. Отрицательные значения идентификаторов зарезервированы.|  
|**parentid**|**bigint**|Идентифицирует родителя узла. Родитель, идентифицируемый данным идентификатором, не обязательно является родительским элементом, это зависит от значения NodeType узла, родитель которого идентифицируется этим идентификатором. Например, если узел является текстовым, его родительский узел может быть атрибутным узлом.<br /><br /> Если узел находится на верхнем уровне XML-документа, то его столбец **ParentID** принимает значение NULL.|  
|**nodetype**|**int**|Идентифицирует тип узла. Целое число, которое соответствует нумерации типов узлов XML DOM.<br /><br /> Типы узлов бывают:<br /><br /> 1 = Элементный узел<br /><br /> 2 = Атрибутный узел<br /><br /> 3 = Текстовый узел|  
|**localname**|**nvarchar**|Задает локальное имя элемента или атрибута. Принимает значение NULL, если у объекта DOM нет имени.|  
|**prefix**|**nvarchar**|Префикс пространства имен для имени узла.|  
|**namespaceuri**|**nvarchar**|URI пространства имен для имени узла. Если значение равно NULL, пространство имен отсутствует.|  
|**datatype**|**nvarchar**|Настоящий тип данных элемента или строки атрибута, иначе равен NULL. Тип данных вычисляется на основе встроенного DTD или встроенной схемы|  
|**prev**|**bigint**|Идентификатор XML предыдущего элемента этого же уровня. Принимает значение NULL, если нет прямого предыдущего одноуровневого элемента.|  
|**text**|**ntext**|Содержит значение атрибута или содержимое элемента в текстовой форме (или равен NULL, если запись **граничной** таблицы не требует значения).|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-simple-select-statement-with-openxml"></a>A. Использование простой инструкции SELECT с OPENXML  
 В следующем примере создается внутреннее представление образа XML с помощью процедуры `sp_xml_preparedocument`. Инструкция `SELECT`, которая использует поставщик набора строк `OPENXML`, выполняется для внутреннего представления XML-документа.  
  
 Значение аргумента *flag* устанавливается равным `1`. Это значение свидетельствует об **атрибутивной модели** сопоставления. Поэтому, XML-атрибуты сопоставляются столбцам набора строк. Аргумент *rowpattern*, заданный как `/ROOT/Customer`, указывает, какие узлы `<Customers>` должны обрабатываться.  
  
 Необязательный аргумент *ColPattern* (шаблон столбцов) не задан, так как имя столбца совпадает с именами XML-атрибутов.  
  
 Поставщик набора строк `OPENXML` создает набор строк с двумя столбцами (`CustomerID` и `ContactName`), из которых инструкция `SELECT` извлекает необходимые столбцы (в данном случае, все столбцы).  
  
```  
DECLARE @idoc int, @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;  
-- Execute a SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customer',1)  
            WITH (CustomerID  varchar(10),  
                  ContactName varchar(20));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 Если выполняется та же инструкция `SELECT` с аргументом *flags*, установленным в значение `2` и указывающим на **элементное сопоставление**, значения аргументов `CustomerID` и `ContactName` для обоих клиентов в XML-документе возвращаются как NULL, потому что в XML-документе отсутствуют элементы с именами `CustomerID` или `ContactName`.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName  
---------- -----------  
NULL       NULL  
NULL       NULL  
```  
  
### <a name="b-specifying-colpattern-for-mapping-between-columns-and-the-xml-attributes"></a>Б. Указание ColPattern для сопоставления столбцов XML-атрибутам  
 Следующий запрос возвращает идентификатор клиента, дату заказа, идентификатор продукта и количественные атрибуты XML-документа. Аргумент *rowpattern* идентифицирует элементы `<OrderDetails>`. Аргументы `ProductID` и `Quantity` являются атрибутами элемента `<OrderDetails>`. Однако `OrderID`, `CustomerID` и `OrderDate` являются атрибутами родительского элемента (`<Orders>`).  
  
 Дополнительный атрибут *ColPattern* указывается для следующих сопоставлений:  
  
-   `OrderID`, `CustomerID` и `OrderDate` в наборе строк сопоставляются с атрибутами родительского узла узлов, заданных в аргументе *rowpattern* в XML-документе.  
  
-   Столбец `ProdID` в наборе строк сопоставляется с атрибутом `ProductID`, а столбец `Qty` в наборе строк сопоставляется с атрибутом `Quantity` узлов, заданных в аргументе *rowpattern*.  
  
 Хотя **сопоставление с использованием элементов** задано в аргументе *flags*, сопоставление, заданное в аргументе *ColPattern*, переопределяет это сопоставление.  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">v  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';   
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT stmt using OPENXML rowset provider  
SELECT *  
FROM   OPENXML (@idoc, '/ROOT/Customer/Order/OrderDetail',2)   
         WITH (OrderID       int         '../@OrderID',   
               CustomerID  varchar(10) '../@CustomerID',   
               OrderDate   datetime    '../@OrderDate',   
               ProdID      int         '@ProductID',   
               Qty         int         '@Quantity');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
OrderID CustomerID           OrderDate                 ProdID    Qty  
------------------------------------------------------------------------  
10248      VINET       1996-07-04 00:00:00.000   11      12  
10248      VINET       1996-07-04 00:00:00.000   42      10  
10283      LILAS       1996-08-16 00:00:00.000   72      3  
```  
  
### <a name="c-obtaining-results-in-an-edge-table-format"></a>В. Получение результатов в формате краевой таблицы  
 Образец XML-документа в следующем примере состоит из элементов `<Customers>`, `<Orders>` и `<Order_0020_Details>`. Сначала вызывается хранимая процедура **sp_xml_preparedocument**, чтобы получить дескриптор документа. Дескриптор документа передается `OPENXML`.  
  
 В инструкции `OPENXML` *rowpattern* (`/ROOT/Customers`) задает узлы `<Customers>` для обработки. Так как предложение WITH не предоставлено, `OPENXML` возвращает набор строк в формате **граничной** таблицы.  
  
 Наконец, инструкция `SELECT` извлекает все столбцы в **граничной** таблице.  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customers CustomerID="VINET" ContactName="Paul Henriot">  
   <Orders CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <Order_x0020_Details OrderID="10248" ProductID="11" Quantity="12"/>  
      <Order_x0020_Details OrderID="10248" ProductID="42" Quantity="10"/>  
   </Orders>  
</Customers>  
<Customers CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Orders CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <Order_x0020_Details OrderID="10283" ProductID="72" Quantity="3"/>  
   </Orders>  
</Customers>  
</ROOT>';  
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customers')   
EXEC sp_xml_removedocument @idoc;  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Примеры. Использование OPENXML](../../relational-databases/xml/examples-using-openxml.md)  
  
