---
title: "STIntersection (тип данных geometry) | Документы Майкрософт"
ms.custom: 
ms.date: 08/03/2017
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
- STIntersection_TSQL
- STIntersection (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection (geometry Data Type)
ms.assetid: 354843f5-cc14-478c-974a-04f363f9530f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f6b2674cbd4c1443a3762459a543fb9712253d8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stintersection-geometry-data-type"></a>STIntersection (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает объект, представляющий точки, в которых экземпляр **geometry** пересекается с другим экземпляром **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIntersection ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой экземпляр **geometry**, сравниваемый с экземпляром, для которого вызван метод `STIntersection()`, чтобы определить место их пересечения.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Метод `STIntersection()` всегда возвращает значение NULL, если идентификаторы пространственных ссылок (SRID) экземпляров **geometry** не совпадают. Результат может содержать сегменты дуги только в том случае, если они содержатся во входном экземпляре.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stintersection-on-polygon-instances"></a>A. Использование STIntersection() в экземплярах Polygon  
 В следующем примере с помощью метода `STIntersection()` вычисляется пересечение двух многоугольников.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-using-stintersection-with-curvepolygon-instance"></a>Б. Использование STIntersection() в экземпляре CurvePolygon  
 Следующий пример возвращает экземпляр, содержащий сегмент дуги.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STIntersection(@g).ToString();
 ```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

