---
description: STDifference (тип данных geography)
title: STDifference (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 067d49755229cad03fe77ae981cf7673d68f536a
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88417040"
---
# <a name="stdifference-geography-data-type"></a>STDifference (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает объект, представляющий набор точек одного экземпляра **geography**, который находится за пределами другого экземпляра **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDifference ( other_geography )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *other_geography*  
 Другой экземпляр **geography**, который показывает, какие точки нужно удалить из экземпляра, для которого вызван метод STDifference().  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Этот метод вызывает исключение **ArgumentException**, если экземпляр содержит противоположную границу.  
  
## <a name="remarks"></a>Remarks  
 Этот метод всегда возвращает значение NULL, если идентификаторы пространственных ссылок (SRID) экземпляров **geography** не совпадают.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набор возможных результатов, возвращаемый на сервер, был пополнен экземплярами **FullGlobe**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает пространственные экземпляры, размер которых превышает полусферу. Результат может содержать сегменты дуги, только если во входном экземпляре содержатся сегменты дуги. Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Вычисление разницы между двумя географическими объектами  
 В следующем примере с помощью метода `STDifference()` вычисляется разница между двумя экземплярами **geography**.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-using-a-fullglobe-with-stdifference"></a>Б. Использование параметра FullGlobe с функцией STDifference()  
 В следующем примере используется экземпляр `FullGlobe`. Первый результат — пустая коллекция `GeometryCollection`, второй результат — экземпляр `Polygon`. `STDifference()` возвращает пустую коллекцию `GeometryCollection`, когда экземпляр `FullGlobe` является параметром. Каждая точка экземпляра `geography` содержится в экземпляре `FullGlobe`.  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 DECLARE @h geography = 'FULLGLOBE';  
 SELECT @g.STDifference(@h).ToString(),  
 @h.STDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
