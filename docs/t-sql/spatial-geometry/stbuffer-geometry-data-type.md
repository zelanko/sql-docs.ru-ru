---
title: "STBuffer (тип данных geometry) | Документы Microsoft"
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
- STBuffer (geometry Data Type)
- STBuffer_TSQL
dev_langs: TSQL
helpviewer_keywords: STBuffer (geometry Data Type)
ms.assetid: ca6bf2dc-1d38-4503-b87e-f2ea033d36ba
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb93bd550570b94b1a924a20d6243e808209adec
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stbuffer-geometry-data-type"></a>STBuffer (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает геометрический объект, представляющий объединение всех точек, расстояние которых от **geometry** экземпляр меньше или равно указанному значению.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *расстояние*  
 Значение типа **float** (**двойные** в платформе .NET Framework) указывающее расстояние от экземпляра геометрического объекта, вокруг которого вычисляется буфер.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 `STBuffer()`Вычисляет буфер аналогично [BufferWithTolerance](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md), указав *отклонения* = distance \* .001 и *относительный*  =   **false**.  
  
 Когда *расстояние* > 0, то **многоугольника** или **MultiPolygon** возвращается экземпляр.  
  
> [!NOTE]  
>  Поскольку аргумент distance относится **float**, очень маленькое значение может быть приравнено к нулю в вычислениях.  Когда это происходит, копия вызывающего **geometry** возвращается экземпляр.  В разделе [float и real &#40; Transact-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)  
  
 Когда *расстояние* = 0, то копия вызывающего **geometry** возвращается экземпляр.  
  
 Когда *расстояние* < 0, то  
  
-   Пустой **GeometryCollection** экземпляр возвращается в том случае, если измерений экземпляра 0 или 1.  
  
-   возвращается отрицательный буфер, если измерения экземпляра — 2 или более.  
  
    > [!NOTE]  
    >  Отрицательный буфер может также создать пустой **GeometryCollection** экземпляра.  
  
 Отрицательный буфер удаляет все точки в пределах указанного расстояния от границы геометрического объекта.  
  
 Ошибкой между теоретическим и рассчитанным буфером является max (погрешность, экстентов * 1.E-7) где отклонение = distance \* .001. Дополнительные сведения об экстентах см. в разделе [Справочник по методам типа данных geometry](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-stbuffer-with-parametervalue--0-on-one-dimensional-geometry-instance"></a>A. Вызов метода STBuffer() с parameter_value < 0 для экземпляра одномерного геометрического объекта  
 В следующем примере возвращается пустой экземпляр `GeometryCollection`:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer(-1).ToString();
 ```  
  
### <a name="b-calling-stbuffer-with-parametervalue--0-on-a-polygon-instance"></a>Б. Вызов метода STBuffer() с parameter_value < 0 для экземпляра объекта Polygon  
 В следующем примере возвращается экземпляр `Polygon` с отрицательным буфером:  
  
```
 DECLARE @g geometry = 'POLYGON((1 1, 1 5, 5 5, 5 1, 1 1))'; 
 SELECT @g.STBuffer(-1).ToString();
 ```  
  
### <a name="c-calling-stbuffer-with-parametervalue--0-on-a-curvepolygon-instance"></a>В. Вызов метода STBuffer() с parameter_value < 0 для экземпляра объекта CurvePolygon  
 В следующем примере возвращается экземпляр `Polygon` с отрицательным буфером из экземпляра `CurvePolygon`:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.STBuffer(-1).ToString();
 ```  
  
> [!NOTE]  
>  Возвращается экземпляр `Polygon` вместо экземпляра `CurvePolygon`.  Чтобы вернуть `CurvePolygon` см. в разделе [BufferWithCurves &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
### <a name="d-calling-stbuffer-with-a-negative-parameter-value-that-returns-an-empty-instance"></a>Г. Вызов метода STBuffer() с отрицательным значением параметра, возвращающего пустой экземпляр  
 В следующем примере показано, что происходит при *расстояние* параметр равен -2 для предыдущего примера.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.STBuffer(-2).ToString();
 ```  
  
 Это **ВЫБЕРИТЕ** инструкция возвращает`GEOMETRYCOLLECTION EMPTY.`  
  
### <a name="e-calling-stbuffer-with-parametervalue--0"></a>Д. Вызов метода STBuffer() с parameter_value = 0  
 В следующем примере возвращается копия вызывающего экземпляра `geometry`:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer(0).ToString();
 ```  
  
### <a name="f-calling-stbuffer-with-a-non-zero-parameter-value-that-is-extremely-small"></a>Е. Вызов метода STBuffer() с ненулевым, но очень малым значением параметра  
 В следующем примере также возвращается копия вызывающего экземпляра `geometry`:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)';  
 DECLARE @distance float = 1e-20;  
 SELECT @g.STBuffer(@distance).ToString();
 ```  
  
### <a name="g-calling-stbuffer-with-parametervalue--0"></a>Ж. Вызов метода STBuffer() с parameter_value > 0  
 В следующем примере возвращается экземпляр `Polygon`:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer(2).ToString();
 ```  
  
### <a name="h-calling-stbuffer-with-a-string-parameter-value"></a>З. Вызов метода STBuffer() со строковым значением параметра  
 В следующем примере возвращается тот же экземпляр `Polygon`, который упоминался ранее, но методу передается строковый параметр:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer('2').ToString();
 ```  
  
 В следующем примере возникнет ошибка:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer('a').ToString();
 ```  
  
> [!NOTE]  
>  В предыдущих двух примерах методу `STBuffer()` был передан строковый литерал.  Первый пример будет работать, поскольку строковый литерал может быть преобразован в числовое значение. Но во втором примере возникнет исключение `ArgumentException`.  
  
### <a name="i-calling-stbuffer-on-a-multipoint-instance"></a>И. Вызов метода STBuffer() для экземпляра объекта MultiPoint  
 Следующий пример возвращает два экземпляра `MultiPolygon` и один экземпляр `Polygon`:  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.STBuffer(1).ToString(); 
 SELECT @g.STBuffer(1.5).ToString(); 
 SELECT @g.STBuffer(1.6).ToString();
 ```  
  
 Первые два **ВЫБЕРИТЕ** инструкции возвращают `MultiPolygon` экземпляра, так как параметр *расстояние* меньше или равен 1/2 расстояния между двумя точками (1 1) и (1-4). Третий **ВЫБЕРИТЕ** инструкция возвращает `Polygon` экземпляра, так как помещенные в буфер экземпляры двух точек (1 1) и (1-4) перекрываются.  
  
## <a name="see-also"></a>См. также:  
 [BufferWithTolerance &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

