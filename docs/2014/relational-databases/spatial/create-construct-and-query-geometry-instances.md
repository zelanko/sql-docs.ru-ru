---
title: Создание и конструирование геометрических экземпляров и отправка запросов к ним | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- planar spatial data [SQL Server], getting started
- geometry data type [SQL Server], getting started
ms.assetid: c6b5c852-37d2-48d0-a8ad-e43bb80d6514
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: cb99c2ff07f30d268980c5c1c4d43a34904cdec9
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66014308"
---
# <a name="create-construct-and-query-geometry-instances"></a>Создание, конструирование и запрос экземпляров geometry
  Планарный пространственный тип данных `geometry` представляет данные в евклидовой (плоской) системе координат. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]этот тип реализован как тип данных среды CLR.  
  
 Тип `geometry` является стандартным и доступен в каждой базе данных. В таблице можно создать столбцы типа `geometry` и обращаться с данными `geometry` так же, как и с данными других типов среды CLR.  
  
 Тип данных `geometry` (плоский), поддерживаемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соответствует спецификации Open Geospatial Consortium (OGC) «Простые объекты для SQL» версии 1.1.0.  
  
 Дополнительные сведения о спецификациях OGC см. в одном из следующих источников:  
  
-   [Спецификации OGC, простой доступ к функциям, часть 1 — общая архитектура](https://go.microsoft.com/fwlink/?LinkId=93628)  
  
-   [Спецификации OGC, простой доступ к функциям, часть 2 — параметры SQL](https://go.microsoft.com/fwlink/?LinkId=93629)  
  
 Служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает подмножество существующего стандарта GML 3.1, определенного по следующей схеме: [https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959).  
  
##  <a name="creating"></a> Создание или построение нового экземпляра геометрического объекта  
  
###  <a name="existing"></a> Создание нового экземпляра геометрического объекта из существующего экземпляра  
 Тип данных `geometry` содержит множество встроенных методов, с помощью которых можно создавать новые объекты `geometry` на основе существующих.  
  
 **Создание буфера вокруг геометрического объекта**  
 [STBuffer (тип данных geometry)](/sql/t-sql/spatial-geometry/stbuffer-geometry-data-type)  
  
 [BufferWithTolerance (тип данных geometry)](/sql/t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type)  
  
 **Создание упрощенной версии геометрического объекта**  
 [Reduce (тип данных geometry)](/sql/t-sql/spatial-geometry/reduce-geometry-data-type)  
  
 **Создание выпуклой оболочки геометрического объекта**  
 [STConvexHull (тип данных geometry)](/sql/t-sql/spatial-geometry/stconvexhull-geometry-data-type)  
  
 **Создание геометрического объекта на основе пересечения двух геометрических объектов**  
 [STIntersection (тип данных geometry)](/sql/t-sql/spatial-geometry/stintersection-geometry-data-type)  
  
 **Создание геометрического объекта основе объединения двух геометрических объектов**  
 [STUnion (тип данных geometry)](/sql/t-sql/spatial-geometry/stunion-geometry-data-type)  
  
 **Создание геометрического объекта на основе точек, в которых один геометрический объект не перекрывается другими**  
 [STDifference (тип данных geometry)](/sql/t-sql/spatial-geometry/stdifference-geometry-data-type)  
  
 **Создание геометрического объекта на основе точек, в которых два геометрических объекта не перекрываются**  
 [STSymDifference (тип данных geometry)](/sql/t-sql/spatial-geometry/stsymdifference-geometry-data-type)  
  
 **Создание произвольного экземпляра Point, принадлежащего существующему геометрическому объекту**  
 [STPointOnSurface (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
  
  
###  <a name="wkt"></a> Построение экземпляра геометрического объекта на основе входных данных в формате Well-Known Text  
 В типе данных `geometry` предусмотрено несколько встроенных методов, позволяющих создать экземпляр типа geometry на основе представления WKT спецификации консорциума OGC. Стандарт WKT представляет собой текстовую строку, позволяющую осуществлять обмен геометрическими данными в текстовой форме.  
  
 **Создание экземпляра геометрического объекта любого типа на основе входных данных формата WKT**  
 [STGeomFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)  
  
 [Parse (тип данных geometry)](/sql/t-sql/spatial-geometry/parse-geometry-data-type)  
  
 **Создание геометрического объекта Point на основе входных данных формата WKT**  
 [STPointFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointfromtext-geometry-data-type)  
  
 **Создание геометрического объекта MultiPoint на основе входных данных формата WKT**  
 [STMPointFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stmpointfromtext-geometry-data-type)  
  
 **Создание геометрического объекта LineString на основе входных данных формата WKT**  
 [STLineFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stlinefromtext-geometry-data-type)  
  
 **Создание геометрического объекта MultiLineString на основе входных данных формата WKT**  
 [STMLineFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stmlinefromtext-geometry-data-type)  
  
 **Создание геометрического объекта Polygon на основе входных данных формата WKT**  
 [STPolyFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stpolyfromtext-geometry-data-type)  
  
 **Создание геометрического объекта MultiPolygon на основе входных данных формата WKT**  
 [STMPolyFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stmpolyfromtext-geometry-data-type)  
  
 **Создание геометрического объекта GeometryCollection на основе входных данных формата WKT**  
 [STGeomCollFromText (тип данных geometry)](/sql/t-sql/spatial-geometry/stgeomcollfromtext-geometry-data-type)  
  
  
  
###  <a name="wkb"></a> Построение экземпляра геометрического объекта на основе входных данных в формате Well-Known Binary Input  
 WKB представляет собой описанный консорциумом OGC двоичный формат, позволяющий осуществлять обмен данными типа `geometry` между клиентскими приложениями и базой данных SQL. Следующие функции допускают создание геометрических объектов на основе входных данных формата WKB.  
  
 **Создание экземпляра геометрического объекта любого типа на основе входных данных формата WKB**  
 [STGeomFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stgeomfromwkb-geometry-data-type)  
  
 **Создание геометрического объекта Point на основе входных данных формата WKB**  
 [STPointFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointfromwkb-geometry-data-type)  
  
 **Создание геометрического объекта MultiPoint на основе входных данных формата WKB**  
 [STMPointFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stmpointfromwkb-geometry-data-type)  
  
 **Создание геометрического объекта LineString на основе входных данных формата WKB**  
 [STLineFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stlinefromwkb-geometry-data-type)  
  
 **Создание геометрического объекта MultiLineString на основе входных данных формата WKB**  
 [STMLineFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stmlinefromwkb-geometry-data-type)  
  
 **Создание геометрического объекта Polygon на основе входных данных формата WKB**  
 [STPolyFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stpolyfromwkb-geometry-data-type)  
  
 **Создание геометрического объекта MultiPolygon на основе входных данных формата WKB**  
 [STMPolyFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stmpolyfromwkb-geometry-data-type)  
  
 **Создание геометрического объекта GeometryCollection на основе входных данных формата WKB**  
 [STGeomCollFromWKB (тип данных geometry)](/sql/t-sql/spatial-geometry/stgeomcollfromwkb-geometry-data-type)  
  
  
  
###  <a name="gml"></a> Построение экземпляра геометрического объекта на основе входных данных в формате GML Text  
 `geometry` Тип данных предоставляет метод, создающий `geometry` на основе GML, XML-представления геометрических объектов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает подмножество GML.  
  
 **Создание экземпляра геометрического объекта любого типа на основе входных данных формата GML**  
 [GeomFromGml (тип данных geometry)](/sql/t-sql/spatial-geometry/geomfromgml-geometry-data-type)  
  
  
  
##  <a name="returning"></a> Получение данных в формате Well-Known Text и Well-Known Binary из геометрического экземпляра  
 Можно использовать следующие методы для получения данных экземпляра `geometry` в формате WKT или формате WKB:  
  
 **Получение WKT-представления экземпляра геометрического объекта**  
 [STAsText (тип данных geometry)](/sql/t-sql/spatial-geometry/stastext-geometry-data-type)  
  
 [ToString (тип данных geometry)](/sql/t-sql/spatial-geometry/tostring-geometry-data-type)  
  
 **Получение WKT-представления экземпляра геометрического объекта, включая значения Z и M**  
 [AsTextZM (тип данных geometry)](/sql/t-sql/spatial-geometry/astextzm-geometry-data-type)  
  
 **Получение WKB-представления экземпляра геометрического объекта**  
 [STAsBinary (тип данных geometry)](/sql/t-sql/spatial-geometry/stasbinary-geometry-data-type)  
  
 **Получение GML-представления экземпляра геометрического объекта**  
 [AsGml (тип данных geometry)](/sql/t-sql/spatial-geometry/asgml-geometry-data-type)  
  
  
  
##  <a name="querying"></a> Запрос свойств и режимов геометрических объектов  
 Все `geometry` экземпляры имеют ряд свойств, которые можно извлечь с помощью методов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет. В следующих разделах описаны свойства и поведение геометрических типов данных, а также методы для запросов к ним.  
  
###  <a name="valid"></a> Допустимость, тип экземпляра и сведения GeometryCollection  
 Как только экземпляр `geometry` сформирован, при помощи следующих методов можно определить правильность его формата, получить тип этого экземпляра или, в случае экземпляра-коллекции, получить определенный экземпляр `geometry`.  
  
 **Получение типа геометрического объекта**  
 [STGeometryType (тип данных geometry)](/sql/t-sql/spatial-geometry/stgeometrytype-geometry-data-type)  
  
 **Определение принадлежности геометрического объекта к заданному типу**  
 [InstanceOf (тип данных geometry)](/sql/t-sql/spatial-geometry/instanceof-geometry-data-type)  
  
 **Проверка соответствия формата экземпляра геометрического объекта его типу**  
 [STIsValid (тип данных geometry)](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
 **Преобразование экземпляра геометрического объекта в экземпляр геометрический объект правильного формата с каким-либо типом экземпляра**  
 [MakeValid (тип данных geometry)](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)  
  
 **Получение количества геометрических экземпляров в экземпляре геометрической коллекции**  
 [STNumGeometries (тип данных geometry)](/sql/t-sql/spatial-geometry/stnumgeometries-geometry-data-type)  
  
 Получение определенного геометрического объекта из экземпляра геометрической коллекции  
 [STGeometryN (тип данных geometry)](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN (тип данных geometry)  
  
  
  
###  <a name="number"></a> Число точек  
 Все непустые `geometry` экземпляров состоят из *точек*. Эти точки представляют координаты X и Y на плоскости, где вычерчиваются геометрические объекты. `geometry` предоставляет многочисленные встроенные методы для создания запросов к точкам экземпляра.  
  
 **Получение числа точек, образующих экземпляр**  
 [STNumPoints (тип данных geometry)](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)  
  
 **Получение выбранной точки в экземпляре**  
 [STPointN](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 **Произвольная точка, принадлежащая экземпляру**  
 [STPointOnSurface](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
 **Получение начальной точки экземпляра**  
 [STStartPoint](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)  
  
 **Получение конечной точки экземпляра**  
 [STEndpoint](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)  
  
 **Координата по оси X экземпляра Point**  
 [STX (тип данных geometry)](/sql/t-sql/spatial-geometry/stx-geometry-data-type)  
  
 **Координата по оси Y экземпляра Point**  
 [STY](/sql/t-sql/spatial-geometry/sty-geometry-data-type)  
  
 **Определение геометрического центра экземпляра Polygon, CurvePolygon или MultiPolygon**  
 [STCentroid](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)  
  
  
  
###  <a name="dimension"></a> Измерение  
 Непустой объект `geometry` может иметь 0, 1 или 2 измерения. Объекты `geometries`, имеющие 0 измерений, например `Point` и `MultiPoint`, не имеют ни длины, ни площади. Одномерные объекты, такие как `LineString, CircularString, CompoundCurve` и `MultiLineString`, имеют длину. Двумерные объекты, такие как `Polygon`, `CurvePolygon` и `MultiPolygon`, имеют длину и площадь. Пустые экземпляры имеют измерение -1, а экземпляр `GeometryCollection` имеет площадь, зависящую от типов его содержимого.  
  
 **Получение измерения экземпляра**  
 [STDimension](/sql/t-sql/spatial-geometry/stdimension-geometry-data-type)  
  
 **Получение длины экземпляра**  
 [STLength](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)  
  
 **Получение площади экземпляра**  
 [STArea](/sql/t-sql/spatial-geometry/starea-geometry-data-type)  
  
  
  
###  <a name="empty"></a> Пустой  
 *Пустой* `geometry` экземпляр не содержит ни одной точки. Длина пустых экземпляров `LineString, CircularString`, `CompoundCurve` и `MultiLineString` равна нулю. Площадь пустых экземпляров `Polygon`, `CurvePolygon` и `MultiPolygon` равна нулю.  
  
 **Проверка, является ли экземпляр пустым**  
 [STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type).  
  
  
  
###  <a name="simple"></a> Простой  
 Для `geometry` экземпляра быть *простой*, он должен удовлетворять двум следующим требованиям:  
  
-   Каждая фигура экземпляра не должна пересекать саму себя, за исключением конечных точек.  
  
-   Никакие две фигуры экземпляра не могут пересекаться в точке, не находящейся на их границах.  
  
> [!NOTE]  
>  Пустые геометрические фигуры всегда являются простыми.  
  
 **Определение, является ли экземпляр простым**  
 [STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type).  
  
  
  
###  <a name="boundary"></a> Граница, внутренняя и внешняя область  
 *Внутренних* из `geometry` экземпляр — это пространство, занимаемое экземпляром и *Наружная* — это пространство не занимаемое им.  
  
 *Граница* определяется в OGC следующим образом:  
  
-   Экземпляры `Point` и `MultiPoint` не имеют границы.  
  
-   Границы `LineString` и `MultiLineString` образуются начальными и конечными точками, за исключением тех, которые появляются четное число раз.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 1, 0 0, 1 0, 0 1), (1 1, 1 0))');  
SELECT @g.STBoundary().ToString();  
```  
  
 Граница экземпляра `Polygon` или `MultiPolygon` — это совокупность его колец.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0), (1 1, 1 2, 2 2, 2 1, 1 1))');  
SELECT @g.STBoundary().ToString();  
```  
  
 **Получение границы экземпляра**  
 [STBoundary](/sql/t-sql/spatial-geometry/stboundary-geometry-data-type)  
  
  
  
###  <a name="envelope"></a> Огибающая  
 *Конверт* из `geometry` экземпляра, также известный как *ограничивающий прямоугольник*, выровненный по осям прямоугольник формируется минимальное и максимальное (X, Y) координирует экземпляра.  
  
 **Получение огибающей экземпляра**  
 [STEnvelope](/sql/t-sql/spatial-geometry/stenvelope-geometry-data-type)  
  
  
  
###  <a name="closure"></a> Замыкание  
 Объект *закрыто* `geometry` — это фигура, начальная и конечная точки которой совпадают. Экземпляры `Polygon` считаются замкнутыми. Экземпляры `Point` не замкнуты.  
  
 Кольцо — это простой замкнутый экземпляр `LineString`.  
  
 **Определение, является ли экземпляр замкнутым**  
 [STIsClosed](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)  
  
 **Определение, является ли экземпляр кольцом**  
 [STIsRing](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)  
  
 **Получение внешнего кольца экземпляра Polygon**  
 [STExteriorRing](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)  
  
 **Получение числа внутренних колец в экземпляре Polygon**  
 [STNumInteriorRing](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)  
  
 **Получение конкретного внутреннего кольца в экземпляре Polygon**  
 [STInteriorRingN](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)  
  
  
  
###  <a name="srid"></a> Идентификатор пространственной ссылки (SRID)  
 Идентификатор пространственной ссылки (SRID) — это идентификатор, указывающий, в какой системе координат представлен экземпляр `geometry`. Два экземпляра с разными идентификаторами SRID несравнимы.  
  
 **Задание или возврат идентификатора SRID экземпляра**  
 [STSrid](/sql/t-sql/spatial-geometry/stsrid-geometry-data-type)  
  
 Это свойство можно изменять.  
  
  
  
##  <a name="rel"></a> Определение связей между геометрическими объектами  
 Тип данных `geometry` предоставляет множество встроенных методов, с помощью которых можно определить связи между двумя объектами типа `geometry`.  
  
 **Определение возможного наличия одинакового набора точек в двух объектах**  
 [STEquals](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 **Определение отсутствия перекрытия двух объектов**  
 [STDisjoint](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 **Определение пересечения двух объектов**  
 [STIntersects](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 **Определение соприкосновений двух экземпляров**  
 [STTouches](/sql/t-sql/spatial-geometry/sttouches-geometry-data-type)  
  
 **Определение перекрещивания двух экземпляров**  
 [STOverlaps](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 **Определение пересечения двух экземпляров**  
 [STCrosses](/sql/t-sql/spatial-geometry/stcrosses-geometry-data-type)  
  
 **Определение нахождения одного экземпляра в другом**  
 [STWithin](/sql/t-sql/spatial-geometry/stwithin-geometry-data-type)  
  
 **Определение содержания одного экземпляра другим**  
 [STContains](/sql/t-sql/spatial-geometry/stcontains-geometry-data-type)  
  
 **Определение перекрещивания одного экземпляра с другим**  
 [STOverlaps](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 **Определение пространственной связи двух экземпляров**  
 [STRelate](/sql/t-sql/spatial-geometry/strelate-geometry-data-type)  
  
 **Определение кратчайшего пути между точками двух геометрических экземпляров**  
 [STDistance](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
  
  
##  <a name="defaultsrid"></a> Значение по умолчанию, равное 0, для идентификаторов SRID экземпляров геометрических объектов  
 Идентификатор SRID для экземпляров `geometry` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет значение по умолчанию, равное 0. При работе с пространственными данными типа `geometry` конкретный идентификатор SRID пространственного экземпляра для выполнения вычислений не требуется. Таким образом, экземпляры могут находиться в неопределенном двумерном пространстве. Чтобы указать неопределенное двумерное пространство в вычислениях методов работы с типом данных `geometry`, в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] используется значение SRID, равное 0.  
  
##  <a name="examples"></a> Примеры  
 В следующих двух примерах иллюстрируется добавление и запрос геометрических данных.  
  
-   В первом примере создается таблица со столбцом идентификаторов и столбцом `geometry` типа `GeomCol1`. Третий столбец обрабатывает столбец `geometry` для представления в формате известного текста (WKT) OGC, используя метод `STAsText()` . Затем вставляются две строки: одна строка содержит объект `LineString` типа `geometry`, а другая — объект `Polygon` .  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeomCol1 geometry,   
        GeomCol2 AS GeomCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
    GO  
    ```  
  
-   Во втором примере метод `STIntersection()` используется для получения точек, в которых пересекаются два вставленные ранее объекта `geometry` .  
  
    ```  
    DECLARE @geom1 geometry;  
    DECLARE @geom2 geometry;  
    DECLARE @result geometry;  
  
    SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geom1.STIntersection(@geom2);  
    SELECT @result.STAsText();  
    ```  
  
  
  
## <a name="see-also"></a>См. также:  
 [Пространственные данные (SQL Server)](spatial-data-sql-server.md)  
  
  
