---
title: "STArea (тип данных geometry) | Документы Microsoft"
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
- STArea (geometry Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea (geometry Data Type)
ms.assetid: a7dd6083-c649-4ac3-885d-1234e0db62f1
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ec0a874d0dc2dd8bb37ce7e04fe71cbea85f860
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="starea-geometry-data-type"></a>STArea (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает общую площадь поверхности **geometry** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **число с плавающей запятой**  
  
 Возвращаемый тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 `STArea()`Возвращает 0, если **geometry** экземпляр содержит только 0 и 1-размерности, или если она пуста. `STArea()`Возвращает **NULL** Если **geometry** экземпляр не инициализирован.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-area-of-a-polygon-instance"></a>A. Вычисление площади экземпляра объекта Polygon  
 В следующем примере создается `Polygon``geometry` и вычисляется площадь многоугольника.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STArea();  
```  
  
### <a name="b-computing-the-area-of-a-curvepolygon-instance"></a>Б. Вычисление площади экземпляра объекта CurvePolygon  
 В следующем примере вычисляется площадь экземпляра `CurvePolygon`.  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 2, 2 0, 4 2, 4 2, 0 2))');`  
  
 `SELECT @g.STArea() AS Area;`  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

