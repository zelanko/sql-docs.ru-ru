---
title: "OPENXML (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENXML_TSQL
- OPENXML
dev_langs: TSQL
helpviewer_keywords:
- OPENXML statement
- rowsets [SQL Server], XML documents
- XML [SQL Server], rowset views
ms.assetid: 8088b114-7d01-435a-8e0d-b81abacc86d6
caps.latest.revision: "24"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7b1fb1d28c4bddb679bd4aab8ce6cb11f21caca5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="openxml-transact-sql"></a>OPENXML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  OPENXML предоставляет представление набора строк XML-документа. Так как OPENXML является поставщиком наборов строк, он может применяться в инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)], в которых могут быть использованы такие поставщики наборов строк, как таблицы, представления или функция OPENROWSET.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OPENXML( idoc int [ in] , rowpattern nvarchar [ in ] , [ flags byte [ in ] ] )   
[ WITH ( SchemaDeclaration | TableName ) ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *IDOC*  
 Дескриптор документа внутреннего представления XML-документа. Внутреннее представление XML-документа создается путем вызова **sp_xml_preparedocument**.  
  
 *rowpattern*  
 Шаблон XPath, используется для идентификации узлов (в XML-документе, дескриптор которого передается в *idoc* параметр) должен обрабатываться как строки.  
  
 *флаги*  
 Указывает на сопоставление, которое должно использоваться между XML-данными и реляционным набором строк, а также на порядок заполнения переполненного столбца. *флаги* является необязательным входным параметром и может принимать одно из следующих значений.  
  
|Байтовое значение|Description|  
|----------------|-----------------|  
|**0**|По умолчанию используется значение **атрибутивного** сопоставления.|  
|**1**|Используйте **атрибутивного** сопоставления. Может быть совмещено с XML_ELEMENTS. В этом случае **атрибутивного** сопоставление применяется первым и затем **элементного** сопоставление применяется для всех столбцов, которые еще не были обработаны с.|  
|**2**|Используйте **элементного** сопоставления. Может быть совмещено с XML_ATTRIBUTES. В этом случае **атрибутивного** сопоставление применяется первым и затем **элементного** сопоставление применяется для всех столбцов еще не обработаны.|  
|**8**|Может быть совмещено (логическое OR) с XML_ATTRIBUTES или XML_ELEMENTS. В смысле получения, этот флаг указывает, что используемые данные не должны копироваться в свойство переполнения  **@mp:xmltext** .|  
  
 *SchemaDeclaration*  
 Определение схемы формы: *ColName**ColType* [*ColPattern* | *метасвойства*] [**,** *ColNameColType* [*ColPattern* | *метасвойства*]...]  
  
 *ColName*  
 Название столбца в наборе строк.  
  
 *ColType*  
 Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] столбца в наборе строк. Если типы столбцов отличаются от соответствующих **xml** происходит типа данных атрибута, приведение типов.  
  
 *ColPattern*  
 Необязательный общий шаблон XPath, который описывает, как узлы XML должны быть сопоставлены столбцам. Если *ColPattern* не указан, сопоставление по умолчанию (**атрибутивного** или **элементного** сопоставления в соответствии с *флаги* ) выполняется.  
  
 Шаблон XPath, заданный как *ColPattern* используется для указания специального порядка сопоставления (в случае использования **атрибутивного** и **элементного** сопоставления), переписывает или расширяет сопоставление по умолчанию, указанное аргументом *флаги*.  
  
 Общий шаблон XPath, заданный как *ColPattern* также поддерживает метасвойства.  
  
 *Метасвойства*  
 Одно из метасвойств, предоставляемых OPENXML. Если *метасвойства* указано, что столбец содержит сведения, предоставленные метасвойством. Метасвойства позволяют извлекать сведения (такие как относительное положение и сведения о пространстве имен) об узлах XML. По сравнению с текстовым представлением метасвойства позволяют увидеть больше сведений.  
  
 *Имя_таблицы*  
 Имя таблицы, которое может быть указано (вместо *SchemaDeclaration*) Если таблица с необходимой схемой уже существует, и никакого шаблона столбцов являются обязательными.  
  
## <a name="remarks"></a>Замечания  
 Предложение WITH предоставляет формат набора строк (и Дополнительные сведения о необходимых сопоставлениях) с помощью *SchemaDeclaration* или указать существующую *TableName*. Если необязательное предложение WITH не указан, результаты возвращаются в **edge** формат таблицы. Краевые таблицы представляют собой структуру мелкогранулированного XML-документа (имена элементов/атрибутов, иерархия документа, пространства имен, и т. д.) в одной таблице.  
  
 В следующей таблице описаны структуры **edge** таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**bigint**|Уникальный идентификатор узла документов.<br /><br /> Корневой элемент имеет значение 0. Отрицательные значения идентификаторов зарезервированы.|  
