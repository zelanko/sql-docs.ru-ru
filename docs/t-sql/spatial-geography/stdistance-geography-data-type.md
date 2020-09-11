---
description: STDistance (географический тип данных)
title: STDistance (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a20279a70d2e68e1cb4b34eb36ffe7de633518a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417000"
---
# <a name="stdistance-geography-data-type"></a>STDistance (географический тип данных)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает наименьшее расстояние от точки в экземпляре **geography** до точки в другом экземпляре **geography**.  
  
> [!NOTE]  
>  `STDistance()` возвращает самое короткое значение **LineString** между двумя типами geography. Это приблизительное значение, соответствующее геодезическому расстоянию. Отклонение значения `STDistance()` на простых моделях Земли от точного геодезического расстояния составляет не более 0,25 %. Это позволяет избежать путаницы, когда речь заходит о незначительной разнице между длиной и расстоянием в геодезических типах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDistance ( other_geography )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *other_geography*  
 Другой экземпляр **geography**, от которого измеряется расстояние до экземпляра, где вызван метод STDistance(). Если *other_geography* является пустым набором, STDistance() возвращает значение NULL.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип возвращаемых данных CLR: **SqlDouble**  
  
## <a name="remarks"></a>Комментарии  
 Результат выражается в единице измерения, определенной [идентификатором пространственной ссылки (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md) пространственных данных.
STDistance() всегда возвращает значение *NULL*, если у экземпляров **geography** не совпадают идентификаторы пространственных ссылок (SRID).  
  
> [!NOTE]  
>  Методы, вызываемые для типа данных **geography** и вычисляющие площадь или расстояние, могут возвращать различные результаты в зависимости от идентификатора SRID экземпляра. Дополнительные сведения об идентификаторах SRID см. в разделе [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере вычисляется расстояние между двумя экземплярами **geography**.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
