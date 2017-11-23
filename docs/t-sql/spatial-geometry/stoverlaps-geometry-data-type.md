---
title: "STOverlaps (тип данных geometry) | Документы Microsoft"
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
- STOverlaps (geometry Data Type)
- STOverlaps_TSQL
dev_langs: TSQL
helpviewer_keywords: STOverlaps (geometry Data Type)
ms.assetid: 1813cba1-5780-456a-9489-6b40a79569b3
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 800073a5f38869967cec42b00c762cd29cdffd09
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stoverlaps-geometry-data-type"></a>STOverlaps (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает 1, если **geometry** экземпляр перекрывается другим **geometry** экземпляра. В противном случае возвращается значение 0.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STOverlaps ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой **geometry** экземпляр для сравнения с экземпляром, в котором `STOverlaps()` вызывается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
 Два **geometry** экземпляров перекрываются, если область, представляющая их пересечение, имеет того же измерения, что и экземпляры и область не равна либо экземпляра.  
  
 `STOverlaps()`всегда возвращает 0, если точки где **geometry** пересекаются не одно измерение.  
  
 Этот метод всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geometry** экземпляров не совпадают.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `STOverlaps()` Чтобы протестировать два **geometry** экземпляров перекрываются.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STOverlaps(@h);  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

