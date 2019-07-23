---
title: STGeometryN (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryN_TSQL
- STGeometryN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN (geometry Data Type)
ms.assetid: 348c7047-3442-4590-8879-fe841e79058c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 8eb3644652d826744b50b6980b0dbe0a42ae2d55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950201"
---
# <a name="stgeometryn-geometry-data-type"></a>STGeometryN (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает указанную геометрию в коллекцию **geometrycollection**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение типа **int** со значением от 1 до количества экземпляров **geometry** в коллекции **geometrycollection**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Данный метод возвращает значение **NULL**, если параметр больше, чем результат `STNumGeometries()`, и вызывает исключение **ArgumentOutOfRangeException**, если параметр *expression* меньше, чем 1.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `MultiPoint``geometry collection` и используется метод `STGeometryN()` для поиска второго экземпляра `geometry` этой коллекции.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

