---
description: STGeometryN (тип данных geography)
title: STGeometryN (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 812a5e63f21de77028c1f00a08f1819c5a07be13
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88445253"
---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает указанный элемент **geography** в коллекции **GeometryCollection** или одном из ее подтипов. При использовании STGeometryN() для подтипа коллекции **GeometryCollection**, например **MultiPoint** или **MultiLineString**, этот метод возвращает экземпляр **geography**, если вызывается с помощью N=1.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STGeometryN ( expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *expression*  
 Выражение типа **int** со значением от 1 до количества экземпляров **geography** в коллекции **GeometryCollection**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Данный метод возвращает значение NULL, если параметр больше, чем результат [STNumGeometries()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md), и вызывает исключение **ArgumentOutOfRangeException**, если параметр *expression* меньше, чем 1.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `MultiPoint``geography` и с помощью метода `STGeometryN()` выполняется поиск второго экземпляра `geography` в коллекции **GeometryCollection**.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
