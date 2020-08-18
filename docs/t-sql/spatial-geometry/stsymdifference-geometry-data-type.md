---
description: STSymDifference (тип данных geometry)
title: STSymDifference (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 02/06/2020
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
ms.openlocfilehash: 1a419562b8326cbdceee2be888c538e61bbedac3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88359630"
---
# <a name="stsymdifference-geometry-data-type"></a>STSymDifference (тип данных geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает объект, представляющий все точки, принадлежащие одному из экземпляров **geometry** или **geometry**, но не лежащие одновременно в обоих экземплярах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STSymDifference ( other_geometry )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *other_geometry*  
 Другой экземпляр **geometry** в дополнение к экземпляру, для которого вызван метод `STSymDifference()`.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Комментарии  
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
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
