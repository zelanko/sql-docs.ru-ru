---
title: "STBoundary (тип данных geometry) | Документы Microsoft"
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
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9c7db74c44bd314d23c7452722159b769def5777
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает границы **geometry** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STBoundary ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 `STBoundary()`Возвращает пустую коллекцию **GeometryCollection** при конечные точки для **LineString**, **CircularString**, или **CompoundCurve** экземпляра одинаковы.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>A. Использование STBoundary() в экземпляре LineString с разными конечными точками  
 В следующем примере создается `LineString``geometry` экземпляра. `STBoundary()`Возвращает границы `LineString`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>Б. Использование STBoundary() в экземпляре LineString с одинаковыми конечными точками  
 В следующем примере создается действительный экземпляр `LineString` с одинаковыми конечными точками. `STBoundary()` возвращает пустую коллекцию `GeometryCollection`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>В. Использование STBoundary() в экземпляре CurvePolygon  
 В следующем примере `STBoundary()` используется в пустом экземпляре `CurvePolygon`. `STBoundary()` возвращает экземпляр `CircularString`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
