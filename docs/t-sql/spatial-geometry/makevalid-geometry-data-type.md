---
title: "MakeValid (тип данных geometry) | Документы Microsoft"
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
- MakeValid
- MakeValid_TSQL
dev_langs: TSQL
helpviewer_keywords: MakeValid (geometry Data Type)
ms.assetid: 38673010-ab77-4ebb-9c4d-b26b79e3b7ea
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: fd3f338dba1020d2424b69a5794fe27f3e151775
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="makevalid-geometry-data-type"></a>MakeValid (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Преобразует недопустимый **geometry** экземпляра в **geometry** экземпляра с допустимым типом Open Geospatial Consortium (OGC).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 Этот метод может вызвать изменение в типе **geometry** экземпляра, а также привести к точкам **geometry** экземпляра к небольшому сдвигу.  
  
## <a name="examples"></a>Примеры  
 В первом примере создается недопустимый экземпляр `LineString`, который перекрывает сам себя, и используется метод `STIsValid()`, чтобы подтвердить, что этот экземпляр является недопустимым. Функция `STIsValid()` возвращает значение 0 для недопустимого экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 0);  
SELECT @g.STIsValid();  
```  
  
 Во втором примере, чтобы преобразовать экземпляр в допустимый и проверить, что этот экземпляр действительно допустим, используется метод `MakeValid()`. `STIsValid()`Возвращает значение 1 для допустимого экземпляра.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 В третьем примере проверяется, как был изменен экземпляр для преобразования его в допустимый.  
  
```  
SELECT @g.ToString();  
```  
  
 В этом примере при выборе экземпляра `LineString` значения возвращаются так же, как при использовании допустимого экземпляра `MultiLineString`.  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
 В следующем примере экземпляр CircularString преобразуется в экземпляр Point.  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 1 1, 1 1)';  
SELECT @g.MakeValid().ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

