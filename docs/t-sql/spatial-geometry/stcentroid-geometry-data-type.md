---
title: STCentroid (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCentroid_TSQL
- STCentroid (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STCentroid (geometry Data Type)
ms.assetid: 4dc5a004-7a53-4cce-81dd-9f5e1dd0db78
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 3693c6a80c6482ec6677a21983f53d338da500f9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939059"
---
# <a name="stcentroid-geometry-data-type"></a>STCentroid (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает геометрический центр экземпляра **geometry**, состоящего из одного или нескольких многоугольников.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCentroid ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
 Тип OGC (открытый геопространственный консорциум): **Point**  
  
## <a name="remarks"></a>Remarks  
 `STCentroid()` возвращает значение NULL, если экземпляр **geometry** не относится к типу **Polygon, CurvePolygon** или **MultiPolygon**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-centroid-of-a-polygon-instance"></a>A. Вычисление центроида экземпляра объекта Polygon  
 В приведенном ниже примере метод `STCentroid()` используется для вычисления центроида экземпляра `polygon``geometry`.  
  
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
  
  

