---
description: Reduce (тип данных geometry)
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
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 704df574cc67a4321faea90795b248adb2859123
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88445101"
---
# <a name="reduce-geometry-data-type"></a>Reduce (тип данных geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает аппроксимацию для указанного экземпляра **geometry**. Она вычисляется при помощи расширенного алгоритма Дугласа-Пекера с заданным допуском.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.Reduce ( tolerance )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *tolerance*  
 Значение типа **float**. Аргумент *tolerance* представляет собой допуск, который должен быть введен в алгоритм приближения.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Для типов коллекции этот алгоритм работает независимо для каждого экземпляра **geometry**, содержащегося в экземпляре.  
  
 Этот алгоритм не изменяет экземпляры **Point**.  
  
 Для экземпляров **LineString**, **CircularString** и **CompoundCurve** алгоритм аппроксимации сохраняет исходные начальную и конечную точки экземпляра. Затем алгоритм итеративно добавляет точки из изначальной кривой, наиболее далеко отстоящие от текущего аппроксимированного результата. Этот процесс продолжается до точки, отклонение которой меньше заданного допуска.  
  
 `Reduce()` возвращает экземпляр **LineString**, **CircularString** или **CompoundCurve** для экземпляров **CircularString**.  `Reduce()` возвращает экземпляр **CompoundCurve** или **LineString** для экземпляров **CompoundCurve**.  
  
 Для экземпляров **Polygon** алгоритм приближения применяется независимо к каждому кольцу. Этот метод вызывает исключение `FormatException`, если возвращаемый экземпляр **Polygon** недопустим. Например, недопустимый экземпляр **MultiPolygon** создается, если метод `Reduce()` применяется для упрощения всех кругов в экземпляре и результирующие круги перекрываются.  Для экземпляров **CurvePolygon** с внешним кругом и без внутренних `Reduce()` возвращает экземпляр **CurvePolygon**, **LineString** или **Point**.  Если экземпляр **CurvePolygon** имеет внутренние кольца, возвращается экземпляр **CurvePolygon** или **MultiPoint**.  
  
 При обнаружении сегмента дуги алгоритм проверяет, можно ли выполнить аппроксимацию дуги ее хордой в пределах половины заданного допуска. В хордах, соответствующих этому критерию, дуга в расчетах заменяется хордой. Если хорда не соответствует этому критерию, дуга сохраняется, а алгоритм применяется к оставшимся сегментам.  
  
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
  
 В этом примере выводятся следующие данные:  
  
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
 В следующем примере показано, как исходные начальная и конечная точки могут не сохраняться в результирующем экземпляре. Это происходит из-за того, что сохранение исходных начальной и конечной точек может сделать получившийся экземпляр **LineString** недопустимым.  
  
```  
DECLARE @g geometry = 'LINESTRING(0 0, 4 0, 2 .01, 1 0)';  
DECLARE @h geometry = @g.Reduce(1);  
SELECT @g.STIsValid() AS Valid  
SELECT @g.ToString() AS Original, @h.ToString() AS Reduced;  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
