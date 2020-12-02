---
description: Filter (тип данных geography)
title: Filter (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Filter
- Filter_TSQL
- Filter (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 82a8f54a-3a47-4e20-b13a-b148029c5448
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4a5e5ff41504184bd8c1aa0805267f38566b5162
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96124316"
---
# <a name="filter-geography-data-type"></a>Filter (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Предоставляет быстрый метод пересечения, который используется только для индексов и определяет, пересекается ли экземпляр **geography** с другим экземпляром **geography** при условии, что индекс доступен.  
  
 Возвращает значение 1, если экземпляр **geography** потенциально пересекается с другим экземпляром **geography**. В результате этого метода может появиться ложный положительный результат, а точный результат может зависеть от плана. Возвращает точное значение 0 (истинный отрицательный результат), если пересечение экземпляров **geography** не обнаружено.  
  
 Если индекс недоступен или не используется, этот метод возвращает те же значения, что и метод **STIntersects()**, при вызове с одинаковыми параметрами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Filter ( other_geography )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *other_geography*  
 Другой экземпляр **geography** для сравнения с экземпляром, для которого вызван метод Filter().  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Комментарии  
 Этот метод не является детерминированным или точным.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `Filter()` определяет, пересекаются ли два экземпляра `geography`.  
  
```  
CREATE TABLE sample (id int primary key, g geography);  
INSERT INTO sample VALUES  
   (0, geography::Point(45, -120, 4326)),  
   (1, geography::Point(45, -120.1, 4326)),  
   (2, geography::Point(45, -120.2, 4326)),  
   (3, geography::Point(45, -120.3, 4326)),  
   (4, geography::Point(45, -120.4, 4326));  
  
CREATE SPATIAL INDEX sample_idx on sample(g);  
SELECT id  
FROM sample   
WHERE g.Filter(geography::Parse(  
   'POLYGON((-120.1 44.9, -119.9 44.9, -119.9 45.1, -120.1 45.1, -120.1 44.9))')) = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [STIntersects (тип данных geography)](../../t-sql/spatial-geography/stintersects-geography-data-type.md)  
  
  
