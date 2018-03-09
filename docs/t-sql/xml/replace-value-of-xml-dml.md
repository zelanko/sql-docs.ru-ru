---
title: "Замените значение (XML DML) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- XML DML [SQL Server]
- update keyword
- replacement values [XML DML]
- updating node values
- replace value of XML DML statement
ms.assetid: c310f6df-7adf-493b-b56b-8e3143b13ae7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 236e919d1817e100c043e29de94c25442aac776f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="replace-value-of-xml-dml"></a>replace value of (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Обновляет значение узла в документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
replace value of Expression1   
with Expression2  
```  
  
## <a name="arguments"></a>Аргументы  
 *Expression1*  
 Определяет узел, значение которого должно быть обновлено. Оно должно определять только один узел. То есть *Expression1* должен быть образом Singleton-классом. Если XML типизирован, тип узла должен быть простым типом. Выбор нескольких узлов вызовет ошибку. Если *Expression1* возвращает пустую последовательность, то замены значения не произойдет и никакие ошибки не возвращаются. *Expression1* должно возвратить одиночный элемент, имеющий простое типизированное содержимое (список или атомарные типы), текстовый узел или узел атрибута. *Expression1* не может быть типом объединения, сложный тип, инструкции по обработке, узел документа или узлом комментария. Если же оно является чем-либо из вышеперечисленного, будет возвращена ошибка.  
  
 *Expression2*  
 Определяет новое значение узла. Это может быть выражение, которое возвращает простой типизированный узел, так как **data()** будет использоваться неявно. Если значение представляет собой список значений, **обновление** инструкции заменит старое значение списком. При изменении типизированного экземпляра XML, *Expression2* должен быть того же типа или подтипа *выражение*1. Иначе возвращается ошибка. При изменении нетипизированного экземпляра XML, *Expression2* должен быть выражением, которое может быть атомизировано. Иначе возвращается ошибка.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано **замените значение** инструкции XML DML показано, как обновить узлы в документе XML.  
  
### <a name="a-replacing-values-in-an-xml-instance"></a>A. Замена значений в экземпляре XML  
 В следующем примере экземпляр документа сначала назначается переменной **xml** типа. Затем **замените значение** инструкций XML DML обновить значения в документе.  
  
```  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Manufacturing steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>';  
SELECT @myDoc;  
  
-- update text in the first manufacturing step  
SET @myDoc.modify('  
  replace value of (/Root/Location/step[1]/text())[1]  
  with     "new text describing the manu step"  
');  
SELECT @myDoc;  
-- update attribute value  
SET @myDoc.modify('  
  replace value of (/Root/Location/@LaborHours)[1]  
  with     "100.0"  
');  
SELECT @myDoc;  
```  
  
 Учтите, что обновляемый адресат должен быть, самое большее, одним узлом, который явно указан в выражении пути путем добавления «[1]» в конце выражения.  
  
### <a name="b-using-the-if-expression-to-determine-replacement-value"></a>Б. Использование выражения «if» для определения замещающего значения  
 Можно указать **Если** выражение в Expression2 **заменить значение XML DML** инструкции, как показано в следующем примере. Expression1 определяет, что атрибут LaborHours первого рабочего центра должен быть обновлен. Expression2 использует **Если** выражение для определения нового значения атрибута LaborHours.  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<Root>  
<Location LocationID="10"   
            LaborHours=".1"  
            MachineHours=".2" >Manu steps are described here.  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
--SELECT @myDoc  
  
SET @myDoc.modify('  
  replace value of (/Root/Location[1]/@LaborHours)[1]  
  with (  
       if (count(/Root/Location[1]/step) > 3) then  
         "3.0"  
       else  
          "1.0"  
      )  
')  
SELECT @myDoc  
```  
  
### <a name="c-updating-xml-stored-in-an-untyped-xml-column"></a>В. Обновление XML, сохраненного в нетипизированном столбце XML  
 Следующий пример обновляет XML, сохраненный в столбце:  
  
```  
drop table T  
go  
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
-- verify the current <ProductDescription> element  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
-- update the ProductName attribute value  
UPDATE T  
SET x.modify('  
  replace value of (/Root/ProductDescription/@ProductName)[1]  
  with "New Road Bike" ')  
-- verify the update  
SELECT x.query(' /Root/ProductDescription')  
FROM T  
```  
  
### <a name="d-updating-xml-stored-in-a-typed-xml-column"></a>Г. Обновление XML, сохраненного в типизированном столбце XML  
 Этот пример заменяет значения в документе производственных команд, сохраненном в типизированном столбце XML.  
  
 В примере сначала создается таблица (T) с типизированным столбцом XML в базе данных AdventureWorks. Затем копируются производственные инструкции экземпляра XML из столбца Instructions в таблице ProductModel в таблицу T. После этого вставленные данные применяются к XML в таблице T.  
  
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
--insert a new location - <Location 1000/>.   
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
insert <MI:Location LocationID="1000"  LaborHours="1000"  LotSize="1000" >  
           <MI:step>Do something using <MI:tool>hammer</MI:tool></MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
go  
-- Now replace manu. tool in location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/MI:step/MI:tool)[1]   
  with   "screwdriver"  
')  
go  
select Instructions  
from T  
-- Now replace value of lot size  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  replace value of (/MI:root/MI:Location/@LotSize)[1]   
  with   500 cast as xs:decimal ?  
')  
go  
select Instructions  
from T  
```  
  
 Обратите внимание на использование **приведения** при замене значения LotSize. Это необходимо, когда значение должно иметь определенный тип. Если бы в этом примере значением было 500, явное приведение было бы не нужно.  
  
## <a name="see-also"></a>См. также  
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных &#40; Язык XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
