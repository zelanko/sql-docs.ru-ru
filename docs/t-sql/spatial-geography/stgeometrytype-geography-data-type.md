---
title: "STGeometryType (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STGeometryType (geography Data Type)
- STGeometryType_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryType method
ms.assetid: 3e169ead-a98e-44af-8d33-fd59a955cae4
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9ce316d900f057e8c1907b8e731f1080a84fb5dc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stgeometrytype-geography-data-type"></a>STGeometryType (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает имя типа Open Geospatial Consortium (OGC), представленный **geography** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STGeometryType ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **nvarchar(4000)**  
  
 Возвращаемый тип CLR: **SqlString**  
  
## <a name="remarks"></a>Замечания  
 Имена типов OGC, которые могут быть возвращены `STGeometryType()` , **точки**, **LineString**, **CircularString**, **CompoundCurve**, **Многоугольника**, **CurvePolygon**, **GeometryCollection**, **MultiPoint**, **MultiLineString**, и **MultiPolygon**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Polygon` и используется метод `STGeometryType()`, чтобы проверить, является ли этот экземпляр многоугольником.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STGeometryType();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах географических объектов](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

