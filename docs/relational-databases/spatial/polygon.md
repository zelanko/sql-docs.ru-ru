---
title: Многоугольник | Документация Майкрософт
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a82789da3207fc42a820a18ff6d7da438f84cdd7
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026144"
---
# <a name="polygon"></a>Polygon

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  **Polygon** представляет собой двухмерную поверхность, хранимую в виде последовательности точек, определяющих внешнее ограничивающее кольцо, и внутренних колец (последние могут отсутствовать).  
  
## <a name="polygon-instances"></a>Экземпляры многоугольников  
 Каждый экземпляр **Polygon** должен быть сформирован на основе кольца, содержащего не менее трех уникальных точек. Экземпляр **Polygon** может быть пустым.  
  
Внешнее и любое внутреннее кольца экземпляра **Polygon** определяют его границы. Пространство внутри колец определяет внутреннюю сторону экземпляра **Polygon**.  
  
На рисунке ниже приведены примеры экземпляров **Polygon** .  
  
 ![Примеры геометрических экземпляров многоугольника](../../relational-databases/spatial/media/polygon.gif "Примеры геометрических экземпляров многоугольника")  
  
На рисунке представлены:  
  
1.  на рисунке 1 представлен экземпляр **Polygon** , граница которого определяется внешним кольцом;  
  
2.  на рисунке 2 представлен экземпляр **Polygon** , граница которого определяется внешним и двумя внутренними кольцами. Область внутри внутренних колец является частью внешней стороны экземпляра **Polygon** ;  
  
3.  на рисунке 3 представлен допустимый экземпляр **Polygon** , поскольку внутренние кольца пересекаются в одной точке касания.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

### <a name="accepted-instances"></a>Правильные экземпляры  
 Правильные экземпляры **Polygon** — это экземпляры, которые можно сохранить в переменной **geometry** или **geography** , не вызывая исключения. Следующие экземпляры **Polygon** являются правильными:  
  
-   Пустой экземпляр **Polygon**  
-   Экземпляр **Polygon** с допустимым внешним кольцом (**LineString**) и с нулем или большим количеством допустимых внутренних колец (**LineString**s).  
  
Чтобы кольцо (**LineString**) было допустимым, должны выполняться следующие требования.  
  
-   Экземпляр **LineString** должен быть принят.  
-   Экземпляр **LineString** должен иметь не менее четырех точек.  
-   Начальная и конечная точки экземпляра **LineString** должны совпадать.  
  
В следующем примере показаны принятые экземпляры **Polygon** .  
  
```sql  
DECLARE @g1 geometry = 'POLYGON EMPTY';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';  
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';  
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';  
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
```  
  
На примере `@g4` и `@g5` видно, что может приниматься экземпляр **Polygon** , который не является допустимым экземпляром **Polygon** . `@g5` также показывает, что экземпляр Polygon должен содержать только кольцо с любыми четырьмя точками.  
  
Следующие примеры формируют исключение `System.FormatException` , так как экземпляры **Polygon** некорректны.  
  
```sql  
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';  
```  
  
`@g1` не принимается, поскольку экземпляр **LineString** для внешнего кольца содержит недостаточное число точек. `@g2` не принимается, поскольку начальная точка внешнего кольца экземпляра **LineString** не совпадает с конечной точкой. В следующем примере внешнее кольцо корректно, а внутреннее — нет. Это также вызовет исключение `System.FormatException`.  
  
```sql  
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Внутренние кольца экземпляра **Polygon** могут соприкасаться как сами с собой, так и друг с другом в точках одной касательной, но если внутренние кольца экземпляра **Polygon** пересекаются, экземпляр недействителен.  
  
 В следующем примере показаны допустимые экземпляры **Polygon** .  
  
```sql  
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g3` является допустимым, так как два внутренних кольца соприкасаются в одной точке и не пересекаются. В следующем примере показаны недопустимые экземпляры `Polygon` .  
  
```sql   
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';  
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';  
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';  
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();  
```  
  
 `@g1` является недопустимым, поскольку внутреннее кольцо касается внешнего в двух местах. `@g2` является недопустимым, поскольку второе внутреннее кольцо находится внутри первого внутреннего кольца. `@g3` является недопустимым, поскольку два внутренних кольца касаются в нескольких последовательных точках. `@g4` является недопустимым, поскольку внутренние области двух внутренних колец перекрываются. `@g5` является недопустимым, поскольку внешнее кольцо не является первым. `@g6` является недопустимым, поскольку кольцо не содержит хотя бы трех различных точек.  
  
## <a name="examples"></a>Примеры  
### <a name="example-a"></a>Пример А.  
В следующем примере создается простой экземпляр `geometry` `Polygon` с gap и SRID 10.
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STPolyFromText(
    'POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))',
    10);
```  
  

### <a name="example-b"></a>Пример Б.   
Недопустимый экземпляр можно ввести и преобразовать в допустимый экземпляр типа `geometry`. В следующем примере экземпляра `Polygon`внутреннее и внешнее кольца перекрещиваются, и экземпляр является недопустимым.  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse(
    'POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))'
    );  
```  
  
### <a name="example-c"></a>Пример В.  
В следующем примере недопустимый экземпляр преобразуется в допустимый с помощью метода `MakeValid()`.  
  
```sql  
SET @g = @g.MakeValid();  
SELECT @g.ToString();  
```  
  
Экземпляром `geometry` , полученным в приведенном выше примере, является `MultiPolygon`.  
  
```sql  
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)),
              ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))
```  
  
### <a name="example-d"></a>Пример Г.  
Это еще один пример преобразования недопустимого экземпляра в допустимый экземпляр geometry. В следующем примере создается экземпляр `Polygon` с тремя одинаковыми точками:  
  
```sql  
DECLARE @g geometry  
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');  
SET @g = @g.MakeValid();  
SELECT @g.ToString()  
```  
  
Экземпляр geometry, возвращаемый выше, — это `Point(1 3)`.  Если задан экземпляр `Polygon` `POLYGON((1 3, 1 5, 1 3, 1 3))` , функция `MakeValid()` вернет `LINESTRING(1 3, 1 5)`.  
  
## <a name="see-also"></a>См. также:  
 [STArea (тип данных geometry)](../../t-sql/spatial-geometry/starea-geometry-data-type.md)   
 [STExteriorRing (тип данных geometry)](../../t-sql/spatial-geometry/stexteriorring-geometry-data-type.md)   
 [STNumInteriorRing (тип данных geometry)](../../t-sql/spatial-geometry/stnuminteriorring-geometry-data-type.md)   
 [STInteriorRingN (тип данных geometry)](../../t-sql/spatial-geometry/stinteriorringn-geometry-data-type.md)   
 [STCentroid (тип данных geometry)](../../t-sql/spatial-geometry/stcentroid-geometry-data-type.md)   
 [STPointOnSurface (тип данных geometry)](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)   
 [MultiPolygon](../../relational-databases/spatial/multipolygon.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [STIsValid (тип данных geography)](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)   
 [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
  
