---
title: "STEquals (тип данных geometry) | Документы Microsoft"
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
- STEquals (geometry Data Type)
- STEquals_TSQL
dev_langs: TSQL
helpviewer_keywords: STEquals (geometry Data Type)
ms.assetid: 808f0e25-9e68-4ba7-9329-07ec950698f3
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8e7aadcdf5d0527fe46337f56c5e98017afc4dd7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stequals-geometry-data-type"></a>STEquals (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает 1, если **geometry** экземпляр представляет как другой набор точек, **geometry** экземпляра. В противном случае возвращается значение 0.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STEquals ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой **geometry** экземпляр для сравнения с экземпляром, в котором `STEquals()` вызывается.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Этот метод всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geometry** экземпляров не совпадают.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается два `geometry` экземпляров с `STGeomFromText()` , которые равны, но заведомо эквивалентными и использует `STEquals()` для проверки их равенства.  
  
```  
DECLARE @g geometry  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('MULTILINESTRING((4 2, 2 0), (0 2, 2 0))', 0);  
SELECT @g.STEquals(@h);  
```  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

