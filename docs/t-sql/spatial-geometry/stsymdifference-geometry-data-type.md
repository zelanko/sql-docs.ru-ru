---
title: "STSymDifference (тип данных geometry) | Документы Microsoft"
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
- STSymDifference_TSQL
- STSymDifference (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STSymDifference (geometry Data Type)
ms.assetid: 1d4cf35a-ca89-4aa4-ae30-e61a0ff18b53
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b83e2ef917f76f615588327c8a3c2721f30e347a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stsymdifference-geometry-data-type"></a>STSymDifference (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает объект, представляющий все точки, в какой-либо **geometry** экземпляр или другой **geometry** экземпляра, но не лежащие одновременно в обоих экземплярах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STSymDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой **geometry** экземпляр в дополнение к экземпляром, в котором `STSymDistance()` вызывается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 Этот метод всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geometry** экземпляров не совпадают. Результат может содержать сегменты дуги, только если во входном экземпляре содержатся сегменты дуги.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygon-instances"></a>A. Вычисление симметричной разницы двух экземпляров Polygon  
 В следующем примере метод `STSymDifference()` применяется для вычисления симметрической разности двух экземпляров `Polygon`.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-between-a-curvepolygon-and-a-polygon-instance"></a>Б. Вычисление симметричной разницы между экземплярами CurvePolygon и Polygon  
 В следующем примере возвращается коллекция `GeometryCollection`, представляющая симметричную разницу между экземплярами `CurvePolygon` и `Polygon`.  
  
 `DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';`  
  
 `DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';`  
  
 `SELECT @h.STSymDifference(@g).ToString();`  
  
## <a name="c-using-stsymdifference-on-curvepolygon-instance-with-an-inscribed-polygon-instance"></a>В. Применение функции STSymDifference() к экземпляру CurvePolygon с вписанным экземпляром Polygon  
 В следующем примере возвращается экземпляр `CurvePolygon`, содержащий внутренний экземпляр `Polygon`, представляющий симметричную разницу между двумя сравниваемыми экземплярами.  
  
 `DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';`  
  
 `DECLARE @h geometry = 'POLYGON ((1 -1, 2 -1, 2 1, 1 1, 1 -1))';`  
  
 `SELECT @h.STSymDifference(@g).ToString();`  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

