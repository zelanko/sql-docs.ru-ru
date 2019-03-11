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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e0ef6816efa98d3e9b2da27525d700fb4eba2501
ms.sourcegitcommit: c3b190f8f87a4c80bc9126bb244896197a6dc453
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852999"
---
# <a name="instanceof-geography-data-type"></a>InstanceOf (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Проверяет принадлежность экземпляра **geography** к указанному типу.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
  
.InstanceOf ( 'geography_type')  
```  
  
## <a name="arguments"></a>Аргументы  
*geography_type*  
Строка типа **nvarchar(4000)**, задающая один из 16 типов, доступных в иерархии типов **geography**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
Возвращаемый тип CLR: **SqlBoolean**  
  
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
  
  