|**parentid**|**bigint**|Идентифицирует родителя узла. Родитель, идентифицируемый данным идентификатором, не обязательно является родительским элементом, это зависит от значения NodeType узла, родитель которого идентифицируется этим идентификатором. Например, если узел является текстовым, его родительский узел может быть атрибутным узлом.<br /><br /> Если узел находится на верхнем уровне XML-документа, то его столбец **ParentID** принимает значение NULL.|  
|**Тип узла**|**int**|Идентифицирует тип узла. Целое число, которое соответствует нумерации типов узлов XML DOM.<br /><br /> Типы узлов бывают:<br /><br /> 1 = Элементный узел<br /><br /> 2 = Атрибутный узел<br /><br /> 3 = Текстовый узел|  
|**localname**|**nvarchar**|Задает локальное имя элемента или атрибута. Принимает значение NULL, если у объекта DOM нет имени.|  
|**prefix**|**nvarchar**|Префикс пространства имен для имени узла.|  
|**namespaceuri**|**nvarchar**|URI пространства имен для имени узла. Если значение равно NULL, пространство имен отсутствует.|  
|**datatype**|**nvarchar**|Настоящий тип данных элемента или строки атрибута, иначе равен NULL. Тип данных вычисляется на основе встроенного DTD или встроенной схемы|  
|**prev**|**bigint**|Идентификатор XML предыдущего элемента этого же уровня. Принимает значение NULL, если нет прямого предыдущего одноуровневого элемента.|  
|**text**|**ntext**|Содержит значение атрибута или содержимое элемента в текстовой форме (или имеет значение NULL, если **edge** запись в таблице не требуется значение).|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-a-simple-select-statement-with-openxml"></a>A. Использование простой инструкции SELECT с OPENXML  
 В следующем примере создается внутреннее представление образа XML с помощью процедуры `sp_xml_preparedocument`. Инструкция `SELECT`, которая использует поставщик набора строк `OPENXML`, выполняется для внутреннего представления XML-документа.  
  
 *Флаг* имеет значение `1`. Это означает **атрибутивного** сопоставления. Поэтому, XML-атрибуты сопоставляются столбцам набора строк. *Rowpattern* указанный в виде `/ROOT/Customer` идентифицирует `<Customers>` узлов для обработки.  
  
 Необязательный *ColPattern* (шаблон столбцов) не указан, так как имя столбца совпадает с именами XML-атрибутов.  
  
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
  
 Если же `SELECT` инструкция выполняется с *флаги* значение `2`, означающее **элементного** сопоставление, значения `CustomerID` и `ContactName` для обоих значение NULL, возвращаются заказчики в XML-документ, так как не все элементы с именем `CustomerID` или `ContactName` в XML-документе.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName  
---------- -----------  
NULL       NULL  
NULL       NULL  
```  
  
### <a name="b-specifying-colpattern-for-mapping-between-columns-and-the-xml-attributes"></a>Б. Указание ColPattern для сопоставления столбцов XML-атрибутам  
 Следующий запрос возвращает идентификатор клиента, дату заказа, идентификатор продукта и количественные атрибуты XML-документа. *Rowpattern* идентифицирует `<OrderDetails>` элементов. Аргументы `ProductID` и `Quantity` являются атрибутами элемента `<OrderDetails>`. Однако `OrderID`, `CustomerID` и `OrderDate` являются атрибутами родительского элемента (`<Orders>`).  
  
 Необязательный *ColPattern* указано. Это указывает на следующее.  
  
-   `OrderID`, `CustomerID`, И `OrderDate` в схеме набора строк с атрибутами родителя узлов, идентифицируемых по *rowpattern* в XML-документе.  
  
-   `ProdID` Столбец в наборе строк сопоставляется `ProductID` атрибут и `Qty` столбец в наборе строк сопоставляется `Quantity` атрибут узлов, заданных в *rowpattern*.  
  
 Несмотря на то что **элементного** сопоставление, указанное по *флаги* параметра, сопоставление, указанное в *ColPattern* перекрывает данное сопоставление.  
  
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
 Образец XML-документа в следующем примере состоит из элементов `<Customers>`, `<Orders>` и `<Order_0020_Details>`. Во-первых, **sp_xml_preparedocument** вызывается, чтобы получить дескриптор документа. Дескриптор документа передается `OPENXML`.  
  
 В `OPENXML` инструкции *rowpattern* (`/ROOT/Customers`) определяет `<Customers>` следует обрабатывать узлы. Поскольку предложение WITH не задано, `OPENXML` возвращает набор строк в **edge** формат таблицы.  
  
 Наконец `SELECT` инструкция извлекает все столбцы в **edge** таблицы.  
  
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
 [Примеры. Использование OPENXML](../../relational-databases/xml/examples-using-openxml.md)  
  
  
