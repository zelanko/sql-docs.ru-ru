---
title: STBuffer (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBuffer (geometry Data Type)
- STBuffer_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBuffer (geometry Data Type)
ms.assetid: ca6bf2dc-1d38-4503-b87e-f2ea033d36ba
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 8d49fa09e703c186664a46f1daa8fe0b6283d33b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939084"
---
# <a name="stbuffer-geometry-data-type"></a>STBuffer (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает геометрический объект, представляющий объединение всех точек, расстояние которых от экземпляра **geometry** меньше или равно указанному значению.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>Аргументы  
 *distance*  
 Значение типа **float** (**double** в .NET Framework), указывающее расстояние от геометрического объекта, вокруг которого вычисляется буфер.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Метод `STBuffer()` вычисляет буфер аналогично методу [BufferWithTolerance](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md), задавая аргументы *tolerance* = distance \* 0,001 и *relative* = **false**.  
  
 Когда *distance* > 0, возвращается экземпляр **Polygon** или **MultiPolygon**.  
  
> [!NOTE]  
>  Поскольку аргумент distance относится к типу **float**, в расчетах очень маленькое значение может быть приравнено к нулю.  Когда это происходит, возвращается экземпляр **geometry**.  См. раздел [Типы данных float и real (Transact-SQL)](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 Когда *distance* = 0, возвращается копия вызывающего экземпляра **geometry**.  
  
 Когда *distance* < 0, то  
  
-   возвращается пустой экземпляр **GeometryCollection**, если измерения экземпляра — 0 или 1.  
  
-   возвращается отрицательный буфер, если измерения экземпляра — 2 или более.  
  
    > [!NOTE]  
    >  Отрицательный буфер может также создать пустой экземпляр **GeometryCollection**.  
  
 Отрицательный буфер удаляет все точки в пределах указанного расстояния от границы геометрического объекта.  
  
 Ошибкой между теоретическим и вычисляемым буфером является max(tolerance, extents * 1.E-7), где tolerance = distance \* 0,001. Дополнительные сведения об экстентах см. в статье [Справочник по методам типа данных geometry](https://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7).  
  
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
>  Возвращается экземпляр `Polygon` вместо экземпляра `CurvePolygon`.  Сведения о возвращении экземпляра `CurvePolygon` см. в статье [BufferWithCurves (тип данных geometry)](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md).  
  
### <a name="d-calling-stbuffer-with-a-negative-parameter-value-that-returns-an-empty-instance"></a>Г. Вызов метода STBuffer() с отрицательным значением параметра, возвращающего пустой экземпляр  
 В следующем примере показано, что произойдет, если параметр *distance* равен –2 для предыдущего примера.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.STBuffer(-2).ToString();
 ```  
  
 Эта инструкция **SELECT** возвращает значение `GEOMETRYCOLLECTION EMPTY.`.  
  
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
  
 Первые две инструкции **SELECT** возвращают экземпляр `MultiPolygon`, поскольку параметр *distance* меньше или равен 1/2 расстояния между двумя точками (1 1) и (1 4). Третья инструкция **SELECT** возвращает экземпляр `Polygon`, поскольку находящиеся в буферной памяти экземпляры двух точек (1 1) и (1 4) перекрываются.  
  
## <a name="see-also"></a>См. также:  
 [BufferWithTolerance (тип данных geometry)](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

