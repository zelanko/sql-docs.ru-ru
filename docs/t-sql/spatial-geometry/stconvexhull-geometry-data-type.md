---
title: "STConvexHull (тип данных geometry) | Документы Microsoft"
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
- STConvexHull (geometry Data Type)
- STConvexHull_TSQL
dev_langs: TSQL
helpviewer_keywords: STConvexHull (geometry Data Type)
ms.assetid: 60a520a6-1a7c-486b-8d91-34401edf6233
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46200dd68f2c152788245bc0aad672de18aeb4b6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stconvexhull-geometry-data-type"></a>STConvexHull (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает объект, представляющий выпуклую оболочку **geometry** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 `STConvexHull()`Возвращает наименьший Выпуклый многоугольник, который содержит данный **geometry** экземпляра. **Точки** или взаимолинейные **LineString** экземпляров будет создавать экземпляр того же типа, как и входные данные.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STConvexHull()` используется для поиска выпуклой оболочки невыпуклого экземпляра `Polygon``geometry`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 1 1, 2 2, 2 0, 0 0))', 0);  
SELECT @g.STConvexHull().ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

