---
title: Запросы XQuery с использованием порядка | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- sequence [XQuery]
- XQuery, sequence
- ordered expressions [XQuery]
ms.assetid: 4f1266c5-93d7-402d-94ed-43f69494c04b
caps.latest.revision: 23
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 978e800ba5539878eb805c16f2460de3761dda59
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051682"
---
# <a name="xqueries-involving-order"></a>Запросы XQuery, использующие упорядочивание
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Реляционные базы данных не используют концепцию последовательности. Например, нельзя создать запрос типа «Получить первого заказчика из базы данных». Тем не менее, можно запрашивать XML-документа и получения первого \<клиента > элемента. Затем всегда будет появляться информация об этом же заказчике.  
  
 В этом подразделе описаны запросы, основанные на последовательности появления узлов в документе.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieve-manufacturing-steps-at-the-second-work-center-location-for-a-product"></a>A. Получить этапы производства на втором участке цеха по изготовлению продукта  
 Для определенной модели продукта следующий запрос извлекает этапы производства на втором участке цеха в последовательности участков цехов в производственном процессе.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    <ManuStep ProdModelID = "{sql:column("Production.ProductModel.ProductModelID")}"  
                ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
     <Location>  
       { (//AWMI:root/AWMI:Location)[2]/@* }  
       <Steps>  
         { for $s in (//AWMI:root/AWMI:Location)[2]//AWMI:step  
           return  
              <Step>  
               { string($s) }  
              </Step>  
         }  
        </Steps>  
      </Location>  
     </ManuStep>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Выражения в фигурных скобках заменяются результатом их оценки. Дополнительные сведения см. в разделе [конструкции XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md).  
  
-   **@\*** Извлекает все атрибуты второго участка производственного цеха.  
  
-   Итерация FLWOR (FOR ... RETURN) извлекает все дочерние элементы <`step`> второго участка производственного цеха.  
  
-   [Функция SQL: column() (XQuery)](../xquery/xquery-extension-functions-sql-column.md) включает реляционного значения в XML, который создается.  
  
 Результат:  
  
```  
<ManuStep ProdModelID="7" ProductModelName="HL Touring Frame">  
  <Location LocationID="20" SetupHours="0.15"   
              MachineHours="2"  LaborHours="1.75" LotSize="1">  
  <Steps>  
   <Step>Assemble all frame components following blueprint 1299.</Step>  
     …  
  </Steps>  
 </Location>  
</ManuStep>    
```  
  
 Предыдущий запрос извлекает только текстовые узлы. Если вы хотите, чтобы весь <`step`> элемент возвращается, вместо этого удалите **string()** функции из запроса:  
  
### <a name="b-find-all-the-material-and-tools-used-at-the-second-work-center-location-in-the-manufacturing-of-a-product"></a>Б. Найти все материалы и инструменты, используемые на втором участке цеха для производства продукта  
 Для определенной модели продукта следующий запрос извлекает инструменты и материалы, используемые на втором участке цеха в последовательности участков цехов в производственном процессе.  
  
```  
SELECT Instructions.query('  
    declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   <Location>  
      { (//AWMI:root/AWMI:Location)[1]/@* }  
       <Tools>  
         { for $s in (//AWMI:root/AWMI:Location)[1]//AWMI:step//AWMI:tool  
           return  
              <Tool>  
                { string($s) }  
              </Tool>  
          }  
        </Tools>  
        <Materials>  
            { for $s in (//AWMI:root/AWMI:Location)[1]//AWMI:step//AWMI:material  
              return  
                 <Material>  
                    { string($s) }  
                 </Material>  
             }  
         </Materials>  
  </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Запрос формирует < Loca`tion`> элемент и извлекает из базы данных значения его атрибутов.  
  
-   Запрос использует две итерации FLWOR (FOR...RETURN): одна необходима для получения инструментов, вторая — для получения используемых материалов.  
  
 Результат:  
  
```  
<Location LocationID="10" SetupHours=".5"   
          MachineHours="3" LaborHours="2.5" LotSize="100">  
  <Tools>  
    <Tool>T-85A framing tool</Tool>  
    <Tool>Trim Jig TJ-26</Tool>  
    <Tool>router with a carbide tip 15</Tool>  
    <Tool>Forming Tool FT-15</Tool>  
  </Tools>  
  <Materials>  
    <Material>aluminum sheet MS-2341</Material>  
  </Materials>  
</Location>  
```  
  
### <a name="c-retrieve-the-first-two-product-feature-descriptions-from-the-product-catalog"></a>В. Извлечь описания характеристик первых двух продуктов из каталога продуктов  
 Для определенной модели продукта запрос извлекает первые два описания характеристик из элемента <`Features`> в каталоге моделей продукта.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <ProductModel ProductModelID= "{ data( (/p1:ProductDescription/@ProductModelID)[1] ) }"  
                   ProductModelName = "{ data( (/p1:ProductDescription/@ProductModelName)[1] ) }" >  
       {  
         for $F in /p1:ProductDescription/p1:Features  
         return   
           $F/*[position() <= 2]   
       }  
     </ProductModel>  
      ') as x  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
 Текст запроса формирует XML, который включает элемент <`ProductModel`>, имеющий атрибуты ProductModelID и ProductModelName.  
  
-   Запрос использует цикл FOR ... RETURN для получения описаний характеристик моделей продуктов. **Position()** функция используется для получения первых двух характеристик.  
  
 Результат:  
  
```  
<ProductModel ProductModelID="19" ProductModelName="Mountain 100">  
 <p1:Warranty   
  xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
  <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
  <p1:Description>parts and labor</p1:Description>  
 </p1:Warranty>  
 <p2:Maintenance   
  xmlns:p2="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
  <p2:NoOfYears>10</p2:NoOfYears>  
  <p2:Description>maintenance contact available through your dealer   
            or any AdventureWorks retail store.  
  </p2:Description>  
 </p2:Maintenance>  
</ProductModel>   
```  
  
### <a name="d-find-the-first-two-tools-used-at-the-first-work-center-location-in-the-manufacturing-process-of-the-product"></a>Г. Найти первые два инструмента, используемые в производственном процессе на первом участке цеха  
 Для модели продукта этот запрос возвращает первые два инструмента, используемые на первом участке цеха в последовательности участков цехов в производственном процессе. Этот запрос указан для производственных инструкций, хранящихся в **инструкции** столбец **Production.ProductModel** таблицы.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   for $Inst in (//AWMI:root/AWMI:Location)[1]  
   return   
     <Location>  
       { $Inst/@* }  
       <Tools>  
         { for $s in ($Inst//AWMI:step//AWMI:tool)[position() <= 2]  
           return  
             <Tool>  
               { string($s) }  
             </Tool>  
         }  
       </Tools>  
     </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Результат:  
  
```  
<Location LocationID="10" SetupHours=".5"   
            MachineHours="3" LaborHours="2.5" LotSize="100">  
  <Tools>  
    <Tool>T-85A framing tool</Tool>  
    <Tool>Trim Jig TJ-26</Tool>  
  </Tools>  
</Location>   
```  
  
### <a name="e-find-the-last-two-manufacturing-steps-at-the-first-work-center-location-in-the-manufacturing-of-a-specific-product"></a>Д. Найти два последних этапа производства в изготовлении определенного продукта на первом участке цеха  
 В запросе используется **last()** функции для получения последних двух этапов производства.  
  
```  
SELECT Instructions.query('   
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  <LastTwoManuSteps>  
   <Last-1Step>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[(last()-1)]/text() }  
   </Last-1Step>  
   <LastStep>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[last()]/text() }  
   </LastStep>  
  </LastTwoManuSteps>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Результат:  
  
```  
<LastTwoManuSteps>  
   <Last-1Step>When finished, inspect the forms for defects per   
               Inspection Specification .</Last-1Step>  
   <LastStep>Remove the frames from the tool and place them in the   
             Completed or Rejected bin as appropriate.</LastStep>  
</LastTwoManuSteps>  
```  
  
## <a name="see-also"></a>См. также  
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)   
 [Построение XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)  
  
  
