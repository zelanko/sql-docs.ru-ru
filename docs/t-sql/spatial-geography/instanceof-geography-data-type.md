---
title: InstanceOf (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf method
ms.assetid: 1eaed0e4-1c72-45a9-9926-5b513335cf33
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3a6939de145d3e63341bddda70d6fa04d9af9b69
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731146"
---
# <a name="instanceof-geography-data-type"></a>InstanceOf (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Проверяет принадлежность экземпляра **geography** к указанному типу.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
  
.InstanceOf ( 'geography_type')  
```  
  
## <a name="arguments"></a>Аргументы  
*geography_type*  
Строка типа **nvarchar(4000)** , задающая один из 16 типов, доступных в иерархии типов **geography**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
Тип возвращаемого значения CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
Возвращает значение 1, если тип экземпляра **geography** совпадает с указанным типом или указанный тип является предком типа экземпляра. В противном случае возвращает значение 0.  
  
Этот метод типа данных **geography** поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
Входным аргументом метода должен быть один из следующих объектов: Geometry, Point, Curve, LineString, CircularString, Surface, Polygon, CurvePolygon, **GeometryCollection**, **MultiSurface**, **MultiPolygon, MultiCurve, MultiLineString**, **MultiPoint** или **FullGlobe**.  
  
Если в качестве входного аргумента указана любая другая строка, этот метод вызовет исключение `ArgumentException`.  
  
Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
В следующем примере создается экземпляр `MultiPoint` и производится вызов метода `InstanceOf()`, позволяющий определить, принадлежит ли этот экземпляр типу `GeometryCollection`.  
  
```sql  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
