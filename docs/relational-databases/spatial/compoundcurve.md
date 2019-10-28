---
title: CompoundCurve | Документация Майкрософт
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a063a2a00ba67640b6a36a43abda2ea9eb45025d
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909211"
---
# <a name="compoundcurve"></a>CompoundCurve
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Объект **CompoundCurve** — это набор из нуля или большего количества непрерывных экземпляров **CircularString** или **LineString** геометрического или географического типов.  
  
> [!IMPORTANT]  
>  Подробное описание и примеры использования новых возможностей обработки пространственных данных в этом выпуске, включая подтип **CompoundCurve** , можно получить, скачав технический документ [Новые возможности обработки пространственных данных в SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).  
  
 Можно создать пустой экземпляр **CompoundCurve** , но, чтобы экземпляр **CompoundCurve** был допустимым, он должен удовлетворять следующим требованиям.  
  
1.  Должен содержать хотя бы один экземпляр **CircularString** или **LineString** .  
  
2.  Последовательность экземпляров **CircularString** или **LineString** должна быть непрерывной.  

Если объект **CompoundCurve** содержит последовательность из нескольких экземпляров **CircularString** и **LineString** , то конечная точка каждого экземпляра, кроме последнего, должна быть начальной конечной точкой следующего экземпляра в последовательности. Это означает, что, если конечная точка предыдущего экземпляра в последовательности — (4 3 7 2), начальной точкой следующего экземпляра в последовательности также должна быть (4 3 7 2). Обратите внимание, что значения Z (высота) и M (мера) этих точек также должны совпадать. Если такие две точки отличаются друг от друга, формируется исключение `System.FormatException` . Точки в объектах **CircularString** могут не иметь значение Z или M. Если значения Z или M не заданы для конечной точки предыдущего экземпляра, начальная точка следующего экземпляра также не может иметь значения Z или M. Если конечная точка для предыдущей последовательности — (4 3), начальной точкой для следующей последовательности также должна быть (4 3) и не может быть (4 3 7 2). Все точки в экземпляре **CompoundCurve** должны либо не иметь значения Z, либо иметь одинаковые значения Z.  
  
## <a name="compoundcurve-instances"></a>Экземпляры CompoundCurve  
На следующей иллюстрации показаны допустимые типы **CompoundCurve** .  
  
![f278742e-b861-4555-8b51-3d972b7602bf](../../relational-databases/spatial/media/f278742e-b861-4555-8b51-3d972b7602bf.gif)  
 
### <a name="accepted-instances"></a>Правильные экземпляры  
 Экземпляр**CompoundCurve** является правильным, если он пустой или удовлетворяет следующим требованиям.  
  
1.  Все экземпляры, содержащиеся в **CompoundCurve** , — это правильные экземпляры сегментов окружности. Дополнительные сведения о допустимых экземплярах сегментов окружности см. в разделах [LineString](../../relational-databases/spatial/linestring.md) и [CircularString](../../relational-databases/spatial/circularstring.md).  
  
2.  Все сегменты окружности в экземпляре **CompoundCurve** соединены. Первая точка каждого последующего сегмента совпадает с последней точкой предыдущего сегмента.  
  
    > [!NOTE]  
    > Это касается и координат Z и M. То есть все четыре координаты (X, Y, Z и M) должны быть одинаковыми.  
  
3.  Ни один из вложенных экземпляров не является пустым.  
  
В следующем примере показаны принятые экземпляры **CompoundCurve** .  
  
```sql  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
```  
  
В следующем примере показаны неправильные экземпляры **CompoundCurve** . Эти экземпляры формируют исключение `System.FormatException`.  
  
```sql  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';  
```  
  
### <a name="valid-instances"></a>Допустимые экземпляры  
 Экземпляр **CompoundCurve** допустим, если удовлетворяет следующим требованиям.  
  
1.  Экземпляр **CompoundCurve** является правильным.  
  
2.  Все экземпляры сегментов окружности, содержащиеся в экземпляре **CompoundCurve** , допустимы.  
  
В следующем примере показаны допустимые экземпляры **CompoundCurve** .  
  
