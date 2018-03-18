---
title: "STDisjoint (тип данных geography) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDisjoint (geography Data Type)
- STDisjoint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDisjoint
ms.assetid: 98328a02-e018-47d6-aa93-de162b8aef62
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a81d42abbc9a15068e1d58d5bb7222defbfc8042
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stdisjoint-geography-data-type"></a>STDisjoint (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает 1, если экземпляр **geography** не имеет пространственного перекрытия с другим экземпляром **geography**. В противном случае возвращается значение 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDisjoint ( other_geography )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geography*  
 Другой экземпляр **geography** для сравнения с экземпляром, для которого вызван метод STDisjoint().  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Два экземпляра **geography** не имеют перекрывающегося пространственного перекрытия, если пересечение их наборов точек является пустым.  
  
 Этот метод всегда возвращает значение NULL, если у экземпляров **geography** не совпадают идентификаторы пространственных ссылок (SRID).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `STDisjoint()`, чтобы протестировать два экземпляра `geography` и выяснить отсутствие пространственного перекрытия между ними.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDisjoint(@h);  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
