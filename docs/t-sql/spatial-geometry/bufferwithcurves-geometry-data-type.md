---
title: "BufferWithCurves (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
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
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithCurves method (geometry)
ms.assetid: 8ffaba3f-d2dd-4e57-9f41-3ced9f14b600
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a88ea4010ec1cfd48661b34e990634fe371141f3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithcurves-geometry-data-type"></a>BufferWithCurves (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Возвращает **geometry** экземпляр, представляющий набор всех точек, расстояние которых от вызывающего **geometry** экземпляр меньше или равно *расстояние* параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *расстояние*  
 — **Float** указывает максимальное расстояние, на котором точки, составляющие буфер может быть из **geometry** экземпляра.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
Возвращаемый тип SQL Server: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="exceptions"></a>Исключения  
 Следующие критерии вызовут исключение **ArgumentException**.  
  
-   Методу, такому как `@g.BufferWithCurves()`, не передаются никакие параметры  
  
-   Методу, например `@g.BufferWithCurves('a')`, передается нечисловой параметр  
  
-   **Значение NULL** передается методу, например`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Замечания  
 На следующем рисунке показан пример экземпляра объекта геометрии (geometry), возвращенного этим методом.  
  
 ![BufferedCurve](../../t-sql/spatial-geometry/media/bufferedcurve.gif)
  
 В следующей таблице показаны результаты, возвращенные для разных значений расстояния.  
  
|Значение расстояния|Измерения типа|Возвращенный пространственный тип|  
|--------------------|---------------------|---------------------------|  
|расстояние < 0|Ноль или один|Пустой **GeometryCollection** экземпляра|  
|расстояние < 0|Два и более|Объект **CurvePolygon** или **GeometryCollection** с отрицательным буфером. **Примечание:** отрицательный буфер может создать пустой **GeometryCollection**|  
|расстояние = 0|Все измерения|Копия вызывающего **geometry** экземпляра|  
|расстояние > 0|Все измерения|**CurvePolygon** или **GeometryCollection** экземпляра|  
  
> [!NOTE]  
>  Поскольку *расстояние* — **float**, очень маленькое значение может быть приравнено к нулю в вычислениях. Когда это происходит копия вызывающего **geometry** возвращается экземпляр. В разделе [float и real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Отрицательный буфер удаляет все точки в пределах указанного расстояния от границы геометрического объекта. На следующей иллюстрации отрицательный буфер показан в виде области круга со светлой тенью. Пунктирная линия — это граница первоначального многоугольника, а сплошная линия — граница получаемого многоугольника.  
  
 Если **строка** параметр передается методу, а затем преобразуется в **float** или возникнет исключение `ArgumentException`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geometry-instance"></a>A. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра одномерного геометрического объекта  
 В следующем примере возвращается пустой экземпляр `GeometryCollection`:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(-1).ToString(); 
 ```
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geometry-instance"></a>Б. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра двумерного геометрического объекта  
 В следующем примере возвращается экземпляр `CurvePolygon` с отрицательным буфером:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>В. Вызов функции BufferWithCurves() со значением параметра < 0, которая возвращает пустую коллекцию GeometryCollection  
 В следующем примере показано, что происходит при *расстояние* параметр равен -2:  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 Это **ВЫБЕРИТЕ** инструкция возвращает`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>Г. Вызов функции BufferWithCurves() со значением параметра = 0  
 В следующем примере возвращается копия вызывающего **geometry** экземпляр:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>Д. Вызов функции BufferWithCurves() с ненулевым, но очень малым значением параметра  
 В следующем примере также возвращается копия вызывающего **geometry** экземпляр:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 DECLARE @distance float = 1e-20; 
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>Е. Вызов функции BufferWithCurves() со значением параметра > 0  
 В следующем примере возвращается экземпляр `CurvePolygon`:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
  
### <a name="g-passing-a-valid-string-parameter"></a>Ж. Передача допустимого строкового параметра  
 В следующем примере возвращается тот же экземпляр `CurvePolygon`, который упоминался ранее, но методу передается строковый параметр:  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves('2').ToString();
 ```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>З. Передача недопустимого строкового параметра  
 В следующем примере возникнет ошибка:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)' 
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 Обратите внимание на то, что в предыдущих двух примерах передавался строковый литерал методу `BufferWithCurves()`. Первый пример будет работать, поскольку строковый литерал может быть преобразован в числовое значение. Но во втором примере возникнет исключение `ArgumentException`.  
  
### <a name="i-calling-bufferwithcurves-on-multipoint-instance"></a>И. Вызов метода BufferWithCurves() для экземпляра объекта MultiPoint  
 Следующий пример возвращает два экземпляра `GeometryCollection` и один экземпляр `CurvePolygon`:  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.BufferWithCurves(1).ToString(); 
 SELECT @g.BufferWithCurves(1.5).ToString(); 
 SELECT @g.BufferWithCurves(1.6).ToString();
 ```  
  
 Первые два **ВЫБЕРИТЕ** инструкции возвращают `GeometryCollection` экземпляра, так как параметр *расстояние* меньше или равен 1/2 расстояния между двумя точками (1 1) и (1-4). Третий **ВЫБЕРИТЕ** инструкция возвращает `CurvePolygon` экземпляра, так как помещенные в буфер экземпляры двух точек (1 1) и (1-4) перекрываются.  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
 