```sql  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
`@g3` допустим, так как допустим экземпляр **CircularString** . Дополнительные сведения о допустимости экземпляра **CircularString** см. в разделе [CircularString](../../relational-databases/spatial/circularstring.md).  
  
В следующем примере показаны недопустимые экземпляры **CompoundCurve** .  
  
```sql  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';  
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
`@g1` недопустим, поскольку второй экземпляр не является допустимым LineString. `@g2` недопустим, так как недопустим экземпляр **LineString** . `@g3` недопустим, так как недопустим экземпляр **CircularString** . Дополнительные сведения о допустимых экземплярах **CircularString** и **LineString** см. в разделах [CircularString](../../relational-databases/spatial/circularstring.md) и [LineString](../../relational-databases/spatial/linestring.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a>A. Создание экземпляра geometry с пустым экземпляром CompoundCurve  
 В следующем примере показано, как создать пустой экземпляр `CompoundCurve` .  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a>Б. Объявление и создание экземпляра geometry с экземпляром CompoundCurve в одной инструкции  
 В следующем примере показано, как объявить и инициализировать экземпляр `geometry` с `CompoundCurve`в одной инструкции:  
  
```sql  
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a>В. Создание экземпляра geography с экземпляром CompoundCurve  
 В следующем примере показано объявление и инициализация экземпляра **geography** с `CompoundCurve`:  
  
```sql  
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a>Г. Хранение квадрата в экземпляре CompoundCurve  
 В следующем примере показаны два способа использования экземпляра `CompoundCurve` для хранения квадрата.  
  
```sql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');  
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');  
SELECT @g1.STLength(), @g2.STLength();  
```  
  
 Длина экземпляров `@g1` и `@g2` одинакова. На этом примере видно, что в экземпляре **CompoundCurve** может храниться один или несколько экземпляров `LineString`.  
  
### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a>Д. Создание экземпляра geometry с помощью экземпляра CompoundCurve с несколькими экземплярами CircularString  
 В следующем примере показано, как использовать два разных экземпляра `CircularString` для инициализации `CompoundCurve`.  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT @g.STLength();  
```  
  
В результате получается следующий вывод: `12.5663706143592` Это эквивалентно 4∏. Экземпляр `CompoundCurve` в этом примере хранит окружность с радиусом 2. В двух предыдущих примерах кода использование экземпляра `CompoundCurve`не требовалось. В первом примере было бы проще использовать экземпляр `LineString` , а во втором было бы проще использовать экземпляр `CircularString` . В следующем примере показано, когда следует использовать экземпляр `CompoundCurve` .  
  
### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a>Е. Использование экземпляра CompoundCurve для хранения полуокружности  
 В следующем примере экземпляр `CompoundCurve` используется для хранения полукруга.  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');  
SELECT @g.STLength();  
```  
  
### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a>Ж. Хранение нескольких экземпляров CircularString и LineString в экземпляре CompoundCurve  
 В следующем примере показано, как можно хранить несколько экземпляров `CircularString` и `LineString` с помощью `CompoundCurve`.  
  
```sql  
DECLARE @g geometry  
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');  
SELECT @g.STLength();  
```  
  
### <a name="h-storing-instances-with-z-and-m-values"></a>З. Хранение экземпляров со значениями Z и M  
 В следующем примере показано, как использовать экземпляр `CompoundCurve` для хранения последовательности экземпляров `CircularString` и `LineString` со значениями Z и M.  
  
```sql  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');  
```  
  
### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a>И. Почему необходимо объявлять экземпляры CircularString явно  
 В следующем примере показано, почему экземпляры `CircularString` должны быть явно объявлены. Программист желает хранить окружность в экземпляре `CompoundCurve` .  
  
```sql  
DECLARE @g1 geometry;    
DECLARE @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');  
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount  
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```  
Circle One11.940039...  
Circle Two12.566370...  
```  
  
Периметр окружности 2 равен примерно 4∏, что является фактическим значением для периметра. Напротив, значение периметра окружности 1 очень неточное. Экземпляр `CompoundCurve` окружности 1 хранит один сегмент окружности (ABC) и два линейных сегмента (CD, DA). Экземпляр `CompoundCurve` должен хранить два сегмента окружности (ABC, CDA), чтобы определять окружности. Экземпляр `LineString` определяет второй набор точек (4 2, 2 4, 0 2) в экземпляре `CompoundCurve` окружности 1. Необходимо явно объявить экземпляр `CircularString` в экземпляре `CompoundCurve`.  
  
## <a name="see-also"></a>См. также:  
 [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [STLength (тип данных geometry)](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STStartPoint (тип данных geometry)](../../t-sql/spatial-geometry/ststartpoint-geometry-data-type.md)   
 [STEndpoint (тип данных geometry)](../../t-sql/spatial-geometry/stendpoint-geometry-data-type.md)   
 [LineString](../../relational-databases/spatial/linestring.md)   
 [CircularString](../../relational-databases/spatial/circularstring.md)   
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Точка](../../relational-databases/spatial/point.md)  
  
