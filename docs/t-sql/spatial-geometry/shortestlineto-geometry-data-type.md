---
title: ShortestLineTo (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geometry)
ms.assetid: 39a2d0e4-4f93-4e94-a27e-6ad9537cfe74
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b5722110fc1ae00e8174078c735b15be0d0006bf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38004876"
---
# <a name="shortestlineto-geometry-data-type"></a>ShortestLineTo (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **LineString** с двумя точками, представляющий кратчайшее расстояние между двумя экземплярами **geometry**. Длина возвращаемого экземпляра **LineString** равна расстоянию между двумя экземплярами **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.ShortestLineTo ( geometry_other )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_other*  
 Второй экземпляр **geometry**, кратчайшее расстояние до которого пытается определить вызывающий экземпляр **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает экземпляр **LineString** с двумя конечными точками, лежащими на границах двух сравниваемых непересекающихся экземпляров **geometry**. Длина возвращаемого экземпляра **LineString** равна кратчайшему расстоянию между двумя экземплярами **geometry**. Пустой экземпляр **LineString** возвращается, когда два экземпляра **geometry** пересекаются друг с другом.  
  
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
 [ShortestLineTo (тип данных geography)](../../t-sql/spatial-geography/shortestlineto-geography-data-type.md)  
  
  

