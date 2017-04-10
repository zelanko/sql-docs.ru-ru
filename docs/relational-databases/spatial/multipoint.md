---
title: "MultiPoint | Microsoft Docs"
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
  - "MultiPoint, геометрический подтип [SQL Server]"
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MultiPoint
  Экземпляр **MultiPoint** представляет собой коллекцию точек. Граница у экземпляра **MultiPoint** отсутствует.  
  
## Примеры  
 В следующем примере создается экземпляр `geometry MultiPoint` со значением SRID, равным 23, и двумя точками, с координатами (2, 3) и (7, 8), и значением Z, равным 9,5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Данный экземпляр `MultiPoint` может быть также выражен посредством `STMPointFromText()`, как показано ниже.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 В следующем примере метод `STGeometryN()` используется с целью получения описания первой точки коллекции.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## См. также:  
 [Точка](../../relational-databases/spatial/point.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  