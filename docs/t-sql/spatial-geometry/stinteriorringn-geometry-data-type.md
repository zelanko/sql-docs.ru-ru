---
title: STInteriorRingN (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 8e6908f612018978e234dd50074ae8eaf1998ed5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938884"
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает указанное внутреннее кольцо экземпляра **Polygongeometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение типа **int** от 1 до количества внутренних колец в экземпляре **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
 Тип OGC (открытый геопространственный консорциум): **LineString**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает значение **NULL**, если экземпляр **geometry** не является многоугольником. Этот метод также вызывает исключение **ArgumentOutOfRangeException**, если значение выражения больше количества колец. Количество колец можно получить с помощью метода `STNumInteriorRing``()`.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере создается экземпляр `Polygon` и используется метод `STInteriorRingN()` для возврата внутреннего кольца многоугольника в виде **LineString**.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

