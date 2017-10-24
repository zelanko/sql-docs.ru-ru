---
title: "STUnion (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STUnion (geometry Data Type)
- STUnion_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STUnion (geometry Data Type)
ms.assetid: 5b168118-137d-402f-9173-fee3f365a89c
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3c41cbcf144e8772cd17cbfb43da403aea29a353
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stunion-geometry-data-type"></a>STUnion (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

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
  
## <a name="remarks"></a>Замечания  
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
  
## <a name="see-also"></a>См. также:  
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


