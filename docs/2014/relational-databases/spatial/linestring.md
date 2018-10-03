---
title: LineString | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
helpviewer_keywords:
- LineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: e50d0b86-8b31-4285-be71-ad05c7712cbd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b03537992a8f6c63c36ffb079f661aee171439be
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059754"
---
# <a name="linestring"></a>LineString
  `LineString` является одномерным объектом, представляющим последовательность точек и соединяющих их линейных сегментов.  
  
## <a name="linestring-instances"></a>Экземпляры LineString  
 На рисунке ниже показаны примеры `LineString` экземпляров.  
  
 ![Примеры геометрических экземпляров LineString](../../database-engine/media/linestring.gif "Примеры геометрических экземпляров LineString")  
  
 На рисунке представлены:  
  
-   на рисунке 1 представлен простой незамкнутый экземпляр объекта `LineString`;  
  
-   На рисунке 2 представлен отличный от простого незамкнутый `LineString` экземпляра.  
  
-   на рисунке 3 продемонстрирован простой замкнутый экземпляр объекта `LineString`, представляющий собой кольцо;  
  
-   на рисунке 4 продемонстрирован замкнутый непростой экземпляр объекта `LineString`, не являющийся кольцом.  
  
### <a name="accepted-instances"></a>Принимаемые экземпляры  
 Принятые экземпляры `LineString` могут быть введены в переменную геометрии, но они могут быть недействительными экземплярами `LineString`. Для принятия экземпляра `LineString` должны соблюдаться следующие критерии. Экземпляр должен быть сформирован по меньшей мере двумя точками или же должен быть пустым. Следующие экземпляры LineString допустимы.  
  
```  
DECLARE @g1 geometry = 'LINESTRING EMPTY';  
DECLARE @g2 geometry = 'LINESTRING(1 1,2 3,4 8, -6 3)';  
DECLARE @g3 geometry = 'LINESTRING(1 1, 1 1)';  
```  
  
 `@g3` показывает, что, хотя экземпляр `LineString` допустим, он недействителен.  
  
 Следующие `LineString` не является принимаемым. Он выдаст исключение `System.FormatException`.  
  
```  
DECLARE @g geometry = 'LINESTRING(1 1)';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Для `LineString` экземпляр был допустимым, он должен удовлетворять следующим условиям.  
  
1.  `LineString` Экземпляр должен быть принят.  
  
2.  Если экземпляр `LineString` не является пустым, он должен содержать по меньшей мере две различные точки.  
  
3.  `LineString` Экземпляра не может перекрывать сам себя на интервале из двух или более последовательных точек.  
  
 Следующие экземпляры `LineString` являются действительными.  
  
```  
DECLARE @g1 geometry= 'LINESTRING EMPTY';  
DECLARE @g2 geometry= 'LINESTRING(1 1, 3 3)';  
DECLARE @g3 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0)';  
DECLARE @g4 geometry= 'LINESTRING(1 1, 3 3, 2 4, 2 0, 1 1)';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
  
```  
  
 Следующие `LineString` экземпляры являются недопустимыми.  
  
```  
DECLARE @g1 geometry = 'LINESTRING(1 4, 3 4, 2 4, 2 0)';  
DECLARE @g2 geometry = 'LINESTRING(1 1, 1 1)';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
> [!WARNING]  
>  Определение пересечений `LineString` основано на расчетах с плавающей запятой, которые не являются точными.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как создать экземпляр `geometry``LineString` с тремя точками и значением SRID, равным 0:  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(1 1, 2 4, 3 9)', 0);  
```  
  
 Каждая точка экземпляра `LineString` может содержать значения Z (уровень) и M (мера). В данном примере значения М добавляются к экземпляру `LineString` , созданному в примере выше. M и Z могут принимать значения NULL.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(1 1 NULL 0, 2 4 NULL 12.3, 3 9 NULL 24.5)', 0);  
```  
  
 В следующем примере показано, как создать экземпляр `geometry LineString` с двумя одинаковыми точками. Вызов `IsValid` указывает, что экземпляр `LineString` не является действительным, а вызов `MakeValid` преобразует экземпляр `LineString` в `Point`.  
  
```tsql  
DECLARE @g geometry  
SET @g = geometry::STGeomFromText('LINESTRING(1 3, 1 3)',0);  
IF @g.STIsValid() = 1  
  BEGIN  
     SELECT @g.ToString() + ' is a valid LineString.';    
  END  
ELSE  
  BEGIN  
     SELECT @g.ToString() + ' is not a valid LineString.';  
     SET @g = @g.MakeValid();  
     SELECT @g.ToString() + ' is a valid Point.';    
  END  
  
```  
  
 Вышеприведенный фрагмент кода вернет следующее:  
  
```  
LINESTRING(1 3, 1 3) is not a valid LineString  
POINT(1 3) is a valid Point.  
```  
  
## <a name="see-also"></a>См. также  
 [STLength (тип данных geometry)](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint (тип данных geometry)](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint (тип данных geometry)](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [STPointN (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)   
 [STNumPoints (тип данных geometry)](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)   
 [STIsRing (тип данных geometry)](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)   
 [STIsClosed (тип данных geometry)](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [STPointOnSurface (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [Пространственные данные (SQL Server)](../spatial/spatial-data-sql-server.md)  
  
  
