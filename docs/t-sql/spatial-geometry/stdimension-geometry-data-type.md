---
title: "STDimension (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 35e8b1b731fc9d557fa233adced67bdd76d0da09
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stdimension-geometry-data-type"></a>STDimension (тип данных geometry, метод)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает максимальное измерение **geometry** экземпляра.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **int**  
  
 Возвращаемый тип CLR: **SqlInt32**  
  
## <a name="remarks"></a>Замечания  
 `STDimension()`Возвращает значение -1, если **geometry** экземпляр пуст.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается табличная переменная для хранения **geometry** экземпляры и вставляет `Point`, `LineString`и `Polygon`.  Затем он использует `STDimension()` возвращает измерения каждого **geometry** экземпляра.  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geometry);  
INSERT INTO @temp values ('Point', geometry::STGeomFromText('POINT(3 3)', 0));  
INSERT INTO @temp values ('LineString', geometry::STGeomFromText('LINESTRING(0 0, 3 3)', 0));  
INSERT INTO @temp values ('Polygon', geometry::STGeomFromText('POLYGON((0 0, 3 0, 0 3, 0 0))', 0));  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 Затем в примере возвращаются измерения каждого из экземпляров `geometry`.  
  
|имя|dim|  
|----------|---------|  
|Точка|0|  
|LineString|1|  
|Многоугольник|2|  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


