---
title: "Фильтр (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- Filter (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 82a8f54a-3a47-4e20-b13a-b148029c5448
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 537e3a05ad368be5278eef9dc9c3d29d19754322
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="filter-geography-data-type"></a>Filter (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Метод, который обеспечивает быстрое, доступное только для индекса пересечение способа определить, если **geography** экземпляр пересекается с другим **geography** экземпляра, если индекс доступен.  
  
 Возвращает 1, если **geography** экземпляр потенциально пересекается с другим **geography** экземпляра. В результате этого метода может появиться ложный положительный результат, а точный результат может зависеть от плана. Возвращает точное значение 0 (истинный отрицательный результат), если пересечение **geography** найдены экземпляры.  
  
 В случаях, когда индекс недоступен, или не используется, метод возвращает те же значения, что **STIntersects()** при вызове с теми же параметрами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Filter ( other_geography )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geography*  
 Другой **geography** экземпляр для сравнения с экземпляром, для которого был вызван Filter().  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
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
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [STIntersects &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stintersects-geography-data-type.md)  
  
  
