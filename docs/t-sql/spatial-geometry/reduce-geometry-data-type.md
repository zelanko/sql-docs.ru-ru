---
title: "Уменьшить (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
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
- Reduce_TSQL
- Reduce
dev_langs: TSQL
helpviewer_keywords: Reduce method
ms.assetid: 132184bf-c4d2-4a27-900d-8373445dce2a
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fb6c4a66f3233620ef5d24506d41e7659fc3b82d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="reduce-geometry-data-type"></a>Reduce (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает приближение заданного **geometry** экземпляр создавались с помощью расширения алгоритма Дугласа-Пекера для экземпляра с заданным допуском.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *отказоустойчивость*  
 Значение типа **float**. *Отклонение* представляет собой допуск, который должен быть введен в алгоритм приближения.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Для типов коллекции этот алгоритм работает независимо для каждого **geometry** содержащиеся в экземпляре.  
  
 Этот алгоритм не изменяет **точки** экземпляров.  
  
 На **LineString**, **CircularString**, и **CompoundCurve** экземпляров, алгоритм приближения сохраняет исходные начальную и конечную точки экземпляра и итеративно обратно точку с исходный экземпляр в наибольшей степени отклоняется от результата, до точки, в которой отклонение становится меньше заданного допуска.  
  
 `Reduce()`Возвращает **LineString**, **CircularString**, или **CompoundCurve** экземпляра для **CircularString** экземпляров.  `Reduce()`Возвращает один **CompoundCurve** или **LineString** экземпляра для **CompoundCurve** экземпляров.  
  
 На **многоугольника** экземпляров, алгоритм приближения применяется независимо к каждому кольцу. Метод получит `FormatException` если возвращенный **многоугольника** экземпляр является недопустимым; например, недопустимый **MultiPolygon** экземпляр создается в том случае, если `Reduce()` применяется для упрощения каждого кольца в экземпляре, но результирующие кольца перекрываются.  На **CurvePolygon** экземпляры с внешним кольцом и без внутренних колец `Reduce()` возвращает **CurvePolygon**, **LineString**, или **точки** экземпляра.  Если **CurvePolygon** имеются внутренние кольца то **CurvePolygon** или **MultiPoint** возвращается экземпляр.  
  
 При обработке сегмента дуги алгоритм приближения проверяет, можно ли выполнить аппроксимацию дуги ее хордой в пределах половины значения допуска.  Если хорда соответствует этому критерию, то дуга в расчетах заменяется хордой. Если она не соответствует этому критерию, дуга сохраняется, а алгоритм приближения применяется к оставшимся сегментам.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-reduce-to-simplify-a-linestring"></a>A. Использование функции Reduce() для упрощения экземпляра LineString  
 В следующем примере создается экземпляр `LineString` и используется метод `Reduce()` для упрощения этого экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0, 2 1, 3 0, 4 1)', 0);  
SELECT @g.Reduce(.75).ToString();  
```  
  
### <a name="b-using-reduce-with-varying-tolerance-levels-on-a-circularstring"></a>Б. Использование функции Reduce() с разными уровнями допуска для экземпляра CircularString  
 В следующем примере используется `Reduce()` с тремя уровнями допуска для **CircularString** экземпляр:  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0)'; 
 SELECT @g.Reduce(5).ToString(); 
 SELECT @g.Reduce(15).ToString(); 
 SELECT @g.Reduce(16).ToString();
 ```  
  
 В примере получается следующий вывод.  
  
 ```
 CIRCULARSTRING (0 0, 8 8, 16 0, 20 -4, 24 0) 
 COMPOUNDCURVE (CIRCULARSTRING (0 0, 8 8, 16 0), (16 0, 24 0)) 
 LINESTRING (0 0, 24 0)
 ```  
  
 Каждый из возвращенных экземпляров содержит конечные точки (0 0) и (24 0).  
  
### <a name="c-using-reduce-with-varying-tolerance-levels-on-a-compoundcurve"></a>В. Использование функции Reduce() с разными уровнями допуска для экземпляра CompoundCurve  
 В следующем примере используется `Reduce()` с двумя уровнями допуска для **CompoundCurve** экземпляр:  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0),(24 0, 20 4, 16 0))';  
 SELECT @g.Reduce(15).ToString();  
 SELECT @g.Reduce(16).ToString();
 ```  
  
 Обратите внимание, что в этом примере второй **ВЫБЕРИТЕ** инструкция возвращает **LineString** экземпляр: `LineString(0 0, 16 0)`.  
  
### <a name="showing-an-example-where-the-original-start-and-end-points-are-lost"></a>Демонстрация примера, в котором исходные начальная и конечная точки потеряны.  
 В следующем примере показано, как исходные начальная и конечная точки могут не сохраняться в результирующем экземпляре. Это происходит потому, что сохранение исходных начальной и конечной точек приведет к созданию недопустимого **LineString** экземпляра.  
  
```  
DECLARE @g geometry = 'LINESTRING(0 0, 4 0, 2 .01, 1 0)';  
DECLARE @h geometry = @g.Reduce(1);  
SELECT @g.STIsValid() AS Valid  
SELECT @g.ToString() AS Original, @h.ToString() AS Reduced;  
```  
  
## <a name="see-also"></a>См. также  
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

