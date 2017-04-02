---
title: "Точка | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Point, геометрический подтип [SQL Server]"
  - "тип данных geometry [SQL Server], пространственные данные"
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Точка
  В пространственных данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляр **Point** является объектом без измерения, представляющим отдельное месторасположение, и может содержать значения Z (уровень) и M (мера).  
  
## Тип данных Geography  
 Тип Point для типа данных geography представляет единичное расположение, где *Lat* представляет широту, а *Long* — долготу. Значения широты и долготы измеряются в градусах. Значения широты всегда находятся в интервале [-90, 90]. Все значения, находящиеся вне этого диапазона, вызывают исключение. Значения долготы всегда находятся в интервале [-180, 180]. Все значения, находящиеся вне этого диапазона, преобразуются в соответствующие значения в его пределах. Например, если введено значение долготы 190, то оно будет преобразовано в значение -170. *SRID* представляет идентификатор пространственной ссылки экземпляра **geography** , который необходимо вернуть.  
  
## Тип данных Geometry  
 Тип элемента для геометрических типов данных представляет собой единое место, где *X* представляет координату x создаваемого экземпляра Point, а *Y* — координату Y создаваемого экземпляра Point. *SRID* представляет идентификатор пространственной ссылки экземпляра **geometry** , который необходимо вернуть.  
  
## Примеры  
 В следующем примере показано создание экземпляра `geometry Point`, представляющего точку (3, 4) со значением SRID, равным 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 В следующем примере показано создание экземпляра `geometry``Point`, представляющего точку (3, 4) со значениями Z (уровень) и M (мера), равными соответственно 7 и 2,5, и значением SRID по умолчанию, равным 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 В последнем примере возвращаются значения X, Y, Z и M для экземпляра `geometry``Point` .  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 Для Z и M может быть явно указано значение NULL, как показано в следующем примере.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## См. также:  
 [MultiPoint](../../relational-databases/spatial/multipoint.md)   
 [STX (тип данных geometry)](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY (тип данных geometry)](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  