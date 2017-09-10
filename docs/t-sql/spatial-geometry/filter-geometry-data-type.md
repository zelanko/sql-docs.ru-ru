---
title: "Фильтр (тип данных geometry) | Документы Microsoft"
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
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: de93cc3be1f1a571b82c2d9ff2943af222f4f337
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="filter-geometry-data-type"></a>Filter (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Метод, который обеспечивает быстрое, доступное только для индекса пересечение способа определить, если **geometry** экземпляр пересекается с другим **geometry** экземпляра, если индекс доступен.
  
Возвращает 1, если **geometry** экземпляр потенциально пересекается с другим **geometry** экземпляра. В результате этого метода может появиться ложный положительный результат, а точный результат может зависеть от плана. Возвращает точное значение 0 (истинный отрицательный результат), если пересечение **geometry** найдены экземпляры.
  
В случаях, когда индекс недоступен, или не используется, метод возвращает те же значения, что **STIntersects()** при вызове с теми же параметрами.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Filter ( other_geometry )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geometry*  
 Другой **geometry** экземпляр для сравнения с экземпляром, для которого был вызван Filter().  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
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
  
  


