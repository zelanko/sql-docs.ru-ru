---
title: "STDisjoint (тип данных geometry) | Документы Microsoft"
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
- STDisjoint_TSQL
- STDisjoint (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDisjoint (geometry Data Type)
ms.assetid: 90acdb21-e826-4d81-afe8-45a71f33282a
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5052e2181dffe8c0404e7f33d1bbcd1ca139a45f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stdisjoint-geometry-data-type"></a>STDisjoint (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает 1, если **geometry** перекрытие из другого **geometry** экземпляра. В противном случае возвращается значение 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDisjoint ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой **geometry** экземпляр для сравнения с экземпляром, в котором `STDisjoint()` вызывается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
 Два **geometry** экземпляров раздельных, если пересечение их наборов точек является пустым.  
  
 Этот метод всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geometry** экземпляров не совпадают.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `STDisjoint()` Чтобы протестировать два **geometry** экземпляров для пространственных раздельных.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(1 1)', 0);  
SELECT @g.STDisjoint(@h);  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

