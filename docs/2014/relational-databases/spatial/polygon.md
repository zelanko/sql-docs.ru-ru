---
title: Многоугольник | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 629dd979c00c9a40915c94c5bfe79d28b746f44a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238764"
---
# <a name="polygon"></a>Polygon
  Объект `Polygon` представляет собой двухмерную поверхность, хранимую в виде последовательности точек, определяющих внешнее ограничивающее кольцо и ноль или более внутренних колец.  
  
## <a name="polygon-instances"></a>Экземпляры многоугольников  
 Объект `Polygon` экземпляр должен быть сформирован на основе кольца, содержащего не менее трех уникальных точек. Объект `Polygon` экземпляр может быть пустым.  
  
 Внешнее и любое внутреннее кольца экземпляра `Polygon` определяют его границы. Пространство внутри колец определяет внутреннюю сторону экземпляра `Polygon`.  
  
 На рисунке ниже показаны примеры `Polygon` экземпляров.  
  
 ![Примеры геометрических экземпляров многоугольника](../../database-engine/media/polygon.gif "Примеры геометрических экземпляров многоугольника")  
  
 На рисунке представлены:  
  
1.  Рис. 1 приведен `Polygon` экземпляра, граница которого определяется внешним кольцом.  
  
2.  на рисунке 2 представлен экземпляр `Polygon`, граница которого определяется внешним и двумя внутренними кольцами. Область внутри внутренних колец является частью внешней стороны экземпляра `Polygon`;  
  
3.  на рисунке 3 представлен допустимый экземпляр `Polygon`, поскольку внутренние кольца пересекаются в одной точке касания.  
  
### <a name="accepted-instances"></a>Правильные экземпляры  
 Правильные экземпляры `Polygon` — это экземпляры, которые можно сохранить в переменной `geometry` или `geography`, не вызывая исключения. Принимаются следующие `Polygon` экземпляров:  
  
-   Пустой `Polygon` экземпляра  
  
-   Экземпляр `Polygon` с правильным внешним кольцом и с нулем или более корректных внутренних колец  
  
 Чтобы кольцо было правильным, должны выполняться следующие требования.  
  
-   `LineString` Экземпляр должен быть принят.  
  
-   Экземпляр `LineString` должен иметь не менее четырех точек.  
  
-   Начальная и конечная точки экземпляра `LineString` должны совпадать.  
  
 В следующем примере показаны принятые `Polygon` экземпляров.  
  
```  
DECLARE @g1 geometry = 'POLYGON EMPTY';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';  
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';  
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';  
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
```  
  
 Как `@g4` и `@g5` видно, что правильным `Polygon` экземпляра не может быть допустимым `Polygon` экземпляра. `@g5` также показывает, что экземпляр Polygon должен содержать только кольцо с любыми четырьмя точками.  
  
 Следующие примеры формируют исключение `System.FormatException`, так как экземпляры `Polygon` некорректны.  
  
```  
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';  
```  
  
 Экземпляр `@g1` не принимается, поскольку экземпляр `LineString` для внешнего кольца содержит недостаточное число точек. Экземпляр `@g2` не принимается, поскольку начальная точка внешнего кольца экземпляра `LineString` не совпадает с конечной точкой. В следующем примере внешнее кольцо корректно, а внутреннее — нет. Это также вызовет исключение `System.FormatException`.  
  
```  
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Внутренние кольца экземпляра `Polygon` могут соприкасаться как сами с собой и друг с другом в одной касательной точках, но если внутренние кольца экземпляра `Polygon` пересекаются, экземпляр недействителен.  
  
 В следующем примере показаны допустимые `Polygon` экземпляров.  
  
```  
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g3` является допустимым, так как два внутренних кольца соприкасаются в одной точке и не пересекаются. В следующем примере показаны недопустимые экземпляры `Polygon` .  
  
```  
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';  
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';  
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';  
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();  
```  
  
 `@g1` является недопустимым, поскольку внутреннее кольцо касается внешнего в двух местах. `@g2` является недопустимым, поскольку второе внутреннее кольцо находится внутри первого внутреннего кольца. `@g3` не допускается так как два внутренних кольца касаются в нескольких последовательных точках. `@g4` является недопустимым, поскольку внутренние области двух внутренних колец перекрываются. `@g5` является недопустимым, поскольку внешнее кольцо не является первым. `@g6` является недопустимым, поскольку кольцо не содержит хотя бы трех различных точек.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается простой экземпляр `geometry``Polygon` с отверстием и значением SRID, равным 10.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);  
```  
  
 Экземпляр, являющийся недопустимым, может быть введен и преобразован в допустимый экземпляр типа `geometry` . В следующем примере экземпляра `Polygon`внутреннее и внешнее кольца перекрещиваются, и экземпляр является недопустимым.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');  
```  
  
 В следующем примере недопустимый экземпляр преобразуется в допустимый с помощью метода `MakeValid()`.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.ToString();  
```  
  
 Экземпляром `geometry` , полученным в приведенном выше примере, является `MultiPolygon`.  
  
```  
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))  
```  
  
 Еще один пример преобразования недопустимого экземпляра в допустимый экземпляр geometry. В следующем примере создается экземпляр `Polygon` с тремя одинаковыми точками:  
  
```tsql  
DECLARE @g geometry  
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');  
SET @g = @g.MakeValid();  
SELECT @g.ToString()  
```  
  
 Экземпляр geometry, возвращаемый выше, — это `Point(1 3)`.  Если задан экземпляр `Polygon` `POLYGON((1 3, 1 5, 1 3, 1 3))` , функция `MakeValid()` вернет `LINESTRING(1 3, 1 5)`.  
  
## <a name="see-also"></a>См. также  
 [STArea (тип данных geometry)](/sql/t-sql/spatial-geometry/starea-geometry-data-type)   
 [STExteriorRing (тип данных geometry)](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)   
 [STNumInteriorRing (тип данных geometry)](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)   
 [STInteriorRingN (тип данных geometry)](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)   
 [STCentroid (тип данных geometry)](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)   
 [STPointOnSurface (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [MultiPolygon](../spatial/polygon.md)   
 [Пространственные данные (SQL Server)](../spatial/spatial-data-sql-server.md)   
 [STIsValid (тип данных geography)](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)   
 [STIsValid (тип данных geometry)](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
  
