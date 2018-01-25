---
title: "STIsValid (тип данных geometry) | Документы Microsoft"
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
- STIsValid (geometry Data Type)
- STIsValid_TSQL
dev_langs: TSQL
helpviewer_keywords: STIsValid (geometry Data Type)
ms.assetid: 6da39bea-0f67-4660-98fc-d7214f9b2138
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 436cab211eceff9eb286b4e44e90aa3f64b9d03c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stisvalid-geometry-data-type"></a>STIsValid (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает значение true, если **geometry** экземпляр имеет правильный формат, в соответствии с типом Open Geospatial Consortium (OGC). Возвращает значение false, если **geometry** экземпляр не является правильным.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Тип OGC **geometry** экземпляра можно определить путем вызова [STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]формирует только допустимые **geometry** экземпляров, но обеспечивает для хранения и получать недопустимые экземпляры. Допустимый экземпляр, представляющий тот же набор точек, что и любой недопустимый экземпляр, может быть получен с помощью метода `MakeValid()`.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `geometry` и используется метод `STIsValid()`, чтобы проверить, допустим ли экземпляр.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STIsValid();  
```  
  
## <a name="see-also"></a>См. также  
 [STGeometryType &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [MakeValid (тип данных geometry)](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

