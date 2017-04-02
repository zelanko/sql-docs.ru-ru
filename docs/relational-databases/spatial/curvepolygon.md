---
title: "CurvePolygon | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e000a1d8-a049-4542-bfeb-943fd6ab3969
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# CurvePolygon
  **CurvePolygon** является топологически закрытой областью, определенной внешним ограничивающим кольцом, а также нулем или более внутренних колец.  
  
> [!IMPORTANT]  
>  Подробное описание и примеры использования возможностей обработки пространственных данных, добавленных в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], в том числе подтипа **CurvePolygon**, можно получить, скачав технический документ [Новые возможности обработки пространственных данных в SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407).  
  
 Следующие критерии определяют атрибуты экземпляра **CurvePolygon** .  
  
-   Границы экземпляра **CurvePolygon** определяются внешним кольцом и всеми внутренними кольцами.  
  
-   Внутреннее пространство экземпляра **CurvePolygon** ― это пространство между внешним кольцом и всеми внутренними кольцами.  
  
 Экземпляр **CurvePolygon** отличается от экземпляра **Polygon** тем, что экземпляр **CurvePolygon** может содержать следующие сегменты дуги: **CircularString** и **CompoundCurve**.  
  
## Экземпляры CompoundCurve  
 На следующей иллюстрации показаны допустимые фигуры **CurvePolygon** .  
  
### Правильные экземпляры  
 Чтобы экземпляр **CurvePolygon** был принят, он должен быть либо пустым, либо содержать только принимаемые кольца дуги. Принимаемое кольцо дуги удовлетворяет следующим требованиям.  
  
1.  Является принятым экземпляром **LineString**, **CircularString**или **CompoundCurve** . Дополнительные сведения о принятых экземплярах см. в разделах [LineString](../../relational-databases/spatial/linestring.md), [CircularString](../../relational-databases/spatial/circularstring.md)и [CompoundCurve](../../relational-databases/spatial/compoundcurve.md).  
  
2.  Имеет минимум четыре точки.  
  
3.  Начальная и конечная точки имеют одинаковые координаты X и Y.  
  
    > [!NOTE]  
    >  Значения Z и M пропускаются.  
  
 В следующем примере показаны принятые экземпляры **CurvePolygon** .  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0, 0 0))';  
DECLARE @g3 geometry = 'CURVEPOLYGON((0 0 1, 0 0 2, 0 0 3, 0 0 3))'  
DECLARE @g4 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
DECLARE @g5 geography = 'CURVEPOLYGON((-122.3 47, 122.3 -47, 125.7 -49, 121 -38, -122.3 47))';  
```  
  
 `@g3` принимается, несмотря на то что начальная и конечная точки имеют различные значения Z, поскольку значения Z не учитываются. `@g5` принимается, хотя экземпляр типа **geography** является недопустимым.  
  
 Следующие примеры вызывают исключение `System.FormatException`.  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON((0 5, 0 0, 0 0, 0 0))';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0))';  
```  
  
 `@g1` не принимается, поскольку не совпадают значения Y для начальной и конечной точек. `@g2` не принимается, поскольку кольцо содержит недостаточное число точек.  
  
### Допустимые экземпляры  
 Чтобы экземпляр **CurvePolygon** был допустимым, внешние и внутренние кольца должны удовлетворять следующим критериям.  
  
1.  Они могут соприкасаться только в одной точке касания.  
  
2.  Они не могут пересекать друг друга.  
  
3.  Каждое кольцо должно содержать минимум четыре точки.  
  
4.  Каждое кольцо должно принадлежать к приемлемому типу кривой.  
  
 Кроме того, экземпляры**CurvePolygon** должны удовлетворять особым критериям в зависимости от того, к какому типу данных они принадлежат, **geometry** или **geography** .  
  
#### Тип данных Geometry  
 Допустимый экземпляр **geometryCurvePolygon** должен иметь следующие атрибуты:  
  
1.  Все внутренние кольца должны находиться в пределах внешнего кольца.  
  
2.  Могут иметь несколько внутренних колец, но при этом одно внутреннее кольцо не может содержать другое внутреннее кольцо.  
  
