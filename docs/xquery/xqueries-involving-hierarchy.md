---
title: Запросы XQuery использующие, включающая иерархию | Документация Майкрософт
description: Просмотрите примеры запросы XQuery использующие, которые используют иерархии.
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- hierarchies [XQuery]
- XQuery, hierarchies
ms.assetid: 6953d8b7-bad8-4b64-bf7b-12fa4f10f65c
author: rothja
ms.author: jroth
ms.openlocfilehash: c4ab17b99dc1d90d867689c5f79425fde0775a4b
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84880631"
---
# <a name="xqueries-involving-hierarchy"></a>Запросы XQuery, использующие иерархию
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Большинство столбцов типа **XML** в базе данных **AdventureWorks** являются частично структурированными документами. Поэтому документы, хранящиеся в каждой строке, могут выглядеть по-разному. Примеры запросов в этом подразделе показывают, как извлечь данные из этих различных документов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-from-the-manufacturing-instructions-documents-retrieve-work-center-locations-together-with-the-first-manufacturing-step-at-those-locations"></a>A. Получение сведений о размещении цехов и о первом этапе производства в этих цехах из документов инструкций производства  
 Для модели продукта 7 Запрос конструирует XML, включающий `ManuInstr` элемент <>, с атрибутами **ProductModelID** и **ProductModelName** и одним или несколькими <`Location`> дочерними элементами.  
  
 Каждый `Location` элемент> <имеет собственный набор атрибутов и один <`step`> дочерний элемент. Этот <`step`> дочерним элементом является первым шагом производства в расположении цеха.  
  
```sql
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
  
-   Ключевое слово **Namespace** в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен. Затем данный префикс используется в теле запроса.  
  
-   Токены переключения контекста, {) и (}, используются для переключения запроса из режима построения XML в режим вычисления.  
  
-   **SQL: column ()** используется для включения реляционного значения в создаваемый XML.  
  
-   При конструировании элемента <`Location`> $WC/@ * получает все атрибуты расположения рабочего центра.  
  
-   Функция **String ()** возвращает строковое значение из `step` элемента <>.  
  
 Частичный результат:  
  
```xml
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
 Следующий запрос получает дополнительные телефонные номера для конкретного контакта клиента, выполняя поиск элемента <> в всей иерархии `telephoneNumber` . Поскольку `telephoneNumber` элемент> <может находиться в любом месте иерархии, в запросе используется потомок и оператор Self (//).  
  
```sql
SELECT AdditionalContactInfo.query('  
 declare namespace ci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
 declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
for $ph in /ci:AdditionalContactInfo//act:telephoneNumber  
   return  
      $ph/act:number  
') as x  
FROM  Person.Contact  
WHERE ContactID = 1  
```  
  
 Результат:  
  
```xml
\<act:number   
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  111-111-1111  
\</act:number>  
\<act:number   
  xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  112-111-1111  
\</act:number>  
```  
  
 Чтобы получить только телефонные номера верхнего уровня, в частности <`telephoneNumber`> дочерние элементы <`AdditionalContactInfo`>, выражение for в запросе изменяется на  
  
 `for $ph in /ci:AdditionalContactInfo/act:telephoneNumber`.  
  
## <a name="see-also"></a>Дополнительно  
 [Основы XQuery](../xquery/xquery-basics.md)   
 [Создание XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)  
  
  
