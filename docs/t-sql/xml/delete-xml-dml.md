---
title: "Удаление (XML DML) | Документы Microsoft"
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
- XML DML [SQL Server]
- delete keyword
- delete statement [XML DML]
- deleting nodes
ms.assetid: b22c93a4-b84d-4356-af4c-6013322a4b71
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57959308668cc5ea0455f6a4135c00482dbca15e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="delete-xml-dml"></a>delete (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Удаляет узлы из экземпляра XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
delete Expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *Выражение*  
 Выражение XQuery, определяющее удаляемые узлы. Будут удалены все узлы, указанные в выражении, а также все узлы или значения, содержащиеся в указанных узлах. Как описано в [insert (XML DML)](../../t-sql/xml/insert-xml-dml.md), это должна быть ссылка на существующий узел в документе. Оно не может ссылаться на создаваемый узел. Кроме того, выражение не может ссылаться на корневой (/) узел. Если выражение возвращает пустую последовательность, узлы не удаляются и ошибка не создается.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-deleting-nodes-from-a-document-stored-in-an-untyped-xml-variable"></a>A. Удаление узлов документа, хранящегося в нетипизированной XML-переменной  
 Следующий пример показывает, как удалить различные узлы документа. Во-первых, экземпляр XML назначается переменной **xml** типа. Последующие инструкции delete языка XML DML удаляют из документа различные узлы.  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<?Instructions for=TheWC.exe ?>   
<Root>  
 <!-- instructions for the 1st work center -->  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Some text 1  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
SELECT @myDoc  
  
-- delete an attribute  
SET @myDoc.modify('  
  delete /Root/Location/@MachineHours  
')  
SELECT @myDoc  
  
-- delete an element  
SET @myDoc.modify('  
  delete /Root/Location/step[2]  
')  
SELECT @myDoc  
  
-- delete text node (in <Location>  
SET @myDoc.modify('  
  delete /Root/Location/text()  
')  
SELECT @myDoc  
  
-- delete all processing instructions  
SET @myDoc.modify('  
  delete //processing-instruction()  
')  
SELECT @myDoc  
```  
  
### <a name="b-deleting-nodes-from-a-document-stored-in-an-untyped-xml-column"></a>Б. Удаление узлов из документа, хранящегося в нетипизированном XML-столбце  
 В следующем примере **удаление** инструкция XML DML удаляет второй дочерний элемент узла <`Features`> из документа, хранящегося в столбце.  
  
```  
CREATE TABLE T (i int, x xml)  
go  
INSERT INTO T VALUES(1,'<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>')  
go  
-- verify the contents before delete  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
-- delete the second feature  
UPDATE T  
SET x.modify('delete /Root/ProductDescription/Features/*[2]')  
-- verify the deletion  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   [Метод modify() (тип данных xml)](../../t-sql/xml/modify-method-xml-data-type.md) используется для указания **удалить** ключевое слово языка XML DML.  
  
-   [Метода query() (тип данных xml)](../../t-sql/xml/query-method-xml-data-type.md) используется для запроса документа.  
  
### <a name="c-deleting-nodes-from-a-typed-xml-column"></a>В. Удаление узлов из типизированного XML-столбца  
 В этом примере удаляются узлы из производственные инструкции хранятся XML-документа в типизированном **xml** столбца.  
  
 В примере сначала создается таблица (T) с типизированным **xml** столбца в базе данных AdventureWorks. Затем экземпляр XML с инструкциями по производству продукции копируется из столбца Instructions таблицы ProductModel в таблицу T, после чего из документа удаляются один или несколько узлов.  
  
```  
use AdventureWorks  
go  
drop table T  
go  
create table T(ProductModelID int primary key,   
Instructions xml (Production.ManuInstructionsSchemaCollection))  
go  
insert  T   
select ProductModelID, Instructions  
from Production.ProductModel  
where ProductModelID=7  
go  
select Instructions  
from T  
--1) insert <Location 1000/>. Note: <Root> must be singleton in the query  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  insert <MI:Location LocationID="1000"  LaborHours="1000" >  
           These are manu steps at location 1000.   
           <MI:step>New step1 instructions</MI:step>  
           Instructions for step 2 are here  
           <MI:step>New step 2 instructions</MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
  
-- delete an attribute  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/@LaborHours)   
')  
go  
select Instructions  
from T  
-- delete text in <location>  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/text())   
')  
go  
select Instructions  
from T  
-- delete 2nd manu step at location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/MI:step[2])   
')  
go  
select Instructions  
from T  
-- cleanup  
drop table T  
go  
```  
  
## <a name="see-also"></a>См. также:  
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных &#40; Язык XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

