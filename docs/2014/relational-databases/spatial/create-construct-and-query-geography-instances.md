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
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 5dde7575a3f657b89d29fefa0da52002bcd6af28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014298"
---
# <a name="create-construct-and-query-geography-instances"></a>Создание, проектирование и создание запросов к экземплярам типа данных geography
  Тип пространственных данных `geography` представляет данные в системе координат круглой земли. Этот тип реализован как тип данных среды CLR .NET в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` хранит данные для эллипсоидальной (сферической) Земли, такие как координаты широты и долготы GPS.  
  
 Тип `geography` является стандартным и доступен в каждой базе данных. В таблице можно создать столбцы типа `geography` и обращаться с данными `geography` так же, как с данными других предусмотренных в системе типов.  
  
##  <a name="creating"></a>Создание или построение нового экземпляра geography  
  
###  <a name="existing"></a>Создание нового экземпляра geography из существующего экземпляра  
 Тип данных `geography` содержит множество встроенных методов, с помощью которых можно создавать новые объекты `geography` на основе существующих.  
  
 **Создание буфера вокруг географического объекта**  
 [Тип данных STBuffer &#40;geography&#41;](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 **Создание буфера вокруг географического объекта с возможностью допуска**  
 [Тип данных BufferWithTolerance &#40;geography&#41;](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 **Создание географического объекта из пересечения двух экземпляров geography**  
 [Тип данных STIntersection &#40;geography&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **Создание географического объекта из объединения двух географических объектов**  
 [Тип данных STUnion &#40;geography&#41;](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 **Создание географического объекта из точек, в которых одна географическая область не пересекается с другой**  
 [Тип данных STDifference &#40;geography&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="wkt"></a>Создание экземпляра geography из хорошо известного текстового ввода  
 Тип данных `geography` предоставляет несколько встроенных методов, позволяющих создать экземпляр типа geography на основе представления Open Geospatial Consortium (OGC) WKT. Стандарт WKT представляет собой текстовую строку, позволяющую осуществлять обмен географическими данными в текстовой форме.  
  
 **Построение любого типа экземпляра geography из входных данных WKT**  
 [Тип данных STGeomFromText &#40;geography&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [&#40;&#41;типа данных geography](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 **Создание экземпляра географической точки из входных данных WKT**  
 [Тип данных STPointFromText &#40;geography&#41;](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 **Построение экземпляра geography MultiPoint из входных данных WKT**  
 [Тип данных STMPointFromText &#40;geography&#41;](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 **Построение экземпляра geography LineString из входных данных WKT**  
 STLineFromText (географический тип данных)  
  
 **Построение экземпляра geography MultiLineString из входных данных WKT**  
 [Тип данных STMLineFromText &#40;geography&#41;](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 **Построение экземпляра географического многоугольника из входных данных WKT**  
 [Тип данных STPolyFromText &#40;geography&#41;](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 **Построение многомногоугольникового экземпляра geography из входных данных WKT**  
 [Тип данных STMPolyFromText &#40;geography&#41;](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 **Построение экземпляра geography GeometryCollection из входных данных WKT**  
 [Тип данных STGeomCollFromText &#40;geography&#41;](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="wkb"></a>Создание экземпляра geography из хорошо известного двоичного ввода  
 WKB представляет собой описанный консорциумом OGC двоичный формат, позволяющий осуществлять обмен данными типа `Geography` между клиентскими приложениями и базой данных SQL. С помощью следующих функций создаются экземпляры географических объектов на основе входных данных WKB:  
  
 **Построение любого типа экземпляра geography из входных данных WKB**  
 [Тип данных STGeomFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 **Создание экземпляра географической точки из входных данных WKB**  
 [Тип данных STPointFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 **Построение экземпляра geography MultiPoint из входных данных WKB**  
 [Тип данных STMPointFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 **Построение экземпляра geography LineString из входных данных WKB**  
 [Тип данных STLineFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 **Построение экземпляра geography MultiLineString из входных данных WKB**  
 [Тип данных STMLineFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 **Построение экземпляра географического многоугольника из входных данных WKB**  
 [Тип данных STPolyFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 **Построение многомногоугольникового экземпляра geography из входных данных WKB**  
 [Тип данных STMPolyFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 **Построение экземпляра geography GeometryCollection из входных данных WKB**  
 [Тип данных STGeomCollFromWKB &#40;geography&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type) STGeomCollFromWKB (тип данных geography)  
  
###  <a name="gml"></a>Создание экземпляра geography на основе текстового ввода GML  
 Тип `geography` данных предоставляет метод, создающий `geography` экземпляр из GML, XML-представление `geography` экземпляра. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает подмножество GML.  
  
 Дополнительные сведения о языке GML см. в спецификации OGC: [Спецификации OGC, географический язык разметки.](https://go.microsoft.com/fwlink/?LinkId=93629)  
  
 **Построение любого типа экземпляра geography из входных данных GML**  
 [Тип данных GeomFromGML &#40;geography&#41;](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning"></a>Возврат хорошо известного текста и хорошо известных двоичных файлов из экземпляра geography  
 Можно использовать следующие методы для получения данных экземпляра `geography` в формате WKT или формате WKB:  
  
 **Возврат WKT-представления экземпляра geography**  
 [Тип данных STAsText &#40;geography&#41;](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [ToString &#40;тип данных geography&#41;](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 **Возврат WKT-представления экземпляра geography, включая любые значения Z и M**  
 [Тип данных AsTextZM &#40;geography&#41;](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 **Возврат WKB-представления экземпляра geography**  
 [Тип данных STAsBinary &#40;geography&#41;](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 **Возврат GML-представления экземпляра geography**  
 [Тип данных AsGml &#40;geography&#41;](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="query"></a>Запрос свойств и поведения экземпляров geography  
 У `geography` всех экземпляров есть ряд свойств, которые можно получить с помощью методов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляемых. В следующих разделах определяются свойства и поведение географических типов, а также методы запросов к каждому из них.  
  
###  <a name="valid"></a>Сведения о допустимости, типе экземпляра и GeometryCollection  
 Когда экземпляр `geography` создан, можно использовать следующие методы, чтобы получить типа экземпляра или, если это экземпляр `GeometryCollection`, конкретный экземпляр `geography`.  
  
 **Возврат типа экземпляра geography**  
 [Тип данных STGeometryType &#40;geography&#41;](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 **Определение, является ли География экземпляром заданного типа**  
 [Тип данных InstanceOf &#40;geography&#41;](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 **Определение правильности формата экземпляра geography для его типа экземпляра**  
 [Тип данных STNumGeometries &#40;geography&#41;](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 **Получение определенного географического объекта в экземпляре GeometryCollection**  
 [Тип данных STGeometryN &#40;geography&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type) STGeometryN (тип данных geography)  
  
###  <a name="number"></a>Число точек  
 Все непустые `geography` экземпляры состоят из *точек*. Данные точки представляют координаты широты и долготы, соответствующие месту создания экземпляров `geography`. В типе данных `geography` предусмотрены многочисленные встроенные методы запросов к точкам экземпляра.  
  
 **Получение количества точек, составляющих экземпляр**  
 [Тип данных STNumPoints &#40;geography&#41;](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 **Возврат определенной точки в экземпляре**  
 [STPointN &#40;типа данных geometry&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 **Получение начальной точки экземпляра**  
 [Тип данных STStartPoint &#40;geography&#41;](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 **Получение конечной точки экземпляра**  
 [Тип данных STEndpoint &#40;geography&#41;](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a>Фокусирован  
 Непустой объект `geography` может иметь 0, 1 или 2 измерения. Экземпляры с нулевым `geography` измерением, такие `Point` как `MultiPoint`и, не имеют длины или площади. Одномерные объекты, такие как `LineString, CircularString`, `CompoundCurve` и `MultiLineString`, имеют длину. Двумерные объекты, такие как `Polygon, CurvePolygon` и `MultiPolygon`, имеют длину и площадь. В отчете пустых экземпляров указывается измерение -1, а в отчетах `GeometryCollection` — максимальное измерение содержимого.  
  
 **Получение измерения экземпляра**  
 [Тип данных STDimension &#40;geography&#41;](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 **Получение длины экземпляра**  
 [Тип данных STLength &#40;geography&#41;](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 **Получение области экземпляра**  
 [Тип данных STArea &#40;geography&#41;](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a>Указано  
 *Пустой* `geography` экземпляр не имеет точек. Длина пустых экземпляров `LineString, CircularString`, `CompoundCurve` и `MultiLineString` равна 0. Площадь пустых экземпляров `Polygon, CurvePolygon` и `MultiPolygon` равна 0.  
  
 **Определение, является ли экземпляр пустым**  
 [Тип данных STIsEmpty &#40;geography&#41;](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a>Закрыт  
 *Закрытый* `geography` экземпляр — это фигура, начальная и конечная точки которой одинаковы. Экземпляры `Polygon` считаются замкнутыми. Экземпляры `Point` не замкнуты.  
  
 Кольцо — это простой замкнутый экземпляр `LineString`.  
  
 **Определение, закрыт ли экземпляр**  
 [Тип данных STIsClosed &#40;geography&#41;](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 **Получение числа колец в экземпляре Polygon**  
 [Тип данных NumRings &#40;geography&#41;](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 **Возврат указанного кольца экземпляра geography**  
 [Тип данных RingN &#40;geography&#41;](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="srid"></a>ИДЕНТИФИКАТОР пространственной ссылки (SRID)  
 Идентификатор пространственной ссылки (SRID) представляет собой идентификатор, указывающий на систему эллиптических координат, в которой находится экземпляр `geography`. Сравнение двух экземпляров `geography` с различными идентификаторами SRID невозможно.  
  
 **Установка или возврат SRID экземпляра**  
 [Тип данных STSrid &#40;geography&#41;](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 Это свойство можно изменять.  
  
##  <a name="rel"></a>Определение связей между экземплярами geography  
 Тип данных `geography` предоставляет множество встроенных методов, с помощью которых можно определить связи между двумя объектами типа `geography`.  
  
 **Определение того, что два экземпляра состоят из одного набора точек**  
 [STEquals &#40;типа данных geometry&#41;](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 **Определение, являются ли два экземпляра несвязанными**  
 [STDisjoint &#40;типа данных geometry&#41;](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 **Определение пересечения двух экземпляров**  
 [STIntersects &#40;типа данных geometry&#41;](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 **Определение точки или точек пересечения двух экземпляров**  
 [Тип данных STIntersection &#40;geography&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **Определение кратчайшего расстояния между точками в двух экземплярах geography**  
 [STDistance &#40;типа данных geometry&#41;](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 **Определение разницы между двумя экземплярами geography**  
 [Тип данных STDifference &#40;geography&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 **Получение симметричной разницы или уникальных точек одного экземпляра geography по сравнению с другим экземпляром**  
 [Тип данных STSymDifference &#40;geography&#41;](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="supportedsrid"></a>Экземпляры geography должны использовать поддерживаемые SRID  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживаются идентификаторы SRID, основанные на стандартах EPSG. При выполнении вычислений или применении методов работы с географическими пространственными данными должны использоваться поддерживаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентификаторы SRID для экземпляров `geography`. Заданный SRID должен соответствовать одному из идентификаторов SRID, отображенных в представлении каталога **sys.spatial_reference_systems** . Как было упомянуто ранее, результаты вычислений на пространственных данных с использованием типа данных `geography` зависят от эллипсоида, использованного при создании рабочих данных, поскольку каждому эллипсоиду назначается отдельный идентификатор пространственной ссылки (SRID).  
  
 При применении методов к экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в `geography` используется значение идентификатора SRID по умолчанию, равное 4326, соответствующее системе пространственных ссылок WGS 84. Если используются данные системы пространственных ссылок, отличной от WGS 84 (или если значение SRID отличается от 4326), для собственных географических пространственных данных необходимо определить отдельный идентификатор SRID.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Пространственные данные (SQL Server)](spatial-data-sql-server.md)  
  
  
