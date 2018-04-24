---
title: STDistance (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1520ed3cc4554c7311d35aa6499ebf19e3eb2137
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="stdistance-geography-data-type"></a>STDistance (географический тип данных)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает наименьшее расстояние от точки в экземпляре **geography** до точки в другом экземпляре **geography**.  
  
> [!NOTE]  
>  `STDistance()` возвращает самое короткое значение **LineString** между двумя типами geography. Это приблизительное значение, соответствующее геодезическому расстоянию. Отклонение значения `STDistance()` на простых моделях Земли от точного геодезического расстояния составляет не более 0,25 %. Это позволяет избежать путаницы, когда речь заходит о незначительной разнице между длиной и расстоянием в геодезических типах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geography*  
 Другой экземпляр **geography**, от которого измеряется расстояние до экземпляра, где вызван метод STDistance(). Если *other_geography* является пустым набором, STDistance() возвращает значение NULL.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип возвращаемых данных CLR: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 STDistance() всегда возвращает значение NULL, если у экземпляров **geography** не совпадают идентификаторы пространственных ссылок (SRID).  
  
> [!NOTE]  
>  Методы, вызываемые для типа данных **geography** и вычисляющие площадь или расстояние, могут возвращать различные результаты в зависимости от идентификатора SRID экземпляра.   Дополнительные сведения об идентификаторах SRID см. в разделе [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере вычисляется расстояние между двумя экземплярами **geography**.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
