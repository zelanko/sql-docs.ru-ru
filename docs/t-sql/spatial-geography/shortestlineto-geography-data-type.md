---
title: "ShortestLineTo (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ShortestLineTo_TSQL
- ShortestLineTo
dev_langs: TSQL
helpviewer_keywords: ShortestLineTo method (geography)
ms.assetid: 9d7c9885-5d1b-49ae-af31-5ef9fb8acaba
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b920113686547966cb67e31fc3f726ffbefba67
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="shortestlineto-geography-data-type"></a>ShortestLineTo (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает **LineString** экземпляра с двумя точками, представляющий кратчайшее расстояние между двумя **geography** экземпляров. Длина **LineString** возвращаемый экземпляр — это расстояние между двумя **geography** экземпляров.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ShortestLineTo ( geography_other )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_other*  
 Указывает второй **geography** экземпляр, вызывающий **geography** пытается определить кратчайшее расстояние до экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Метод возвращает **LineString** экземпляр с конечными точками, лежащими на границах двух непересекающиеся **geography** сравниваемых экземпляров. Длина **LineString** возвращаемый равна кратчайшему расстоянию между двумя **geography** экземпляров. Пустой **LineString** экземпляр возвращается, когда два **geography** пересекаются друг с другом.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Вызов функции ShortestLineTo() для непересекающихся экземпляров  
 В этом примере ищется кратчайшее расстояние между экземпляром `CircularString` и экземпляром `LineString` и возвращается экземпляр `LineString`, соединяющий эти две точки:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>Б. Вызов функции ShortestLineTo() для пересекающихся экземпляров  
 Этот пример возвращает пустой экземпляр `LineString`, поскольку экземпляр `LineString` пересекает экземпляр `CircularString`:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.348 47.649, -122.681 47.655)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
``` 
  
## <a name="see-also"></a>См. также  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
