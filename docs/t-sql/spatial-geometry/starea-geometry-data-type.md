---
title: "STArea (тип данных geometry) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STArea (geometry Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea (geometry Data Type)
ms.assetid: a7dd6083-c649-4ac3-885d-1234e0db62f1
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87325f0124b52f6b77c9b62d67b1eec6915afbbb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="starea-geometry-data-type"></a>STArea (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает общую площадь поверхности экземпляра **geometry**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип возвращаемых данных CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Метод `STArea()` возвращает значение 0, если экземпляр **geometry** содержит только объекты размерности 0 и 1 либо является пустым. Метод `STArea()` возвращает значение **NULL**, если экземпляр **geometry** не инициализирован.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-area-of-a-polygon-instance"></a>A. Вычисление площади экземпляра объекта Polygon  
 В следующем примере создается экземпляр `Polygon``geometry` и вычисляется площадь многоугольника.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STArea();  
```  
  
### <a name="b-computing-the-area-of-a-curvepolygon-instance"></a>Б. Вычисление площади экземпляра объекта CurvePolygon  
 В следующем примере вычисляется площадь экземпляра `CurvePolygon`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 2, 2 0, 4 2, 4 2, 0 2))');  
 SELECT @g.STArea() AS Area;
 ```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
