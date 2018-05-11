---
title: STDistance (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance (geometry Data Type)
ms.assetid: ac815bc7-5342-4cc4-af40-c80a1c4c8b68
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00c6dad394bac2fd36c16d44023bdb1f40a80b8a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="stdistance-geometry-data-type"></a>STDistance (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает наименьшее расстояние от точки в экземпляре **geometry** до точки в другом экземпляре **geometry**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDistance ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой экземпляр **geometry**, от которого измеряется расстояние до экземпляра, где вызван метод `STDistance()`. Если *other_geometry* является пустым множеством, метод `STDistance()` возвращает значение NULL.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип возвращаемых данных CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Метод `STDistance()` всегда возвращает значение NULL, если идентификаторы пространственных ссылок (SRID) экземпляров **geometry** не совпадают.  
  
## <a name="examples"></a>Примеры  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POINT(10 10)', 0);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
