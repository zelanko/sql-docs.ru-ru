---
title: "STIsSimple (тип данных geometry) | Документы Microsoft"
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
- STIsSimple_TSQL
- STIsSimple (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsSimple (geometry Data Type)
ms.assetid: da8f45d4-4f9c-405d-b883-760eb5344a71
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5240f2a8c9dc28f9256db87106fdcfaf0b689034
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stissimple-geometry-data-type"></a>STIsSimple (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает 1, если **geometry** экземпляр является простым, как определено, Open Geospatial Consortium (OGC). Возвращает 0, если **geometry** экземпляр не является простым.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsSimple ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Чтобы быть простым, **geometry** экземпляр должен отвечать следующим требованиям:  
  
-   Каждая фигура экземпляра не должна пересекать саму себя, за исключением конечных точек.  
  
-   Никакие две фигуры экземпляра не могут пересекаться в точке, не находящейся на их границах.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается непростой экземпляр `LineString`, который пересекает самого себя, и используется метод `STIsSimple()`, чтобы проверить, является ли экземпляр `LineString` простым.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STIsSimple();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

