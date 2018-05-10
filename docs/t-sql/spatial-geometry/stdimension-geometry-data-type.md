---
title: STDimension (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STDimension_TSQL
- STDimension (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension (geometry Data Type)
ms.assetid: 4fbd27dd-317b-4916-a8ae-4df1b8a6f27c
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8611900914f51229a95aae8f838ecf07e428e347
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="stdimension-geometry-data-type"></a>STDimension (тип данных geometry, метод)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает максимальную размерность экземпляра **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип возвращаемых данных CLR: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Метод `STDimension()` возвращает значение –1, если экземпляр **geometry** является пустым.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается табличная переменная для хранения экземпляров **geometry**, а также вставляется `Point`, `LineString` и `Polygon`.  Затем функция `STDimension()` возвращает измерения каждого экземпляра **geometry**.  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geometry);  
INSERT INTO @temp values ('Point', geometry::STGeomFromText('POINT(3 3)', 0));  
INSERT INTO @temp values ('LineString', geometry::STGeomFromText('LINESTRING(0 0, 3 3)', 0));  
INSERT INTO @temp values ('Polygon', geometry::STGeomFromText('POLYGON((0 0, 3 0, 0 3, 0 0))', 0));  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 Затем в примере возвращаются измерения каждого из экземпляров `geometry`.  
  
|name|dim|  
|----------|---------|  
|Точка|0|  
|LineString|1|  
|Polygon|2|  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

