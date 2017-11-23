---
title: "STDifference (тип данных geometry) | Документы Microsoft"
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
- STDifference_TSQL
- STDifference (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STDifference (geometry Data Type)
ms.assetid: 737f39bb-8750-4ffb-8594-23febc2f1075
caps.latest.revision: "31"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2e08d0245937739d29277bdddad0f1f4c6f695bc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stdifference-geometry-data-type"></a>STDifference (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает объект, представляющий набор точек одного **geometry** экземпляр, который не находится внутри другой **geometry** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой **geometry** , позволяющее определить, какие точки нужно удалить из экземпляра, на котором экземпляр `STDifference()` вызывается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 Этот метод всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geometry** экземпляров не совпадают.   Результат может содержать сегменты дуги, только если во входном экземпляре содержатся сегменты дуги.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-difference-between-two-polygon-instances"></a>A. Вычисление разницы между двумя экземплярами объекта Polygon  
 В следующем примере с помощью метода `STDifference()` вычисляется разница между двумя многоугольниками.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-invoking-stdifference-on-a-curvepolygon-instance"></a>Б. Вызов метода STDifference() для экземпляра CurvePolygon  
 В следующем примере метод STDifference() используется для экземпляра объекта CurvePolygon.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 -- Note the different results returned by the two SELECT statements  
 SELECT @h.STDifference(@g).ToString(), @g.STDifference(@h).ToString();
 ```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

