---
description: STNumPoints (тип данных geography)
title: STNumPoints (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STNumPoints (geography Data Type)
- STNumPoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints method
ms.assetid: 25ff7ad1-ba5f-4cfb-816a-59255ac1591d
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6dbbf84ae21589d6428528d1599fe65eba7704f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88445198"
---
# <a name="stnumpoints-geography-data-type"></a>STNumPoints (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает общее количество точек в каждой из фигур в экземпляре **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STNumPoints ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип возвращаемых данных CLR: **SqlInt32**  
  
## <a name="remarks"></a>Примечания  
 Этот метод подсчитывает число точек в описании экземпляра **geography**. Повторяющиеся точки учитываются, однако соединение точек между сегментами учитывается только один раз. Если экземпляр является коллекцией, этот метод возвращает общее количество точек в каждом из элементов коллекции.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieving-the-total-number-of-points-in-a-linestring"></a>A. Получение общего количества точек в объекте LineString  
 В следующем примере создается экземпляр `LineString` и вызывается метод `STNumPoints()`, определяющий число точек, использованных в его описании.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STNumPoints();  
```  
  
### <a name="b-retrieving-the-total-number-of-points-in-a-geometrycollection"></a>Б. Получение общего количества точек в объекте GeometryCollection  
 В следующем примере возвращается сумма точек во всех элементах коллекции `GeometryCollection`.  
  
```  
DECLARE @g geography = 'GEOMETRYCOLLECTION(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)  
    ,CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
SELECT @g.STNumPoints();  
```  
  
### <a name="c-returning-the-number-of-points-in-a-compoundcurve"></a>В. Возврат числа точек в объекте CompoundCurve  
 В следующем примере возвращается число точек в экземпляре CompoundCurve. Запрос возвращает 5 вместо 6, так как функция STNumPoints() учитывает точку соединения между сегментами только один раз.  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658),( -122.348 47.658, -121.56 48.12, -122.358 47.653))'  
 SELECT @g.STNumPoints();
 ```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
