---
title: "ShortestLineTo (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geometry)
ms.assetid: 39a2d0e4-4f93-4e94-a27e-6ad9537cfe74
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc8843ceefe8819d2f314d76b019720863866ed1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="shortestlineto-geometry-data-type"></a>ShortestLineTo (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает **LineString** экземпляра с двумя точками, представляющий кратчайшее расстояние между двумя **geometry** экземпляров. Длина **LineString** возвращаемый экземпляр — это расстояние между двумя **geometry** экземпляров.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ShortestLineTo ( geometry_other )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_other*  
 Второй **geometry** экземпляр, вызывающий **geometry** пытается определить кратчайшее расстояние до экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 Метод возвращает **LineString** экземпляр с конечными точками, лежащими на границах двух непересекающиеся **geometry** сравниваемых экземпляров. Длина **LineString** возвращаемый равна кратчайшему расстоянию между двумя **geometry** экземпляров. Пустой **LineString** экземпляр возвращается, когда два **geometry** пересекаются друг с другом.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Вызов функции ShortestLineTo() для непересекающихся экземпляров  
 В этом примере ищется кратчайшее расстояние между экземпляром `CircularString` и экземпляром `LineString` и возвращается экземпляр `LineString`, соединяющий эти две точки:  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(-4 7, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>Б. Вызов функции ShortestLineTo() для пересекающихся экземпляров  
 Этот пример возвращает пустой экземпляр `LineString`, поскольку экземпляр `LineString` пересекает экземпляр `CircularString`:  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(0 5, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
## <a name="see-also"></a>См. также:  
 [ShortestLineTo &#40; тип данных geography &#41;](../../t-sql/spatial-geography/shortestlineto-geography-data-type.md)  
  
  


