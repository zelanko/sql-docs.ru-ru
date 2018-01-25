---
title: "STUnion (тип данных geometry) | Документы Microsoft"
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
- STUnion (geometry Data Type)
- STUnion_TSQL
dev_langs: TSQL
helpviewer_keywords: STUnion (geometry Data Type)
ms.assetid: 5b168118-137d-402f-9173-fee3f365a89c
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45156b37fbc46ed92cb342eb1b1e82baa93131f7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stunion-geometry-data-type"></a>STUnion (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает объект, представляющий объединение **geometry** экземпляр с другим **geometry** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STUnion ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой **geometry** экземпляра, образующий объединение с экземпляром, на котором `STUnion()` вызывается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Этот метод всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geometry** экземпляров не совпадают. Результат может содержать сегменты дуги, только если во входном экземпляре содержатся сегменты дуги.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-union-of-two-polygon-instances"></a>A. Вычисление объединения двух экземпляров многоугольников  
 В следующем примере метод `STUnion()` производит объединение двух экземпляров `Polygon`.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STUnion(@h).ToString();  
```  
  
### <a name="b-computing-the-union-of-a-polygon-instance-with-a-curvepolygon-instance"></a>Б. Вычисление объединения экземпляра Polygon с экземпляром CurvePolygon  
 Следующий пример возвращает экземпляр `GeometryCollection`, содержащий сегмент дуги.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON((5 -1, 5 -3, 7 -3, 7 -1, 5 -1))';  
 SELECT @g.STUnion(@h).ToString();
 ```  
  
 Функция `STUnion()` возвращает результат, содержащий сегмент дуги, так как экземпляр, вызвавший `STUnion()`, содержит сегмент дуги.  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

