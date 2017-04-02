---
title: "Создание, конструирование и запрос экземпляров geometry | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "плоские пространственные данные [SQL Server], приступая к работе"
  - "тип данных geometry [SQL Server], приступая к работе"
ms.assetid: c6b5c852-37d2-48d0-a8ad-e43bb80d6514
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Создание, конструирование и запрос экземпляров geometry
  Планарный пространственный тип данных **geometry** представляет данные в евклидовой (плоской) системе координат. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот тип реализован как тип данных среды CLR.  
  
 Тип **geometry** является стандартным и доступен в каждой базе данных. В таблице можно создать столбцы типа **geometry** и обращаться с данными **geometry** так же, как и с данными других типов среды CLR.  
  
 Тип данных **geometry** (плоский), поддерживаемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], соответствует спецификации Open Geospatial Consortium (OGC) "Простые объекты для SQL" версии 1.1.0.  
  
 Дополнительные сведения о спецификациях OGC см. в одном из следующих источников:  
  
-   [Спецификации OGC, простой доступ к функциям, часть 1 — общая архитектура](http://go.microsoft.com/fwlink/?LinkId=93628)  
  
-   [Спецификации OGC, простой доступ к функциям, часть 2 — параметры SQL](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает подмножество существующего стандарта GML 3.1, который определяется по следующей схеме: [http://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](http://go.microsoft.com/fwlink/?LinkId=230959).  
  
##  <a name="creating"></a> Создание или построение нового экземпляра геометрического объекта  
  
###  <a name="existing"></a> Создание нового экземпляра геометрического объекта из существующего экземпляра  
 Тип данных **geometry** предоставляет многочисленные встроенные методы создания новых экземпляров **geometry** на основе существующих экземпляров.  
  
 **Создание буфера вокруг геометрического объекта**  
 [STBuffer (тип данных geometry)](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)  
  
 [BufferWithTolerance (тип данных geometry)](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md)  
  
 **Создание упрощенной версии геометрического объекта**  
 [Reduce (тип данных geometry)](../../t-sql/spatial-geometry/reduce-geometry-data-type.md)  
  
 **Создание выпуклой оболочки геометрического объекта**  
 [STConvexHull (тип данных geometry)](../../t-sql/spatial-geometry/stconvexhull-geometry-data-type.md)  
  
 **Создание геометрического объекта на основе пересечения двух геометрических объектов**  
 [STIntersection (тип данных geometry)](../../t-sql/spatial-geometry/stintersection-geometry-data-type.md)  
  
 **Создание геометрического объекта основе объединения двух геометрических объектов**  
 [STUnion (тип данных geometry)](../../t-sql/spatial-geometry/stunion-geometry-data-type.md)  
  
 **Создание геометрического объекта на основе точек, в которых один геометрический объект не перекрывается другими**  
 [STDifference (тип данных geometry)](../../t-sql/spatial-geometry/stdifference-geometry-data-type.md)  
  
 **Создание геометрического объекта на основе точек, в которых два геометрических объекта не перекрываются**  
 [STSymDifference (тип данных geometry)](../../t-sql/spatial-geometry/stsymdifference-geometry-data-type.md)  
  
 **Создание произвольного экземпляра Point, принадлежащего существующему геометрическому объекту**  
 [STPointOnSurface (тип данных geometry)](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="wkt"></a> Построение экземпляра геометрического объекта на основе входных данных в формате Well-Known Text  
 В типе данных **geometry** предусмотрено несколько встроенных методов, позволяющих создать экземпляр типа geometry на основе представления WKT спецификации консорциума OGC. Стандарт WKT представляет собой текстовую строку, позволяющую осуществлять обмен геометрическими данными в текстовой форме.  
  
 **Создание экземпляра геометрического объекта любого типа на основе входных данных формата WKT**  
 [STGeomFromText (тип данных geometry)](../../t-sql/spatial-geometry/stgeomfromtext-geometry-data-type.md)  
  
 [Parse (тип данных geometry)](../../t-sql/spatial-geometry/parse-geometry-data-type.md)  
  
 **Создание геометрического объекта Point на основе входных данных формата WKT**  
 [STPointFromText (тип данных geometry)](../../t-sql/spatial-geometry/stpointfromtext-geometry-data-type.md)  
  
 **Создание геометрического объекта MultiPoint на основе входных данных формата WKT**  
 [STMPointFromText (тип данных geometry)](../../t-sql/spatial-geometry/stmpointfromtext-geometry-data-type.md)  
  
 **Создание геометрического объекта LineString на основе входных данных формата WKT**  
 [STLineFromText (тип данных geometry)](../../t-sql/spatial-geometry/stlinefromtext-geometry-data-type.md)  
  
 **Создание геометрического объекта MultiLineString на основе входных данных формата WKT**  
 [STMLineFromText (тип данных geometry)](../../t-sql/spatial-geometry/stmlinefromtext-geometry-data-type.md)  
  
 **Создание геометрического объекта Polygon на основе входных данных формата WKT**  
 [STPolyFromText (тип данных geometry)](../../t-sql/spatial-geometry/stpolyfromtext-geometry-data-type.md)  
  
 **Создание геометрического объекта MultiPolygon на основе входных данных формата WKT**  
 [STMPolyFromText (тип данных geometry)](../../t-sql/spatial-geometry/stmpolyfromtext-geometry-data-type.md)  
  
 **Создание геометрического объекта GeometryCollection на основе входных данных формата WKT**  
 [STGeomCollFromText (тип данных geometry)](../../t-sql/spatial-geometry/stgeomcollfromtext-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="wkb"></a> Построение экземпляра геометрического объекта на основе входных данных в формате Well-Known Binary Input  
 WKB представляет собой описанный консорциумом OGC двоичный формат, позволяющий осуществлять обмен данными типа **geometry** между клиентскими приложениями и базой данных SQL. Следующие функции допускают создание геометрических объектов на основе входных данных формата WKB.  
  
 **Создание экземпляра геометрического объекта любого типа на основе входных данных формата WKB**  
 [STGeomFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stgeomfromwkb-geometry-data-type.md)  
  
 **Создание геометрического объекта Point на основе входных данных формата WKB**  
 [STPointFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stpointfromwkb-geometry-data-type.md)  
  
 **Создание геометрического объекта MultiPoint на основе входных данных формата WKB**  
 [STMPointFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stmpointfromwkb-geometry-data-type.md)  
  
 **Создание геометрического объекта LineString на основе входных данных формата WKB**  
 [STLineFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stlinefromwkb-geometry-data-type.md)  
  
 **Создание геометрического объекта MultiLineString на основе входных данных формата WKB**  
 [STMLineFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stmlinefromwkb-geometry-data-type.md)  
  
 **Создание геометрического объекта Polygon на основе входных данных формата WKB**  
 [STPolyFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stpolyfromwkb-geometry-data-type.md)  
  
 **Создание геометрического объекта MultiPolygon на основе входных данных формата WKB**  
 [STMPolyFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stmpolyfromwkb-geometry-data-type.md)  
  
 **Создание геометрического объекта GeometryCollection на основе входных данных формата WKB**  
 [STGeomCollFromWKB (тип данных geometry)](../../t-sql/spatial-geometry/stgeomcollfromwkb-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="gml"></a> Построение экземпляра геометрического объекта на основе входных данных в формате GML Text  
 Тип данных **geometry** предоставляет метод, формирующий экземпляр **geometry** на основе GML, XML-представления геометрических объектов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает подмножество GML.  
  
 **Создание экземпляра геометрического объекта любого типа на основе входных данных формата GML**  
 [GeomFromGml (тип данных geometry)](../../t-sql/spatial-geometry/geomfromgml-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
##  <a name="returning"></a> Получение данных в формате Well-Known Text и Well-Known Binary из геометрического экземпляра  
 Можно использовать следующие методы для получения данных экземпляра **geometry** в формате WKT или формате WKB:  
  
 **Получение WKT-представления экземпляра геометрического объекта**  
 [STAsText (тип данных geometry)](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)  
  
 [ToString (тип данных geometry)](../../t-sql/spatial-geometry/tostring-geometry-data-type.md)  
  
 **Получение WKT-представления экземпляра геометрического объекта, включая значения Z и M**  
 [AsTextZM (тип данных geometry)](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)  
  
 **Получение WKB-представления экземпляра геометрического объекта**  
 [STAsBinary (тип данных geometry)](../../t-sql/spatial-geometry/stasbinary-geometry-data-type.md)  
  
 **Получение GML-представления экземпляра геометрического объекта**  
 [AsGml (тип данных geometry)](../../t-sql/spatial-geometry/asgml-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
##  <a name="querying"></a> Запрос свойств и режимов геометрических объектов  
 Все экземпляры **geometry** обладают рядом свойств, получить которые можно с помощью методов, предоставляемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В следующих разделах описаны свойства и поведение геометрических типов данных, а также методы для запросов к ним.  
  
###  <a name="valid"></a> Допустимость, тип экземпляра и сведения GeometryCollection  
 Как только экземпляр **geometry** сформирован, при помощи следующих методов можно определить правильность его формата, получить тип этого экземпляра или, в случае экземпляра-коллекции, получить определенный экземпляр **geometry**.  
  
 **Получение типа геометрического объекта**  
 [STGeometryType (тип данных geometry)](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)  
  
 **Определение принадлежности геометрического объекта к заданному типу**  
 [InstanceOf (тип данных geometry)](../../t-sql/spatial-geometry/instanceof-geometry-data-type.md)  
  
 **Проверка соответствия формата экземпляра геометрического объекта его типу**  
 [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
 **Преобразование экземпляра геометрического объекта в экземпляр геометрический объект правильного формата с каким-либо типом экземпляра**  
 [MakeValid (тип данных geometry)](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)  
  
 **Получение количества геометрических экземпляров в экземпляре геометрической коллекции**  
 [STNumGeometries (тип данных geometry)](../../t-sql/spatial-geometry/stnumgeometries-geometry-data-type.md)  
  
 Получение определенного геометрического объекта из экземпляра геометрической коллекции  
 [STGeometryN (тип данных geometry)](../../t-sql/spatial-geometry/stgeometryn-geometry-data-type.md)STGeometryN (тип данных geometry)  
  
 [В этом разделе](#TOP)  
  
###  <a name="number"></a> Число точек  
 Все непустые экземпляры **geometry** состоят из *точек*. Эти точки представляют координаты X и Y на плоскости, где вычерчиваются геометрические объекты. **geometry** предоставляет многочисленные встроенные методы для создания запросов, адресованных точкам экземпляра.  
  
 **Получение числа точек, образующих экземпляр**  
 [STNumPoints (тип данных geometry)](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)  
  
 **Получение выбранной точки в экземпляре**  
 [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)  
  
 **Произвольная точка, принадлежащая экземпляру**  
 [STPointOnSurface](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)  
  
 **Получение начальной точки экземпляра**  
 [STStartPoint](../../t-sql/spatial-geometry/ststartpoint-geometry-data-type.md)  
  
 **Получение конечной точки экземпляра**  
 [STEndpoint](../../t-sql/spatial-geometry/stendpoint-geometry-data-type.md)  
  
 **Координата по оси X экземпляра Point**  
 [STX (тип данных geometry)](../../t-sql/spatial-geometry/stx-geometry-data-type.md)  
  
 **Координата по оси Y экземпляра Point**  
 [STY](../../t-sql/spatial-geometry/sty-geometry-data-type.md)  
  
 **Определение геометрического центра экземпляра Polygon, CurvePolygon или MultiPolygon**  
 [STCentroid](../../t-sql/spatial-geometry/stcentroid-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="dimension"></a> Измерение  
 Непустой объект **geometry** может иметь 0, 1 или 2 измерения. Объекты **geometries**, имеющие 0 измерений, например **Point** и **MultiPoint**, не имеют ни длины, ни площади. Одномерные объекты, такие как **LineString, CircularString, CompoundCurve** и **MultiLineString**, имеют длину. Двухмерные объекты, такие как **Polygon**, **CurvePolygon** и **MultiPolygon**, имеют длину и площадь. Пустые объекты имеют измерение -1, а объект **GeometryCollection** имеет площадь, зависящую от типов его содержимого.  
  
 **Получение измерения экземпляра**  
 [STDimension](../../t-sql/spatial-geometry/stdimension-geometry-data-type.md)  
  
 **Получение длины экземпляра**  
 [STLength](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)  
  
 **Получение площади экземпляра**  
 [STArea](../../t-sql/spatial-geometry/starea-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="empty"></a> Пустой  
 *Пустой* объект **geometry** не имеет никаких точек. Длина пустых экземпляров **LineString, CircularString**, **CompoundCurve**и **MultiLineString** равна нулю. Площадь пустых экземпляров **Polygon**, **CurvePolygon**и **MultiPolygon** равна нулю.  
  
 **Проверка, является ли экземпляр пустым**  
 [STIsEmpty](../../t-sql/spatial-geometry/stisempty-geometry-data-type.md).  
  
 [В этом разделе](#TOP)  
  
###  <a name="simple"></a> Простой  
 Чтобы объект **geometry** экземпляра был *простым*, он должен удовлетворять двум следующим требованиям.  
  
-   Каждая фигура экземпляра не должна пересекать саму себя, за исключением конечных точек.  
  
-   Никакие две фигуры экземпляра не могут пересекаться в точке, не находящейся на их границах.  
  
> [!NOTE]  
>  Пустые геометрические фигуры всегда являются простыми.  
  
 **Определение, является ли экземпляр простым**  
 [STIsSimple](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md).  
  
 [В этом разделе](#TOP)  
  
###  <a name="boundary"></a> Граница, внутренняя и внешняя область  
 *Внутренняя область* экземпляра **geometry** — это пространство, занимаемое экземпляром, а *внешняя область* — это пространство, не занимаемое им.  
  
 *Граница* определяется в OGC следующим образом:  
  
-   Экземпляры**Point** и **MultiPoint** не имеют границы.  
  
-   Границы**LineString** и **MultiLineString** boundaries are formed by the start points и end points, removing those that occur an even number of times.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 1, 0 0, 1 0, 0 1), (1 1, 1 0))');  
SELECT @g.STBoundary().ToString();  
```  
  
 Граница экземпляра **Polygon** или **MultiPolygon** — это совокупность его колец.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0), (1 1, 1 2, 2 2, 2 1, 1 1))');  
SELECT @g.STBoundary().ToString();  
```  
  
 **Получение границы экземпляра**  
 [STBoundary](../../t-sql/spatial-geometry/stboundary-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="envelope"></a> Огибающая  
 *Огибающая* экземпляра **geometry**, которая также называется *ограничивающим прямоугольником*, представляет собой выровненный по осям прямоугольник, который построен на основе минимальных и максимальных координат (X,Y) объекта.  
  
 **Получение огибающей экземпляра**  
 [STEnvelope](../../t-sql/spatial-geometry/stenvelope-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="closure"></a> Замыкание  
 *Замкнутый* объект **geometry** — это фигура, начальная и конечная точки которой совпадают. Экземпляры**Polygon** считаются замкнутыми. Экземпляры**Point** не замкнуты.  
  
 Кольцо — это простой замкнутый экземпляр **LineString** .  
  
 **Определение, является ли экземпляр замкнутым**  
 [STIsClosed](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)  
  
 **Определение, является ли экземпляр кольцом**  
 [STIsRing](../../t-sql/spatial-geometry/stisring-geometry-data-type.md)  
  
 **Получение внешнего кольца экземпляра Polygon**  
 [STExteriorRing](../../t-sql/spatial-geometry/stexteriorring-geometry-data-type.md)  
  
 **Получение числа внутренних колец в экземпляре Polygon**  
 [STNumInteriorRing](../../t-sql/spatial-geometry/stnuminteriorring-geometry-data-type.md)  
  
 **Получение конкретного внутреннего кольца в экземпляре Polygon**  
 [STInteriorRingN](../../t-sql/spatial-geometry/stinteriorringn-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
###  <a name="srid"></a> Идентификатор пространственной ссылки (SRID)  
 Идентификатор пространственной ссылки (SRID) — это идентификатор, указывающий, в какой системе координат представлен объект **geometry**. Два экземпляра с разными идентификаторами SRID несравнимы.  
  
 **Задание или возврат идентификатора SRID экземпляра**  
 [STSrid](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)  
  
 Это свойство можно изменять.  
  
 [В этом разделе](#TOP)  
  
##  <a name="rel"></a> Определение связей между геометрическими объектами  
 Тип данных **geometry** предоставляет множество встроенных методов, с помощью которых можно определить связи между двумя объектами типа **geometry**.  
  
 **Определение возможного наличия одинакового набора точек в двух объектах**  
 [STEquals](../../t-sql/spatial-geometry/stequals-geometry-data-type.md)  
  
 **Определение отсутствия перекрытия двух объектов**  
 [STDisjoint](../../t-sql/spatial-geometry/stdisjoint-geometry-data-type.md)  
  
 **Определение пересечения двух объектов**  
 [STIntersects](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
 **Определение соприкосновений двух экземпляров**  
 [STTouches](../../t-sql/spatial-geometry/sttouches-geometry-data-type.md)  
  
 **Определение перекрещивания двух экземпляров**  
 [STOverlaps](../../t-sql/spatial-geometry/stoverlaps-geometry-data-type.md)  
  
 **Определение пересечения двух экземпляров**  
 [STCrosses](../../t-sql/spatial-geometry/stcrosses-geometry-data-type.md)  
  
 **Определение нахождения одного экземпляра в другом**  
 [STWithin](../../t-sql/spatial-geometry/stwithin-geometry-data-type.md)  
  
 **Определение содержания одного экземпляра другим**  
 [STContains](../../t-sql/spatial-geometry/stcontains-geometry-data-type.md)  
  
 **Определение перекрещивания одного экземпляра с другим**  
 [STOverlaps](../../t-sql/spatial-geometry/stoverlaps-geometry-data-type.md)  
  
 **Определение пространственной связи двух экземпляров**  
 [STRelate](../../t-sql/spatial-geometry/strelate-geometry-data-type.md)  
  
 **Определение кратчайшего пути между точками двух геометрических экземпляров**  
 [STDistance](../../t-sql/spatial-geometry/stdistance-geometry-data-type.md)  
  
 [В этом разделе](#TOP)  
  
##  <a name="defaultsrid"></a> Значение по умолчанию, равное 0, для идентификаторов SRID экземпляров геометрических объектов  
 Идентификатор SRID для экземпляров **geometry** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет значение по умолчанию, равное 0. При работе с пространственными данными типа **geometry** конкретный идентификатор SRID пространственного экземпляра для выполнения вычислений не требуется. Таким образом, экземпляры могут находиться в неопределенном двумерном пространстве. Чтобы указать неопределенное двумерное пространство в вычислениях методов работы с типом данных **geometry** , в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] используется значение SRID, равное 0.  
  
##  <a name="examples"></a> Примеры  
 В следующих двух примерах иллюстрируется добавление и запрос геометрических данных.  
  
-   В первом примере создается таблица со столбцом идентификаторов и столбцом `geometry` типа `GeomCol1`. Третий столбец обрабатывает столбец `geometry` для представления в формате известного текста (WKT) OGC, используя метод `STAsText()`. Затем вставляются две строки: одна строка содержит объект `LineString` типа `geometry`, а другая — объект `Polygon`.  
  
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
  
 [В этом разделе](#TOP)  
  
## См. также:  
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  