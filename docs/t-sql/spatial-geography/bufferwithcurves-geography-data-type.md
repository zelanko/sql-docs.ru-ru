---
title: "BufferWithCurves (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 08/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BufferWithCurves
- BufferWithCurves_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithCurves method (geography)
ms.assetid: abf0a11c-c99c-4faa-bf80-3ae8e04d7bfb
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 80f16777999a029e1063305a0d1b8501af7e05d7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithcurves-geography-data-type"></a>BufferWithCurves (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает **geography** экземпляр, представляющий набор всех точек, расстояние которых от вызывающего **geography** экземпляр меньше или равно *расстояние* параметр.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *расстояние*  
 — **Float** указывает максимальное расстояние, на котором точки, составляющие буфер, могут находиться от экземпляра географического объекта.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Следующие критерии вызовут исключение **ArgumentException**.  
  
-   Методу, например `@g.BufferWithCurves()`, не передаются никакие параметры  
  
-   Методу, например `@g.BufferWithCurves('a')`, передается нечисловой параметр  
  
-   **Значение NULL** передается методу, например`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице показаны результаты, возвращенные для разных значений расстояния.  
  
|Значение расстояния|Измерения типа|Возвращенный пространственный тип|  
|--------------------|---------------------|---------------------------|  
|расстояние < 0|Ноль или один|Пустой **GeometryCollection** экземпляра|  
|расстояние \< 0|Два и более|Объект **CurvePolygon** или **GeometryCollection** с отрицательным буфером.<br /><br /> Примечание: Отрицательный буфер может создать пустой **GeometryCollection**|
|расстояние = 0|Все измерения|Копия вызывающего **geography** экземпляра|  
|расстояние > 0|Все измерения|**CurvePolygon** или **GeometryCollection** экземпляра|  
  
> [!NOTE]  
>  Поскольку *расстояние* — **float**, очень маленькое значение может быть приравнено к нулю в вычислениях.  Когда это происходит, затем копия вызывающего **geography** возвращается экземпляр.  
  
 Если **строка** параметр передается методу, а затем преобразуется в **float** или возникнет исключение `ArgumentException`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geography-instance"></a>A. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра одномерного географического объекта  
 В следующем примере возвращается пустой экземпляр `GeometryCollection`:  
  
 `DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `SELECT @g.BufferWithCurves(-1).ToString();`  
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geography-instance"></a>Б. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра двухмерного географического объекта  
 В следующем примере возвращается экземпляр `CurvePolygon` с отрицательным буфером:  
  
 `DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';`  
  
 `SELECT @g.BufferWithCurves(-1).ToString()`  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>В. Вызов функции BufferWithCurves() со значением параметра < 0, которая возвращает пустую коллекцию GeometryCollection  
 В следующем примере показано, что происходит при *расстояние* параметр равен -2:  
  
 `DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';`  
  
 `SELECT @g.BufferWithCurves(-2).ToString();`  
  
 Это **ВЫБЕРИТЕ** инструкция возвращает`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>Г. Вызов функции BufferWithCurves() со значением параметра = 0  
 В следующем примере возвращается копия вызывающего **geography** экземпляр:  
  
 `DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `SELECT @g.BufferWithCurves(0).ToString();`  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>Д. Вызов функции BufferWithCurves() с ненулевым, но очень малым значением параметра  
 В следующем примере также возвращается копия вызывающего **geography** экземпляр:  
  
 `DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `DECLARE @distance float = 1e-20;`  
  
 `SELECT @g.BufferWithCurves(@distance).ToString();`  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>Е. Вызов функции BufferWithCurves() со значением параметра > 0  
 В следующем примере возвращается экземпляр `CurvePolygon`:  
  
 `DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `SELECT @g.BufferWithCurves(2).ToString();`  
  
### <a name="g-passing-a-valid-string-parameter"></a>Ж. Передача допустимого строкового параметра  
 В следующем примере возвращается тот же экземпляр `CurvePolygon`, который упоминался ранее, но методу передается строковый параметр:  
  
 `DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';`  
  
 `SELECT @g.BufferWithCurves('2').ToString();`  
  
### <a name="h-passing-an-invalid-string-parameter"></a>З. Передача недопустимого строкового параметра  
 В следующем примере возникнет ошибка:  
  
 `DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)'`  
  
 `SELECT @g.BufferWithCurves('a').ToString();`  
  
 Обратите внимание на то, что в предыдущих двух примерах передавался строковый литерал методу `BufferWithCurves()`. Первый пример будет работать, поскольку строковый литерал может быть преобразован в числовое значение. Но во втором примере возникнет исключение `ArgumentException`.  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах географических объектов](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [BufferWithCurves &#40; тип данных geometry &#41;](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
  

