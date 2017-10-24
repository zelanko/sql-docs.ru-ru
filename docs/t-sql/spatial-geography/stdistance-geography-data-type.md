---
title: "STDistance (тип данных geography) | Документы Microsoft"
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
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f79891d789938a6f4615c0e4be9cc3ba5d361f1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stdistance-geography-data-type"></a>STDistance (географический тип данных)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает кратчайшее расстояние между точкой в **geography** экземпляра и точки в другом **geography** экземпляра.  
  
> [!NOTE]  
>  `STDistance()`Возвращает самое короткое **LineString** между двумя типами geography. Это приблизительное значение, соответствующее геодезическому расстоянию. Отклонение `STDistance()` на простых моделях Земли от точного геодезического расстояния — не более. 25%. Это позволяет избежать путаницы, когда речь заходит о незначительной разнице между длиной и расстоянием в геодезических типах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geography*  
 Другой **geography** экземпляр, из которого измеряется расстояние до экземпляра, для которого был вызван STDistance(). Если *other_geography* задан пустой, STDistance() возвращает значение null.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **число с плавающей запятой**  
  
 Возвращаемый тип CLR: **SqlDouble**  
  
## <a name="remarks"></a>Замечания  
 STDistance() всегда возвращает значение null, если идентификаторы пространственной ссылки (SRID) из **geography** экземпляров не совпадают.  
  
> [!NOTE]  
>  Методы в **geography** тип данных, вычисляющие площадь или расстояние будет возвращать различные результаты в зависимости от идентификатора SRID экземпляра, используемого в методе.   Дополнительные сведения об идентификаторах SRID см. в разделе [идентификаторы пространственных ссылок &#40; SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере вычисляется расстояние между двумя **geography** экземпляров.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах географических объектов](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

