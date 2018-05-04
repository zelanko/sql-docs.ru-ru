---
title: Count, функция (XQuery) | Документы Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
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
- fn:count function
- count function [XQuery]
ms.assetid: a9f7131f-23e1-4d4d-a36c-180447543926
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a4736bae163e427d98c4c7e21f13cc957d91187f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions---count"></a>Агрегатные функции — count
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает количество элементов, содержащихся в последовательности, указываемой аргументом *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:count($arg as item()*) as xs:integer  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Подсчитываемые элементы.  
  
## <a name="remarks"></a>Замечания  
 Возвращает 0, если *$arg* представляет собой пустую последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-count-xquery-function-to-count-the-number-of-work-center-locations-in-the-manufacturing-of-a-product-model"></a>A. Использование функции XQuery count() для подсчета количества различных географических расположений цехов, участвующих в производстве определенной модели продукта  
 Следующий запрос подсчитывает количество цехов, участвующих в производстве продукта определенной модели (ProductModelID=7).  
  
```  
SELECT Production.ProductModel.ProductModelID,   
       Production.ProductModel.Name,   
       Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations>  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **Имен** ключевое слово в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен. Затем этот префикс используется в теле запроса XQuery.  
  
-   Запрос создает XML, включающий элемент <`NoOfWorkStations`>.  
  
-   **Count()** функционировать в теле запроса XQuery подсчитывает число <`Location`> элементов.  
  
 Результат:  
  
```  
ProductModelID   Name                 WorkCtrCount       
-------------- ---------------------------------------------------  
7             HL Touring Frame  <NoOfWorkStations>6</NoOfWorkStations>     
```  
  
 Можно также создать XML, включающий идентификатор и название модели продукта, как это показано в следующем запросе:  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations  
             ProductModelID= "{ sql:column("Production.ProductModel.ProductModelID") }"   
             ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID= 7  
```  
  
 Результат:  
  
```  
<NoOfWorkStations ProductModelID="7"   
                  ProductModelName="HL Touring Frame">6</NoOfWorkStations>  
```  
  
 Эти значения можно вернуть в формате, отличном от XML, как показано в следующем запросе. В запросе используется [метод value() (тип данных xml)](../t-sql/xml/value-method-xml-data-type.md) для получения количества цехов.  
  
```  
SELECT  ProductModelID,   
        Name,   
        Instructions.value('declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
           count(/AWMI:root/AWMI:Location)', 'int' ) as WorkCtrCount  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Результат:  
  
```  
ProductModelID    Name            WorkCtrCount  
-------------- ---------------------------------  
7              HL Touring Frame        6     
```  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
