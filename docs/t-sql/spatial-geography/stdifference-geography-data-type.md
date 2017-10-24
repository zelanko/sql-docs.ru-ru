---
title: "STDifference (тип данных geography) | Документы Microsoft"
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
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5afb37eb29e63d8cf08e9c158b94385a66d4c41f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stdifference-geography-data-type"></a>STDifference (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает объект, представляющий набор точек одного **geography** экземпляр, который находится за пределами другого **geography** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geography*  
 Другой **geography** , позволяющее определить, какие точки нужно удалить из экземпляра, для которого вызывается STDifference() экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Этот метод создает исключение **ArgumentException** Если экземпляр содержит противоположную границу.  
  
## <a name="remarks"></a>Замечания  
 Этот метод всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geography** экземпляров не совпадают.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], набор возможных результатов, возвращаемый на сервер была расширена для **FullGlobe** экземпляров. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает пространственные экземпляры, размер которых превышает полусферу. Результат может содержать сегменты дуги, только если во входном экземпляре содержатся сегменты дуги. Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Вычисление разницы между двумя географическими объектами  
 В следующем примере используется `STDifference()` вычисляется разница между двумя **geography** экземпляров.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах географических объектов](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

