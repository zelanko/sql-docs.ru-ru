---
title: InstanceOf (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
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
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 9622a762b8ac7e40dfcbd61c9ff4acdbe2aef67c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748881"
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (тип данных geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Метод, который проверяет принадлежность экземпляра **geometry** к указанному типу. Возвращает значение 1, если тип экземпляра **geometry** соответствует указанному типу. Этот метод также возвращает значение 1, если указанный тип является предком типа экземпляра. В противном случае этот метод всегда возвращает значение 0.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>Аргументы  
*geometry_type*  
Строка **nvarchar(4000)** , задающая один из 15 типов, доступных в иерархии типов **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемого значения CLR: **SqlBoolean**  
  
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
  
  

