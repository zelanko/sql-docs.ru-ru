---
title: Filter (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5cbfa37a468fcc600b4092340d9f58365954294a
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86556033"
---
# <a name="filter-geometry-data-type"></a>Filter (тип данных geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Предоставляет быстрый метод пересечения, который используется только для индексов и определяет, пересекается ли экземпляр **geometry** с другим экземпляром **geometry** при условии, что индекс доступен.
  
Возвращает значение 1, если экземпляр **geometry** потенциально пересекается с другим экземпляром **geometry**. В результате этого метода может появиться ложный положительный результат, а точный результат может зависеть от плана. Возвращает точное значение 0 (истинный отрицательный результат), если пересечение экземпляров **geometry** не обнаружено.
  
Если индекс недоступен или не используется, этот метод возвращает те же значения, что и метод **STIntersects()** , при вызове с одинаковыми параметрами.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Filter ( other_geometry )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *other_geometry*  
 Другой экземпляр **geometry** для сравнения с экземпляром, для которого вызван метод Filter().  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Этот метод не является детерминированным или точным.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `Filter()` определяет, пересекаются ли два экземпляра `geometry`.  
  
```  
CREATE TABLE sample (id int primary key, g geometry);  
GO  
INSERT INTO sample VALUES  
   (0, geometry::Point(0, 0, 0)),  
   (1, geometry::Point(0, 1, 0)),  
   (2, geometry::Point(0, 2, 0)),  
   (3, geometry::Point(0, 3, 0)),  
   (4, geometry::Point(0, 4, 0));  
  
CREATE SPATIAL INDEX sample_idx ON sample(g)  
WITH (bounding_box = (-8000, -8000, 8000, 8000));  
GO  
SELECT id  
FROM sample   
WHERE g.Filter(geometry::Parse('POLYGON((-1 -1, 1 -1, 1 1, -1 1, -1 -1))')) = 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [STIntersects (тип данных geometry)](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
  

