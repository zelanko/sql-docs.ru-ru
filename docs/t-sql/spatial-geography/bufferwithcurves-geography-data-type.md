---
title: BufferWithCurves (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 08/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 45510220511ae8d487c8f2f961ab47274bb4fd26
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36259936"
---
# <a name="bufferwithcurves-geography-data-type"></a>BufferWithCurves (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Возвращает экземпляр **geography**, представляющий набор всех точек, расстояние которых от вызывающего экземпляра **geography** меньше параметра *distance* или равно ему.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *distance*  
 Имеет тип **float** и указывает максимальное расстояние, на котором точки, составляющие буфер, могут находиться от экземпляра geography.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Следующие критерии вызовут исключение **ArgumentException**.  
  
-   Методу, например `@g.BufferWithCurves()`, не передаются никакие параметры  
  
-   Методу, например `@g.BufferWithCurves('a')`, передается нечисловой параметр  
  
-   **NULL** передается методу, например `@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>Remarks  
 В следующей таблице показаны результаты, возвращенные для разных значений расстояния.  
  
|Значение расстояния|Измерения типа|Возвращенный пространственный тип|  
|--------------------|---------------------|---------------------------|  
|расстояние < 0|Ноль или один|Пустой экземпляр **GeometryCollection**|  
|расстояние \< 0|Два и более|Экземпляр **CurvePolygon** или **GeometryCollection** с отрицательным буфером.<br /><br /> Примечание. Отрицательный буфер может создать пустой экземпляр **GeometryCollection**|
|расстояние = 0|Все измерения|Копия вызывающего экземпляра **geography**|  
|расстояние > 0|Все измерения|Экземпляр **CurvePolygon** или **GeometryCollection**|  
  
> [!NOTE]  
>  Поскольку аргумент *distance* относится к типу **float**, в расчетах очень маленькое значение может быть приравнено к нулю.  Когда это происходит, возвращается копия вызывающего экземпляра **geography**.  
  
 Если методу передается параметр **string**, то он будет преобразован в тип **float** или возникнет исключение `ArgumentException`.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geography-instance"></a>A. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра одномерного географического объекта  
 В следующем примере возвращается пустой экземпляр `GeometryCollection`:  
  
 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(-1).ToString();
``` 
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geography-instance"></a>Б. Вызов метода BufferWithCurves() со значением параметра < 0 для экземпляра двухмерного географического объекта  
 В следующем примере возвращается экземпляр `CurvePolygon` с отрицательным буфером:  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>В. Вызов функции BufferWithCurves() со значением параметра < 0, которая возвращает пустую коллекцию GeometryCollection  
 Следующий пример демонстрирует, что происходит, когда параметр *distance* равняется –2:  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 Эта инструкция **SELECT** возвращает `GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>Г. Вызов функции BufferWithCurves() со значением параметра = 0  
 В следующем примере возвращается копия вызывающего экземпляра **geography**:  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>Д. Вызов функции BufferWithCurves() с ненулевым, но очень малым значением параметра  
 В следующем примере также возвращается копия вызывающего экземпляра **geography**:  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @distance float = 1e-20;  
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>Е. Вызов функции BufferWithCurves() со значением параметра > 0  
 В следующем примере возвращается экземпляр `CurvePolygon`:  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
### <a name="g-passing-a-valid-string-parameter"></a>Ж. Передача допустимого строкового параметра  
 В следующем примере возвращается тот же экземпляр `CurvePolygon`, который упоминался ранее, но методу передается строковый параметр:  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves('2').ToString();
```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>З. Передача недопустимого строкового параметра  
 В следующем примере возникнет ошибка:  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)'  
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 Обратите внимание на то, что в предыдущих двух примерах передавался строковый литерал методу `BufferWithCurves()`. Первый пример будет работать, поскольку строковый литерал может быть преобразован в числовое значение. Но во втором примере возникнет исключение `ArgumentException`.  
  
## <a name="see-also"></a>См. также:  
 [Расширенные методы в экземплярах Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [BufferWithCurves (тип данных geometry)](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
  
