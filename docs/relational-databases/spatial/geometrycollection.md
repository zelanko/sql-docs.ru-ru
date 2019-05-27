---
title: GeometryCollection | Документация Майкрософт
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0f50e5e1aea75e0b079f1933bbdd949d934ccbff
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65935210"
---
# <a name="geometrycollection"></a>GeometryCollection
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Тип данных **GeometryCollection** представляет собой коллекцию экземпляров **geometry** или **geography** . Коллекция **GeometryCollection** может быть пустой.  
  
## <a name="geometrycollection-instances"></a>Экземпляры GeometryCollection  
  
### <a name="accepted-instances"></a>Принимаемые экземпляры  
 Чтобы экземпляр **GeometryCollection** был принимаемым, он должен быть пустым экземпляром **GeometryCollection** или все экземпляры, составляющие экземпляр **GeometryCollection** , должны быть принимаемыми экземплярами. В следующем примере показаны принимаемые экземпляры.  
  
```sql  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 В следующем примере возникает исключение `System.FormatException` , так как экземпляр **LinesString** в экземпляре **GeometryCollection** не является принимаемым.  
  
```sql  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Экземпляр **GeometryCollection** является допустимым, если допустимы все экземпляры, составляющие экземпляр **GeometryCollection** . В следующем примере показаны три допустимых экземпляра **GeometryCollection** и один недопустимый экземпляр.  
  
```sql  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` не является допустимым, так как экземпляр **Polygon** в экземпляре **GeometryCollection** не является допустимым.  
  
 Дополнительные сведения о принимаемых и допустимых экземплярах см. в разделах [Point](../../relational-databases/spatial/point.md), [MultiPoint](../../relational-databases/spatial/multipoint.md), [LineString](../../relational-databases/spatial/linestring.md), [MultiLineString](../../relational-databases/spatial/multilinestring.md), [Polygon](../../relational-databases/spatial/polygon.md)и [MultiPolygon](../../relational-databases/spatial/multipolygon.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается коллекция экземпляров `geometry``GeometryCollection` ; значения по оси Z в объекте с идентификатором SRID 1 содержат один экземпляр `Point` и один экземпляр `Polygon` .  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a>См. также:  
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