3.  Кольцо не может пересекать само себя или другое кольцо.  
  
4.  Кольца могут соприкасаться только в одной точке (число точек, где точки соприкасаются, должно быть конечным).  
  
5.  Внутренняя часть многоугольника должна быть замкнутой.  
  
 В приведенном ниже примере показаны допустимые экземпляры **geometryCurvePolygon**.  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
 К экземплярам CurvePolygon применяются такие правила определения допустимости, как и к экземплярам Polygon, за исключением того, что экземпляры CurvePolygon могут принимать новые типы сегментов дуги. Дополнительные примеры допустимых и недопустимых экземпляров приведены в разделе [Polygon](../../relational-databases/spatial/polygon.md).  
  
#### Тип данных Geography  
 Допустимый экземпляр **geographyCurvePolygon** должен иметь следующие атрибуты:  
  
1.  Внутреннее пространство многоугольника соединяется с использованием правила левой руки.  
  
2.  Кольцо не может пересекать само себя или другое кольцо.  
  
3.  Кольца могут соприкасаться только в одной точке (число точек, где точки соприкасаются, должно быть конечным).  
  
4.  Внутренняя часть многоугольника должна быть замкнутой.  
  
 В следующем примере показан допустимый экземпляр CurvePolygon типа Geography.  
  
```  
DECLARE @g geography = 'CURVEPOLYGON((-122.3 47, 122.3 47, 125.7 49, 121 38, -122.3 47))';  
SELECT @g.STIsValid();  
```  
  
## Примеры  
  
### A. Создание экземпляра типа Geometry с пустым CurvePolygon  
 В этом примере показано, как создать пустой экземпляр **CurvePolygon** :  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON EMPTY');  
```  
  
### Б. Объявление и создание экземпляра типа Geometry с CurvePolygon в одной и той же инструкции  
 В этом фрагменте кода показывается объявление и инициализация экземпляра типа Geometry с **CurvePolygon** в одной инструкции.  
  
```tsql  
DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))'  
```  
  
### В. Создание экземпляра типа Geometry с CurvePolygon  
 На примере следующего фрагмента кода показано объявление и создание экземпляра **geography** с **CurvePolygon**.  
  
```tsql  
DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### Г. Сохранение CurvePolygon только с внешним ограничивающим кольцом  
 В этом примере показано сохранение простого круга в экземпляре **CurvePolygon** (для определения круга используется только внешнее ограничивающее кольцо):  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
### Д. Сохранение CurvePolygon с внутренними кольцами  
 В этом примере в экземпляре **CurvePolygon** создается бублик (для определения бублика используются как внешнее ограничивающее кольцо, так и внутреннее кольцо):  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
 В этом примере показано, как при использовании внутренних колец экземпляр **CurvePolygon** может быть допустимым и недопустимым.  
  
```tsql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (-2 2, 2 2, 2 -2, -2 -2, -2 2))');  
IF @g1.STIsValid() = 1  
  BEGIN  
     SELECT @g1.STArea();  
  END  
SET @g2 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (0 5, 5 0, 0 -5, -5 0, 0 5))');  
IF @g2.STIsValid() = 1  
  BEGIN  
     SELECT @g2.STArea();  
  END  
SELECT @g1.STIsValid() AS G1, @g2.STIsValid() AS G2;  
```  
  
 И в @g1, и в @g2 используется внешнее ограничивающее кольцо: круг с радиусом 5, а в качестве внутреннего кольцо в обоих экземплярах используется квадрат.  При этом экземпляр @g1 является допустимым, а @g2 ― нет.  Причина, по которой экземпляр @g2 является недопустимым, заключается в том, что внутреннее кольцо делит внутреннее пространство, ограниченное внешним кольцом, на четыре отдельные области.  На следующем чертеже показано, что произошло.  
  
## См. также:  
 [Многоугольник](../../relational-databases/spatial/polygon.md)   
 [CircularString](../../relational-databases/spatial/circularstring.md)   
 [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)   
 [Справочник по методам типа данных geometry](../Topic/geometry%20Data%20Type%20Method%20Reference.md)   
 [Справочник по методам типа данных geography](../Topic/geography%20Data%20Type%20Method%20Reference.md)   
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  