---
title: STStartPoint (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STStartPoint_TSQL
- STStartPoint (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STStartPoint method
ms.assetid: 7df18a5f-b9ee-4e36-b765-a0790c1dee3d
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f673860664d6be588479111803c200f2903db0ca
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68120793"
---
# <a name="ststartpoint-geography-data-type"></a>STStartPoint (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает начальную точку экземпляра **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STStartPoint ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
 Тип открытого геопространственного консорциума (OGC): **Point**  
  
## <a name="remarks"></a>Remarks  
 Метод STStartPoint() является эквивалентом метода [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)`(1)`.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `LineString` и при помощи метода `STStartPoint()` производится получение его начальной точки.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STStartPoint().ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
