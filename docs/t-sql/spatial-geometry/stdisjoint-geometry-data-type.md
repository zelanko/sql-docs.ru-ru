---
description: STDisjoint (тип данных geometry)
title: STDisjoint (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDisjoint_TSQL
- STDisjoint (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDisjoint (geometry Data Type)
ms.assetid: 90acdb21-e826-4d81-afe8-45a71f33282a
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 43d6372bbe90146004e205d8ac3678196d76712e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88416900"
---
# <a name="stdisjoint-geometry-data-type"></a>STDisjoint (тип данных geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает 1, если экземпляр **geometry** не имеет пространственного перекрытия с другим экземпляром **geometry**. В противном случае возвращается значение 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDisjoint ( other_geometry )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *other_geometry*  
 Другой экземпляр **geometry** для сравнения с экземпляром, для которого вызван метод `STDisjoint()`.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Комментарии  
 Два экземпляра **geometry** не имеют пространственного перекрытия, если пересечение их наборов точек является пустым.  
  
 Этот метод всегда возвращает значение NULL, если у экземпляров **geometry** не совпадают идентификаторы пространственных ссылок (SRID).  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере используется метод `STDisjoint()`, чтобы протестировать два экземпляра **geometry** на отсутствие пространственного перекрытия между ними.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(1 1)', 0);  
SELECT @g.STDisjoint(@h);  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
