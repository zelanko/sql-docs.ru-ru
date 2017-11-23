---
title: "STInteriorRingN (тип данных geometry) | Документы Microsoft"
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
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e80a67f84c153a8b2daffc0174046af70c972709
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает указанное внутреннее кольцо **Polygongeometry** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 — **Int** выражение от 1 до количества внутренних колец в **geometry** экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
 Открытый тип Geospatial Consortium (OGC): **LineString**  
  
## <a name="remarks"></a>Замечания  
 Этот метод возвращает **null** Если **geometry** экземпляр не многоугольника. Этот метод также вызывает **ArgumentOutOfRangeException** Если выражения больше количества колец. Количество колец можно получить с помощью метода `STNumInteriorRing``()`.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `Polygon` и с помощью `STInteriorRingN()` для возврата внутреннее кольцо многоугольника как **LineString**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

