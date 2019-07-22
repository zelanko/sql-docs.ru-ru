---
title: STPointOnSurface (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointOnSurface (geometry Data Type)
- STPointOnSurface_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointOnSurface (geometry Data Type)
ms.assetid: 23b2b8eb-4176-49fb-ace0-92398928d60e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b1a820bc4f951fcbe294060825979d83a34f8969
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066376"
---
# <a name="stpointonsurface-geometry-data-type"></a>STPointOnSurface (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает произвольную точку, которая находится внутри экземпляра **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STPointOnSurface ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
 Тип OGC (открытый геопространственный консорциум): **Point**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает значение NULL, если экземпляр пуст.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Polygon` и с помощью метода `STPointOnSurface()` выполняется поиск точки в экземпляре.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STPointOnSurface().ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

