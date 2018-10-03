---
title: Reduce (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: 132184bf-c4d2-4a27-900d-8373445dce2a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b3706237fdd673e4bcf42fbcc5e611e094fd1ebf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47805622"
---
# <a name="reduce-geometry-data-type"></a>Reduce (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает приближенное значение для указанного экземпляра **geometry**, полученное путем выполнения расширения алгоритма Дугласа-Пекера для экземпляра с заданным допуском.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *tolerance*  
 Значение типа **float**. Аргумент *tolerance* представляет собой допуск, который должен быть введен в алгоритм приближения.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Для типов коллекции этот алгоритм работает независимо для каждого экземпляра **geometry**, содержащегося в экземпляре.  
  
 Этот алгоритм не изменяет экземпляры **Point**.  
  
 Для экземпляров **LineString**, **CircularString** и **CompoundCurve** алгоритм приближения сохраняет исходные начальную и конечную точки экземпляра и итеративно выполняет суммирование в обратном направлении — от точки, начиная с которой исходный экземпляр в наибольшей степени отклоняется от результата, до точки, в которой отклонение становится меньше заданного допуска.  
  
 `Reduce()` возвращает экземпляр **LineString**, **CircularString** или **CompoundCurve** для экземпляров **CircularString**.  `Reduce()` возвращает экземпляр **CompoundCurve** или **LineString** для экземпляров **CompoundCurve**.  
  
 Для экземпляров **Polygon** алгоритм приближения применяется независимо к каждому кольцу. Этот метод вызывает исключение `FormatException`, если возвращаемый экземпляр **Polygon** является недопустимым. Недопустимый экземпляр **MultiPolygon** создается, например, если метод `Reduce()` применяется в целях упрощения каждого кольца в экземпляре, но результирующие кольца перекрываются.  Для экземпляров **CurvePolygon** с внешним кольцом, но без внутренних колец `Reduce()` возвращает экземпляр **CurvePolygon**, **LineString** или **Point**.  Если экземпляр **CurvePolygon** имеет внутренние кольца, возвращается экземпляр **CurvePolygon** или **MultiPoint**.  
  
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
 В приведенном ниже примере используется функция `Reduce()` с тремя уровнями допуска для экземпляра **CircularString**.  
  
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
 В приведенном ниже примере используется функция `Reduce()` с двумя уровнями допуска для экземпляра **CompoundCurve**.  
  
```
 DECLARE @g geometry = 'COMPOUNDCURVE(CIRCULARSTRING(0 0, 8 8, 16 0, 20 -4, 24 0),(24 0, 20 4, 16 0))';  
 SELECT @g.Reduce(15).ToString();  
 SELECT @g.Reduce(16).ToString();
 ```  
  
 В этом примере обратите внимание, что вторая инструкция **SELECT** возвращает экземпляр **LineString**: `LineString(0 0, 16 0)`.  
  
### <a name="showing-an-example-where-the-original-start-and-end-points-are-lost"></a>Демонстрация примера, в котором исходные начальная и конечная точки потеряны.  
 В следующем примере показано, как исходные начальная и конечная точки могут не сохраняться в результирующем экземпляре. Это происходит из-за того, что сохранение исходных начальной и конечной точек приведет к созданию недопустимого экземпляра **LineString**.  
  
```  
DECLARE @g geometry = 'LINESTRING(0 0, 4 0, 2 .01, 1 0)';  
DECLARE @h geometry = @g.Reduce(1);  
SELECT @g.STIsValid() AS Valid  
SELECT @g.ToString() AS Original, @h.ToString() AS Reduced;  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

