---
title: MultiPolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d941425b1faa2fcbc23b48555dce12846a7fd52e
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018989"
---
# <a name="multipolygon"></a>MultiPolygon
  Экземпляр `MultiPolygon` представляет собой коллекцию экземпляров `Polygon`.  
  
## <a name="polygon-instances"></a>Экземпляры многоугольников  
 На рисунке ниже приведены примеры экземпляров `MultiPolygon`.  
  
 ![Примеры геометрических экземпляров MultiPolygon](../../database-engine/media/multipolygon.gif "Примеры геометрических экземпляров MultiPolygon")  
  
 На рисунке представлены:  
  
-   1 — экземпляр типа `MultiPolygon` с двумя элементами `Polygon`. Граница определяется двумя внешними кольцами и тремя внутренними кольцами.  
  
-   2 — экземпляр типа `MultiPolygon` с двумя элементами `Polygon`. Граница определяется двумя внешними кольцами и тремя внутренними кольцами. Два элемента `Polygon` пересекаются в точке касания.  
  
### <a name="accepted-instances"></a>Принимаемые экземпляры  
 Экземпляр `MultiPolygon` является принимаемым, если истинно одно из следующих условий.  
  
-   Это пустой экземпляр `MultiPolygon`.  
  
-   Все экземпляры, составляющие экземпляр `MultiPolygon`, являются принимаемыми экземплярами `Polygon`. Дополнительные сведения о принимаемых `Polygon` экземпляров, см. в разделе [многоугольника](../spatial/polygon.md).  
  
 В следующих примерах показаны принимаемые экземпляры `MultiPolygon`.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
 В следующем примере показан экземпляр MultiPolygon, который вызывает исключение `System.FormatException`.  
  
```  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
 Второй экземпляр в MultiPolygon — это экземпляр LineString, не является принимаемым экземпляром Polygon.  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Экземпляр `MultiPolygon` является допустимым, если это пустой экземпляр `MultiPolygon` или удовлетворяет следующим требованиям.  
  
1.  Все экземпляры, составляющие экземпляр `MultiPolygon`, являются допустимыми экземплярами `Polygon`. Для допустимых `Polygon` экземпляров, см. в разделе [многоугольника](../spatial/polygon.md).  
  
2.  Никакие экземпляры `Polygon`, составляющие экземпляр `MultiPolygon`, не перекрываются.  
  
 В следующем примере показаны два допустимых экземпляра `MultiPolygon` и один недопустимый экземпляр `MultiPolygon`.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 Объект `@g2` допустим, поскольку два экземпляра `Polygon` имеют только общую точку касания. Объект `@g3` недопустим, поскольку внутренние области экземпляров `Polygon` перекрываются.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует создание экземпляра `geometry``MultiPolygon` и возвращает второй компонент в формате Well-Known Text (WKT).  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
 В данном примере создается пустой экземпляр `MultiPolygon` .  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## <a name="see-also"></a>См. также  
 [Polygon](../spatial/polygon.md)   
 [STArea (тип данных geometry)](/sql/t-sql/spatial-geometry/starea-geometry-data-type)   
 [STCentroid (тип данных geometry)](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)   
 [STPointOnSurface (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [Пространственные данные (SQL Server)](../spatial/spatial-data-sql-server.md)  
  
  
