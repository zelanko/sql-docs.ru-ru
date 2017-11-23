---
title: "STCentroid (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STCentroid_TSQL
- STCentroid (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STCentroid (geometry Data Type)
ms.assetid: 4dc5a004-7a53-4cce-81dd-9f5e1dd0db78
caps.latest.revision: "26"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 61bde787ab407107ed7747499024ed6d3f0a9c14
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stcentroid-geometry-data-type"></a>STCentroid (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает геометрический центр **geometry** экземпляр, который состоит из одного или нескольких многоугольников.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCentroid ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
 Открытый тип Geospatial Consortium (OGC): **точки**  
  
## <a name="remarks"></a>Замечания  
 `STCentroid()`Возвращает значение null, если **geometry** экземпляр не **Polygon, CurvePolygon**, или **MultiPolygon** типа.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-centroid-of-a-polygon-instance"></a>A. Вычисление центроида экземпляра объекта Polygon  
 В следующем примере используется `STCentroid()` для вычисления центроида экземпляра `polygon``geometry` экземпляр:  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STCentroid().ToString();  
```  
  
### <a name="b-computing-the-centroid-of-a-curvepolygon-instance"></a>Б. Вычисление центроида экземпляра объекта CurvePolygon  
 В следующем примере вычисляется центроид экземпляра `CurvePolygon`.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))';  
 SELECT @g.STCentroid().ToString() AS Centroid
 ```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

