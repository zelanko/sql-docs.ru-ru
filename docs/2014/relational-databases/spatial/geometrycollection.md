---
title: GeometryCollection | Документация Майкрософт
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 5aceabe5a263cfa53572be6f818ddc905f9742a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66014232"
---
# <a name="geometrycollection"></a>GeometryCollection
  Тип данных `GeometryCollection` представляет собой коллекцию экземпляров `geometry` или `geography`. Коллекция `GeometryCollection` может быть пустой.  
  
## <a name="geometrycollection-instances"></a>Экземпляры GeometryCollection  
  
### <a name="accepted-instances"></a>Принимаемые экземпляры  
 Чтобы экземпляр `GeometryCollection` был принимаемым, он должен быть пустым экземпляром `GeometryCollection` или все экземпляры, составляющие экземпляр `GeometryCollection`, должны быть принимаемыми экземплярами. В следующем примере показаны принимаемые экземпляры.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 В следующем примере возникает исключение `System.FormatException`, так как экземпляр `LinesString` в экземпляре `GeometryCollection` не является принимаемым.  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Экземпляр `GeometryCollection` является допустимым, если допустимы все экземпляры, составляющие экземпляр `GeometryCollection`. В следующем примере показаны три допустимых экземпляра `GeometryCollection` и один недопустимый экземпляр.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` не является допустимым, так как экземпляр `Polygon` в экземпляре `GeometryCollection` не является допустимым.  
  
 Дополнительные сведения о принимаемых и допустимых экземплярах см. в разделах [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [Polygon](polygon.md)и [MultiPolygon](multipolygon.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается коллекция экземпляров `geometry``GeometryCollection` ; значения по оси Z в объекте с идентификатором SRID 1 содержат один экземпляр `Point` и один экземпляр `Polygon` .  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a>См. также  
 [Пространственные данные (SQL Server)](spatial-data-sql-server.md)  
  
  
