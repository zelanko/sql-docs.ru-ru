---
title: "MultiLineString | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MultiLineString, геометрический подтип [SQL Server]"
  - "geometry, подтипы [SQL Server]"
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# MultiLineString
  Тип данных **MultiLineString** представляет собой коллекцию экземпляров **geometry** или **geographyLineString**.  
  
## Экземпляры MultiLineString  
 На рисунке ниже приведены примеры экземпляров **MultiLineString** .  
  
 ![Примеры объектов MultiLineString типа geometry](../../relational-databases/spatial/media/multilinestring.png "Примеры объектов MultiLineString типа geometry")  
  
 На рисунке представлены:  
  
-   Изображение 1 представляет простой экземпляр **MultiLineString** , граница которого определяется четырьмя конечными точками двух его элементов **LineString** .  
  
-   Изображение 2 представляет простой экземпляр **MultiLineString** , поскольку пересекаются только конечные точки элементов **LineString** . Граница образована двумя неперекрывающимися конечными точками.  
  
-   Изображение 3 представляет непростой экземпляр **MultiLineString** , поскольку имеется пересечение внутренней части одного из элементов **LineString** этого экземпляра. Границей данного экземпляра **MultiLineString** являются четыре конечные точки.  
  
-   На рисунке 4 представлен отличный от простого незамкнутый экземпляр объекта **MultiLineString** .  
  
-   Изображение 5 представляет простой, незамкнутый экземпляр **MultiLineString**. Экземпляр является незамкнутым, поскольку незамкнуты его элементы **LineStrings** . Экземпляр является простым, поскольку внутренние стороны экземпляров **LineStrings** не пересекаются.  
  
-   Изображение 6 представляет простой, замкнутый экземпляр **MultiLineString** . Экземпляр является замкнутым, поскольку все его элементы замкнуты. Экземпляр является простым, поскольку внутренние области его элементов не пересекаются.  
  
### Правильные экземпляры  
 Чтобы экземпляр **MultiLineString** был принят, он должен либо быть пустым, либо содержать только принимаемые экземпляры **LineString** . Дополнительные сведения о принимаемых экземплярах **LineString** см. в разделе [LineString](../../relational-databases/spatial/linestring.md). В следующих примерах показаны принятые экземпляры **MultiLineString** .  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 Приведенный ниже пример вызывает исключение `System.FormatException`, так как второй экземпляр **LineString** недействителен.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### Допустимые экземпляры  
 Чтобы экземпляр **MultiLineString** был действителен, он должен соответствовать следующим критериям.  
  
1.  Все экземпляры, составляющие экземпляр **MultiLineString** , должны быть действительными экземплярами **LineString** .  
  
2.  Никакие два экземпляра **LineString** , составляющие экземпляр **MultiLineString** , не могут перекрывать сами себя на интервале. Экземпляры **LineString** могут взаимодействовать или соприкасаться только с собой или с другими экземплярами **LineString** в конечном числе точек.  
  
 В следующем примере показаны три действительных экземпляра **MultiLineString** и один экземпляр **MultiLineString** , который недействителен.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` является недопустимым, так как второй экземпляр **LineString** пересекается с первым экземпляром **LineString** в интервале. Они соприкасаются в бесконечном количестве точек.  
  
## Примеры  
 В следующем примере создается простой экземпляр `geometry``MultiLineString` , содержащий два элемента `LineString` со значением SRID 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 Чтобы создать экземпляр с другим значением SRID, используйте функции `STGeomFromText()` или `STMLineStringFromText()`. Можно также использовать функцию `Parse()`, а затем изменить SRID, как показано в следующем примере.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## См. также:  
 [STLength (тип данных geometry)](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STIsClosed (тип данных geometry)](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [LineString](../../relational-databases/spatial/linestring.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  