---
title: "STNumGeometries (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- STNumGeometries (geography Data Type)
- STNumGeometries_TSQL
dev_langs: TSQL
helpviewer_keywords: STNumGeometries method
ms.assetid: 6ae7fac2-62f1-420f-9fc9-a09606be9605
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ec0dd1fac37d8040b3b2cc327127820d7761778
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stnumgeometries-geography-data-type"></a>STNumGeometries (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает число **геометрических объектов** , составляющих **geography** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **int**  
  
 Возвращаемый тип CLR: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает 1, если **geography** экземпляр не **MultiPoint**, **MultiLineString**, **MultiPolygon**, или **GeometryCollection** экземпляра или 0, если **geography** экземпляр пуст.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается `MultiPoint` и с помощью `STNumGeometries()` чтобы узнать, как много **геометрических объектов** экземпляр содержит.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT((-122.360 47.656), (-122.343 47.656))', 4326);  
SELECT @g.STNumGeometries();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
