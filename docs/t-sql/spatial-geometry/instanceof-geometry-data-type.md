---
title: "InstanceOf (тип данных geometry) | Документы Майкрософт"
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
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c53e66f85d614b79e51312dc4404fd19acd69fed
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Метод, который проверяет принадлежность экземпляра **geometry** к указанному типу. Возвращает значение 1, если экземпляр **geometry** имеет указанный тип или если указанный тип является предком типа экземпляра в иерархии. В противном случае возвращает значение 0.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_type*  
 Строка типа **nvarchar(4000)**, задающая один из 15 типов, доступных в иерархии типов **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Входные данные метода должны быть одного из следующих типов: **Geometry**, **Point**, **Curve**, **LineString**, **CircularString**, **CompoundCurve**, **Surface**, **Polygon**, **CurvePolygon**, **GeometryCollection**, **MultiSurface**, **MultiPolygon**, **MultiCurve**, **MultiLineString** или **MultiPoint**. Если в качестве входного аргумента указана любая другая строка, этот метод вызовет исключение **ArgumentException**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `MultiPoint` и производится вызов метода `InstanceOf()`, позволяющего определить, является ли экземпляр `GeometryCollection`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

