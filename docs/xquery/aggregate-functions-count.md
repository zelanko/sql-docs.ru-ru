---
title: Count, функция (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:count function
- count function [XQuery]
ms.assetid: a9f7131f-23e1-4d4d-a36c-180447543926
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 30ec1817d4f22ff8ee23746f925943397981382f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046927"
---
# <a name="aggregate-functions---count"></a>Агрегатные функции — count
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает количество элементов, содержащихся в последовательности, указываемой аргументом *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:count($arg as item()*) as xs:integer  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Подсчитываемые элементы.  
  
## <a name="remarks"></a>Примечания  
 Возвращает 0, если *$arg* представляет собой пустую последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-using-the-count-xquery-function-to-count-the-number-of-work-center-locations-in-the-manufacturing-of-a-product-model"></a>A. Использование функции XQuery count() для подсчета количества различных географических расположений цехов, участвующих в производстве определенной модели продукта  
 Следующий запрос подсчитывает количество цехов, участвующих в производстве продукта определенной модели (ProductModelID=7).  
  
```  
SELECT Production.ProductModel.ProductModelID,   
       Production.ProductModel.Name,   
       Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations>  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   **Пространства имен** ключевое слово в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен. Затем этот префикс используется в теле запроса XQuery.  
  
-   Запрос создает XML, включающий <`NoOfWorkStations`> элемента.  
  
-   **Count()** работать в теле запроса XQuery подсчитывает количество <`Location`> элементы.  
  
 Это результат:  
  
```  
ProductModelID   Name                 WorkCtrCount       
-------------- ---------------------------------------------------  
7             HL Touring Frame  <NoOfWorkStations>6</NoOfWorkStations>     
```  
  
 Можно также создать XML, включающий идентификатор и название модели продукта, как это показано в следующем запросе:  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
       <NoOfWorkStations  
             ProductModelID= "{ sql:column("Production.ProductModel.ProductModelID") }"   
             ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >  
          { count(/AWMI:root/AWMI:Location) }  
       </NoOfWorkStations>  
') as WorkCtrCount  
FROM Production.ProductModel  
WHERE Production.ProductModel.ProductModelID= 7  
```  
  
 Это результат:  
  
```  
<NoOfWorkStations ProductModelID="7"   
                  ProductModelName="HL Touring Frame">6</NoOfWorkStations>  
```  
  
 Эти значения можно вернуть в формате, отличном от XML, как показано в следующем запросе. В запросе используется [метод value() (тип данных xml)](../t-sql/xml/value-method-xml-data-type.md) для получения количества цехов.  
  
```  
SELECT  ProductModelID,   
        Name,   
        Instructions.value('declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
           count(/AWMI:root/AWMI:Location)', 'int' ) as WorkCtrCount  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Это результат:  
  
```  
ProductModelID    Name            WorkCtrCount  
-------------- ---------------------------------  
7              HL Touring Frame        6     
```  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
