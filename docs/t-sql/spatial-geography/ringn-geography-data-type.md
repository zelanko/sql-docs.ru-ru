---
description: RingN (тип данных geography)
title: RingN (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- RingN
- RingN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RingN method
ms.assetid: 30f47275-2727-4d22-bbec-c0c54bcb3ac2
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 58325135db25b79d7c38fb3447f6b7e5bfd8c89a
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88417020"
---
# <a name="ringn-geography-data-type"></a>RingN (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает указанное кольцо экземпляра **geography**: `1 ≤ n ≤ NumRings()`.  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
.RingN (expression )
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *expression*  
 Выражение типа **int** со значением от 1 до количества колец в экземпляре **polygon**.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Если значение индекса кольца **n** меньше 1, этот метод создает исключение **ArgumentOutOfRangeException.** Значение индекса кольца должно быть больше или равно 1 и меньше или равно значению, возвращенному методом `NumRings()`.  
  
## <a name="examples"></a>Примеры  
 В этом примере создается экземпляр `Polygon` с двумя кольцами и возвращается второе кольцо.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.RingN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [NumRings (тип данных geography)](../../t-sql/spatial-geography/numrings-geography-data-type.md)  
  
  
