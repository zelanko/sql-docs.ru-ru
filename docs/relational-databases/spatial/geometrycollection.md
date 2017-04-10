---
title: "GeometryCollection | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GeomCollection, геометрический подтип [SQL Server]"
  - "geometry, подтипы [SQL Server]"
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# GeometryCollection
  Тип данных **GeometryCollection** представляет собой коллекцию экземпляров **geometry** или **geography** . Коллекция **GeometryCollection** может быть пустой.  
  
## Экземпляры GeometryCollection  
  
### Принимаемые экземпляры  
 Чтобы экземпляр **GeometryCollection** был принимаемым, он должен быть пустым экземпляром **GeometryCollection** или все экземпляры, составляющие экземпляр **GeometryCollection** , должны быть принимаемыми экземплярами. В следующем примере показаны принимаемые экземпляры.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 В следующем примере возникает исключение `System.FormatException`, так как экземпляр **LinesString** в экземпляре **GeometryCollection** не является принимаемым.  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### Допустимые экземпляры  
 Экземпляр **GeometryCollection** является допустимым, если допустимы все экземпляры, составляющие экземпляр **GeometryCollection** . В следующем примере показаны три допустимых экземпляра **GeometryCollection** и один недопустимый экземпляр.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` не является допустимым, так как экземпляр **Polygon** в экземпляре **GeometryCollection** не является допустимым.  
  
 Дополнительные сведения о принимаемых и допустимых экземплярах см. в разделах [Point](../../relational-databases/spatial/point.md), [MultiPoint](../../relational-databases/spatial/multipoint.md), [LineString](../../relational-databases/spatial/linestring.md), [MultiLineString](../../relational-databases/spatial/multilinestring.md), [Polygon](../../relational-databases/spatial/polygon.md)и [MultiPolygon](../../relational-databases/spatial/multipolygon.md).  
  
## Примеры  
 В следующем примере создается коллекция экземпляров `geometry``GeometryCollection` ; значения по оси Z в объекте с идентификатором SRID 1 содержат один экземпляр `Point` и один экземпляр `Polygon` .  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## См. также:  
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  