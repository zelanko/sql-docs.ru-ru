---
title: STSymDifference (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSymDifference_TSQL
- STSymDifference (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STSymDifference (geometry Data Type)
ms.assetid: 1d4cf35a-ca89-4aa4-ae30-e61a0ff18b53
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: bd51f436a5899722cc759ef79c5ead212f345bf6
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65935690"
---
# <a name="stsymdifference-geometry-data-type"></a>STSymDifference (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает объект, представляющий все точки, принадлежащие одному из экземпляров **geometry** или **geometry**, но не лежащие одновременно в обоих экземплярах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STSymDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой экземпляр **geometry** в дополнение к экземпляру, для которого вызван метод `STSymDistance()`.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Этот метод всегда возвращает значение NULL, если у экземпляров **geometry** не совпадают идентификаторы пространственных ссылок (SRID). Результат может содержать сегменты дуги, только если во входном экземпляре содержатся сегменты дуги.  
  
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
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="c-using-stsymdifference-on-curvepolygon-instance-with-an-inscribed-polygon-instance"></a>В. Применение функции STSymDifference() к экземпляру CurvePolygon с вписанным экземпляром Polygon  
 В следующем примере возвращается экземпляр `CurvePolygon`, содержащий внутренний экземпляр `Polygon`, представляющий симметричную разницу между двумя сравниваемыми экземплярами.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 2 -1, 2 1, 1 1, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
