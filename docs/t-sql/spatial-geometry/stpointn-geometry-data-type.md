---
title: "STPointN (тип данных geometry) | Документы Microsoft"
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
- STPointN_TSQL
- STPointN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointN (geometry Data Type)
ms.assetid: 8f0bb3b7-5cd9-42c2-b9f8-f04628653bd0
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 123ce8f5775bff59ff917bf0916f8e37108b9245
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stpointn-geometry-data-type"></a>STPointN (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает указанную точку в **geometry** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STPointN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 — **Int** выражение от 1 до количества точек в **geometry** экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
 Открытый тип Geospatial Consortium (OGC): **точки**  
  
## <a name="remarks"></a>Remarks  
 Если **geometry** экземпляр является пользователем, созданным, `STPointN()` возвращает точку, указанную *выражение* путем упорядочения точек в том порядке, в котором они были первоначально введены.  
  
 Если **geometry** экземпляр был создан системой, `STPointN()` возвращает точку, указанную *выражение* путем упорядочения всех точек в том же порядке, они должны быть выведены: сначала по геометрическим объектам, затем по кольцам внутри геометрического объекта (если применимо), а затем по точкам внутри кольца. Это порядок является детерминированным.  
  
 Если этот метод вызывается со значением менее 1, он выдает **ArgumentOutOfRangeException**.  
  
 Если этот метод вызывается со значением, превышающим число точек в экземпляре, он возвращает значение NULL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString`, и при помощи метода `STPointN()` производится получение второй точки в его описании.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STPointN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

