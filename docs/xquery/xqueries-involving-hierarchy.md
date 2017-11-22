---
title: "Запросы XQuery, использующие иерархию | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- hierarchies [XQuery]
- XQuery, hierarchies
ms.assetid: 6953d8b7-bad8-4b64-bf7b-12fa4f10f65c
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e27b8715a426ce4ad2b19fa10a0172a48b8ec67c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="xqueries-involving-hierarchy"></a>Запросы XQuery, использующие иерархию
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Большинство **xml** -столбцов в **AdventureWorks** базы данных представляют собой полуструктурированные документы. Поэтому документы, хранящиеся в каждой строке, могут выглядеть по-разному. Примеры запросов в этом подразделе показывают, как извлечь данные из этих различных документов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-from-the-manufacturing-instructions-documents-retrieve-work-center-locations-together-with-the-first-manufacturing-step-at-those-locations"></a>A. Получение сведений о размещении цехов и о первом этапе производства в этих цехах из документов инструкций производства  
 Для модели продукта 7 запрос создает XML, включающий <`ManuInstr`> элемент, с **ProductModelID** и **ProductModelName** атрибутов и один или несколько <`Location`> дочерние элементы.  
  
 Каждый элемент <`Location`> имеет свой собственный набор атрибутов и один дочерний элемент <`step`>. Этот дочерний элемент <`step`> соответствует первому этапу производства в данном цехе:  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   \<ManuInstr  ProdModelID = "{sql:column("Production.ProductModel.ProductModelID") }"   
                ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
            {   
              for $wc in //AWMI:root/AWMI:Location  
              return  
                <Location>  
                 {$wc/@* }  
                 <step1> { string( ($wc//AWMI:step)[1] ) } </step1>  
                </Location>  
            }  
          </ManuInstr>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **Имен** ключевое слово в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен. Затем данный префикс используется в теле запроса.  
  
-   Токены переключения контекста, {) и (}, используются для переключения запроса из режима построения XML в режим вычисления.  
  
-   **SQL: column()** используется для включения реляционного значения в XML, который создается.  
  
-   При формировании элемента <`Location`>, $wc/@* возвращает все атрибуты размещения цехов.  
  
-   **String()** функция возвращает строковое значение из <`step`> элемент.  
  
 Частичный результат:  
  
```  
<ManuInstr ProdModelID="7" ProductModelName="HL Touring Frame">  
   <Location LocationID="10" SetupHours="0.5"   
            MachineHours="3" LaborHours="2.5" LotSize="100">  
     <step1>Insert aluminum sheet MS-2341 into the T-85A   
             framing tool.</step1>  
   </Location>  
   <Location LocationID="20" SetupHours="0.15"   
            MachineHours="2" LaborHours="1.75" LotSize="1">  
      <step1>Assemble all frame components following   
             blueprint 1299.</step1>  
   </Location>  
...  
</ManuInstr>   
```  
  
### <a name="b-find-all-telephone-numbers-in-the-additionalcontactinfo-column"></a>Б. Поиск всех телефонных номеров в столбце AdditionalContactInfo  
 Следующий запрос возвращает дополнительные телефонные номера заказчиков поиском по всей иерархии элемента <`telephoneNumber`>. Поскольку элемент <`telephoneNumber`> может находиться в любом месте иерархии, запрос использует нисходящий поиск от корня иерархии (//):  
  
```  
SELECT AdditionalContactInfo.query('  
 declare namespace ci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
 declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
for $ph in /ci:AdditionalContactInfo//act:telephoneNumber  
   return  
      $ph/act:number  
') as x  
FROM  Person.Contact  
WHERE ContactID = 1  
```  
  
 Результат:  
  
```  
\<act:number   
  xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  111-111-1111  
\</act:number>  
\<act:number   
  xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  112-111-1111  
\</act:number>  
```  
  
 Чтобы получить телефонные номера только верхнего уровня (дочерние элементы <`telephoneNumber`> элемента <`AdditionalContactInfo`>), следует изменить выражение FOR в запросе на:  
  
 `for $ph in /ci:AdditionalContactInfo/act:telephoneNumber`.  
  
## <a name="see-also"></a>См. также:  
 [Основы языка XQuery](../xquery/xquery-basics.md)   
 [Построение XML &#40; XQuery &#41;](../xquery/xml-construction-xquery.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)  
  
  
