---
title: "InstanceOf (тип данных geometry) | Документы Microsoft"
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
- InstanceOf
- InstanceOf_TSQL
dev_langs: TSQL
helpviewer_keywords: InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
caps.latest.revision: "26"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5503698d81244ba5194a32812bd86ecf40f1cd39
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Метод, который проверяет, может ли **geometry** экземпляра совпадает с указанным типом. Возвращает 1, если тип **geometry** экземпляра совпадает со значением указанного типа, или если указанный тип является предком типа экземпляра; в противном случае возвращает 0.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_type*  
 — **Nvarchar(4000)** строка, задающая один из 15 типов, доступных в **geometry** иерархия типов.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
 Входные данные для метода должен быть одним из следующих: **Geometry**, **точки**, **кривой**, **LineString**,  **CircularString**, **CompoundCurve**, **поверхность**, **многоугольника**, **CurvePolygon**, **GeometryCollection**, **MultiSurface**, **MultiPolygon**, **MultiCurve**, **MultiLineString**, и **MultiPoint**. Этот метод создает исключение **ArgumentException** другие строки при использовании для входных данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `MultiPoint` и производится вызов метода `InstanceOf()`, позволяющего определить, является ли экземпляр `GeometryCollection`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

