---
title: Создание и конструирование географических экземпляров и отправка запросов к ним | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a576a6d047148675fd50730bcb4a5e76a5684b14
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018749"
---
# <a name="create-construct-and-query-geography-instances"></a>Создание, проектирование и создание запросов к экземплярам типа данных geography
  Тип пространственных данных `geography` представляет данные в системе координат круглой земли. Этот тип реализован как тип данных среды CLR .NET в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` Тип данных хранит эллипсоидальные (сферические) данные, такие как координаты широты и долготы GPS.  
  
 Тип `geography` является стандартным и доступен в каждой базе данных. В таблице можно создать столбцы типа `geography` и обращаться с данными `geography` так же, как с данными других предусмотренных в системе типов.  
  
##  <a name="creating"></a> Создание или построение нового экземпляра географического объекта  
  
###  <a name="existing"></a> Создание нового экземпляра географического объекта из существующего экземпляра  
 Тип данных `geography` содержит множество встроенных методов, с помощью которых можно создавать новые объекты `geography` на основе существующих.  
  
 **Создание буфера вокруг географического объекта**  
 [STBuffer (тип данных geography)](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 **Создание буфера вокруг географического объекта с допуском**  
 [BufferWithTolerance (тип данных geography)](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 **Создание географического объекта из пересечения двух географических объектов**  
 [STIntersection (тип данных geography)](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **Создание географического объекта из объединения двух географических объектов**  
 [STUnion (тип данных geography)](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 **Создание географического объекта из точек, в которых один объект не пересекается с другим**  
 [STDifference (тип данных geography)](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="wkt"></a> Построение экземпляра географического объекта на основе входных данных в формате Well-Known Text  
 Тип данных `geography` предоставляет несколько встроенных методов, позволяющих создать экземпляр типа geography на основе представления Open Geospatial Consortium (OGC) WKT. Стандарт WKT представляет собой текстовую строку, позволяющую осуществлять обмен географическими данными в текстовой форме.  
  
 **Создание экземпляра географического объекта любого типа на основе входных данных в формате WKT**  
 [STGeomFromText (тип данных geography)](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [Parse (тип данных geography)](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 **Создание экземпляра географического объекта Point на основе входных данных в формате WKT**  
 [STPointFromText (тип данных geography)](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 **Создание экземпляра географического объекта MultiPoint на основе входных данных в формате WKT**  
 [STMPointFromText (тип данных geography)](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 **Создание экземпляра географического объекта LineString на основе входных данных в формате WKT**  
 STLineFromText (географический тип данных)  
  
 **Создание экземпляра географического объекта MultiLineString на основе входных данных в формате WKT**  
 [STMLineFromText (тип данных geography)](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 **Создание экземпляра географического объекта Polygon на основе входных данных в формате WKT**  
 [STPolyFromText (тип данных geography)](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 **Создание экземпляра географического объекта MultiPolygon на основе входных данных в формате WKT**  
 [STMPolyFromText (тип данных geography)](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 **Создание экземпляра географического объекта GeometryCollection на основе входных данных в формате WKT**  
 [STGeomCollFromText (тип данных geography)](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="wkb"></a> Построение экземпляра географического объекта на основе входных данных в формате Well-Known Binary  
 WKB представляет собой описанный консорциумом OGC двоичный формат, позволяющий осуществлять обмен данными типа `Geography` между клиентскими приложениями и базой данных SQL. С помощью следующих функций создаются экземпляры географических объектов на основе входных данных WKB:  
  
 **Создание экземпляра географического объекта любого типа на основе входных данных в формате WKB**  
 [STGeomFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 **Создание экземпляра географического объекта Point на основе входных данных в формате WKB**  
 [STPointFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 **Создание экземпляра географического объекта MultiPoint на основе входных данных в формате WKB**  
 [STMPointFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 **Создание экземпляра географического объекта LineString на основе входных данных в формате WKB**  
 [STLineFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 **Создание экземпляра географического объекта MultiLineString на основе входных данных в формате WKB**  
 [STMLineFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 **Создание экземпляра географического объекта Polygon на основе входных данных в формате WKB**  
 [STPolyFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 **Создание экземпляра географического объекта MultiPolygon на основе входных данных в формате WKB**  
 [STMPolyFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 **Создание экземпляра географического объекта GeometryCollection на основе входных данных в формате WKB**  
 [STGeomCollFromWKB (тип данных geography)](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (тип данных geography)  
  
###  <a name="gml"></a> Построение экземпляра географического объекта на основе входных данных в формате GML Text  
 `geography` Тип данных предоставляет метод, создающий `geography` на основе GML, XML-представление `geography` экземпляра. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает подмножество GML.  
  
 Дополнительные сведения о языке GML см. в спецификации OGC: [Спецификации OGC, географический язык разметки.](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
 **Создание экземпляра географического объекта любого типа на основе входных данных в формате GML**  
 [GeomFromGML (тип данных geography)](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning"></a> Получение данных в формате Well-Known Text и Well-Known Binary из экземпляра географического объекта  
 Можно использовать следующие методы для получения данных экземпляра `geography` в формате WKT или формате WKB:  
  
 **Возврат WKT-представления экземпляра географического объекта**  
 [STAsText (тип данных geography)](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [ToString (тип данных geography)](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 **Получение представления экземпляра географического объекта в формате WKT, включая все значения Z и M**  
 [AsTextZM (тип данных geography)](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 **Возврат WKB-представления экземпляра географического объекта**  
 [STAsBinary (тип данных geography)](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 **Возврат GML-представления экземпляра географического объекта**  
 [AsGml (тип данных geography)](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="query"></a> Выполнение запроса к свойствам и методам экземпляров географических объектов  
 Все `geography` экземпляры имеют ряд свойств, которые можно извлечь с помощью методов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет. В следующих разделах определяются свойства и поведение географических типов, а также методы запросов к каждому из них.  
  
###  <a name="valid"></a> Допустимость, тип экземпляра и сведения GeometryCollection  
 Когда экземпляр `geography` создан, можно использовать следующие методы, чтобы получить типа экземпляра или, если это экземпляр `GeometryCollection`, конкретный экземпляр `geography`.  
  
 **Возврат типа географического экземпляра**  
 [STGeometryType (тип данных geography)](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 **Определение принадлежности географического экземпляра к заданному типу**  
 [InstanceOf (тип данных geography)](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 **Проверка соответствия формата экземпляра географического объекта его типу**  
 [STNumGeometries (тип данных geography)](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 **Возврат конкретного географического экземпляра из экземпляра GeometryCollection**  
 [STGeometryN (тип данных geography)](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (тип данных geography)  
  
###  <a name="number"></a> Число точек  
 Все непустые `geography` экземпляров состоят из *точек*. Данные точки представляют координаты широты и долготы, соответствующие месту создания экземпляров `geography`. В типе данных `geography` предусмотрены многочисленные встроенные методы запросов к точкам экземпляра.  
  
 **Получение числа точек, образующих экземпляр**  
 [STNumPoints (тип данных geography)](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 **Получение выбранной точки в экземпляре**  
 [STPointN (тип данных geometry)](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 **Получение начальной точки экземпляра**  
 [STStartPoint (тип данных geography)](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 **Получение конечной точки экземпляра**  
 [STEndpoint (тип данных geography)](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a> Измерение  
 Непустой объект `geography` может иметь 0, 1 или 2 измерения. Без измерений `geography` экземпляров, таких как `Point` и `MultiPoint`, не имеют длины или области. Одномерные объекты, такие как `LineString, CircularString`, `CompoundCurve` и `MultiLineString`, имеют длину. Двумерные объекты, такие как `Polygon, CurvePolygon` и `MultiPolygon`, имеют длину и площадь. В отчете пустых экземпляров указывается измерение -1, а в отчетах `GeometryCollection` — максимальное измерение содержимого.  
  
 **Получение измерения экземпляра**  
 [STDimension (тип данных geography)](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 **Получение длины экземпляра**  
 [STLength (тип данных geography)](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 **Получение площади экземпляра**  
 [STArea (тип данных geography)](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a> Пустой  
 *Пустой* `geography` экземпляр не содержит ни одной точки. Длина пустых экземпляров `LineString, CircularString`, `CompoundCurve` и `MultiLineString` равна 0. Площадь пустых экземпляров `Polygon, CurvePolygon` и `MultiPolygon` равна 0.  
  
 **Проверка, является ли экземпляр пустым**  
 [STIsEmpty (тип данных geography)](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a> Замыкание  
 Объект *закрыто* `geography` — это фигура, начальная и конечная точки которой совпадают. Экземпляры `Polygon` считаются замкнутыми. Экземпляры `Point` не замкнуты.  
  
 Кольцо — это простой замкнутый экземпляр `LineString`.  
  
 **Определение, является ли экземпляр замкнутым**  
 [STIsClosed (тип данных geography)](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 **Получение количества колец экземпляра объекта Polygon**  
 [NumRings (тип данных geography)](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 **Получение указанного кольца какого-либо географического объекта**  
 [RingN (тип данных geography)](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="srid"></a> Идентификатор пространственной ссылки (SRID)  
 Идентификатор пространственной ссылки (SRID) представляет собой идентификатор, указывающий на систему эллиптических координат, в которой находится экземпляр `geography`. Сравнение двух экземпляров `geography` с различными идентификаторами SRID невозможно.  
  
 **Задание или возврат идентификатора SRID экземпляра**  
 [STSrid (тип данных geography)](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 Это свойство можно изменять.  
  
##  <a name="rel"></a> Определение связей между экземплярами географических объектов  
 Тип данных `geography` предоставляет множество встроенных методов, с помощью которых можно определить связи между двумя объектами типа `geography`.  
  
 **Определение возможного наличия одинакового набора точек в двух объектах**  
 [STEquals (тип данных geometry)](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 **Определение отсутствия перекрытия двух объектов**  
 [STDisjoint (тип данных geometry)](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 **Определение пересечения двух объектов**  
 [STIntersects (тип данных geometry)](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 **Определение точки или точек пересечения двух объектов**  
 [STIntersection (тип данных geography)](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **Определение кратчайшего расстояния между точками двух географических объектов**  
 [STDistance (тип данных geometry)](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 **Определение разницы в точках между двумя географическими объектами**  
 [STDifference (тип данных geography)](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 **Получение симметрической разницы (или уникальных точек) между двумя экземплярами географических объектов**  
 [STSymDifference (тип данных geography)](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="supportedsrid"></a> Обязательное использование поддерживаемых SRID в экземплярах географических объектах  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются идентификаторы SRID, основанные на стандартах EPSG. При выполнении вычислений или применении методов работы с географическими пространственными данными должны использоваться поддерживаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификаторы SRID для экземпляров `geography`. Заданный SRID должен соответствовать одному из идентификаторов SRID, отображенных в представлении каталога **sys.spatial_reference_systems** . Как было упомянуто ранее, результаты вычислений на пространственных данных с использованием типа данных `geography` зависят от эллипсоида, использованного при создании рабочих данных, поскольку каждому эллипсоиду назначается отдельный идентификатор пространственной ссылки (SRID).  
  
 При применении методов к экземплярам `geography` в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется значение идентификатора SRID по умолчанию, равное 4326, соответствующее системе пространственных ссылок WGS 84. Если используются данные системы пространственных ссылок, отличной от WGS 84 (или если значение SRID отличается от 4326), для собственных географических пространственных данных необходимо определить отдельный идентификатор SRID.  
  
##  <a name="examples"></a> Примеры  
 В следующих примерах иллюстрируется добавление и запрос географических данных.  
  
-   В первом примере создается таблица со столбцом идентификаторов и столбцом `geography` типа `GeogCol1`. Третий столбец обрабатывает столбец `geography` для представления в формате известного текста (WKT) OGC, используя метод `STAsText()` . Затем вставляются две строки: одна строка содержит объект `LineString` типа `geography`, а другая — объект `Polygon` .  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   Во втором примере метод `STIntersection()` используется для получения точек, в которых пересекаются два вставленные ранее объекта `geography` .  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a>См. также  
 [Пространственные данные (SQL Server)](spatial-data-sql-server.md)  
  
  
