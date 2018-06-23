---
title: MultiPolygon | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f1d29c76541d87e950c973fd6dc7d57482c6d2b2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095180"
---
# <a name="multipolygon"></a>MultiPolygon
  Объект `MultiPolygon` представляет собой коллекцию из нуля или более `Polygon` экземпляров.  
  
## <a name="polygon-instances"></a>Экземпляры многоугольников  
 На рисунке ниже показаны примеры `MultiPolygon` экземпляров.  
  
 ![Примеры геометрических экземпляров MultiPolygon](../../database-engine/media/multipolygon.gif "Примеры геометрических экземпляров MultiPolygon")  
  
 На рисунке представлены:  
  
-   На рисунке 1 представлена `MultiPolygon` с двумя `Polygon` элементов. Граница определяется двумя внешними кольцами и тремя внутренними кольцами.  
  
-   2 — экземпляр типа `MultiPolygon` с двумя элементами `Polygon`. Граница определяется двумя внешними кольцами и тремя внутренними кольцами. Два элемента `Polygon` пересекаются в точке касания.  
  
### <a name="accepted-instances"></a>Принимаемые экземпляры  
 Объект `MultiPolygon` является правильным, будет выполнено одно из следующих условий.  
  
-   Это пустой `MultiPolygon` экземпляра.  
  
-   Все экземпляры, составляющие `MultiPolygon` принимаются экземпляр `Polygon` экземпляров. Дополнительные сведения о принимаемых `Polygon` экземпляры, в разделе [многоугольника](../spatial/polygon.md).  
  
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
  
1.  Все экземпляры, составляющие экземпляр `MultiPolygon`, являются допустимыми экземплярами `Polygon`. Для допустимых `Polygon` экземпляры, в разделе [многоугольника](../spatial/polygon.md).  
  
2.  Никакие экземпляры `Polygon`, составляющие экземпляр `MultiPolygon`, не перекрываются.  
  
 В следующем примере показаны два допустимых экземпляра `MultiPolygon` и один недопустимый экземпляр `MultiPolygon`.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g2` является допустимым из-за двух `Polygon` экземпляры имеют только общую точку касания. `@g3` не является допустимым поскольку внутренние области двух `Polygon` экземпляров пересекаться друг с другом.  
  
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
  
  
