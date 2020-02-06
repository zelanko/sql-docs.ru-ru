---
title: STIsSimple (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsSimple_TSQL
- STIsSimple (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsSimple (geometry Data Type)
ms.assetid: da8f45d4-4f9c-405d-b883-760eb5344a71
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 0b91fdde3c6940ffa0a7f2e77591e05578e005c4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67894919"
---
# <a name="stissimple-geometry-data-type"></a>STIsSimple (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает 1, если экземпляр **geometry** является простым по определению консорциума OGC. Возвращает значение 0, если экземпляр **geometry** не является простым.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsSimple ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Чтобы быть простым, экземпляр **geometry** должен отвечать следующим требованиям:  
  
-   Каждая фигура экземпляра не должна пересекать саму себя, за исключением конечных точек.  
  
-   Никакие две фигуры экземпляра не могут пересекаться в точке, не находящейся на их границах.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается непростой экземпляр `LineString`, который пересекает самого себя, и используется метод `STIsSimple()`, чтобы проверить, является ли экземпляр `LineString` простым.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STIsSimple();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

