---
title: Использование пространственных типов Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f133fa066ef2c486cf7bb40c5b653c99e077bc46
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026944"
---
# <a name="using-spatial-datatypes"></a>Использование пространственных типов данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Пространственные типы (Geometry и geography) поддерживаются при запуске предварительной версии драйвера JDBC 6.5.0 RELEASE. Пространственные типы данных в настоящее время не поддерживаются хранимыми процедурами, параметрами с табличным значением (TVP), BulkCopy и Always Encrypted. На этой странице показаны различные варианты использования геометрических и географических типов данных с помощью драйвера JDBC. Общие сведения о пространственных типах данных см. на странице с [обзором пространственных типов](https://docs.microsoft.com/sql/relational-databases/spatial/spatial-data-types-overview) .

## <a name="creating-a-geometry--geography-object"></a>Создание объекта geometry или geography

Существует два основных способа создания объекта geometry или geography — либо преобразовать из хорошо известного текста (WKT), либо как хорошо известный двоичный файл (WKB).

### <a name="creating-from-wkt"></a>Создание из WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

При этом будет создан объект Geometry LINESTRING с идентификатором системы пространственной ссылки (SRID) 0, а также объект geography с SRID 4326.

### <a name="creating-from-wkb"></a>Создание из WKB

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

Будет создан объект Geometry и geography, эквивалентный ранее созданным из WKT.

## <a name="working-with-a-geometry--geography-object"></a>Работа с объектом Geometry или geography

Предполагая, что у пользователя есть таблица на SQL Server, как показано ниже:

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Пример скрипта для вставки значения геометрии:

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

То же самое можно сделать для географического объекта, используя столбец geography и метод **сетжеографи ()** .

Чтобы считать столбец геометрии или geography, выполните следующие действия.

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

То же самое можно сделать для одного географического объекта с помощью географического столбца и метода **-geography ()** .

## <a name="newly-introduced-apis"></a>Вновь появившиеся API

Это новые общедоступные API, которые появились с помощью этого сложения, в классах **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometry**и **Geography**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Метод|Описание|
|:------|:----------|
|void setGeometry(int n, Geometry x)| Задает указанный параметр для заданного объекта класса Microsoft. SQL. Geometry.
|void Сетжеографи (int n, geography x)| Задает указанный параметр для заданного объекта класса Microsoft. SQL. geography.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Метод|Описание|
|:------|:----------|
|Геометрическая геометрия (int Колуниндекс)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта COM. Microsoft. SqlServer. JDBC. Geometry на языке программирования Java.
|Геометрическая геометрия (String columnName)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта COM. Microsoft. SqlServer. JDBC. Geometry на языке программирования Java.
|География geography (int Колуниндекс)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта COM. Microsoft. SqlServer. JDBC. geography на языке программирования Java.
|География geography (строковое columnName)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта COM. Microsoft. SqlServer. JDBC. geography на языке программирования Java.

### <a name="geometry"></a>Geometry

|Метод|Описание|
|:------|:----------|
|Геометрический STGeomFromText (String WKT, int SRID)| Конструктор экземпляра Geometry из WKT-представления Открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), входящими в экземпляр.
|Геометрический STGeomFromWKB (Byte [] WKB)| Конструктор экземпляра Geometry из WKB-представления Открытого геопространственного консорциума (OGC).
|Несериализуемые геометрические объекты (Byte [] WKB)| Конструктор для экземпляра geometry из внутреннего формата SQL Server для пространственных данных.
|Анализ геометрии (String WKT)| Конструктор экземпляра Geometry из WKT-представления Открытого геопространственного консорциума (OGC). Идентификатор пространственной ссылки по умолчанию равен 0.
|Геометрическая точка (двойной x, Double y, int SRID)| Конструктор для экземпляра geometry, представляющий экземпляр Point из его значений X и Y и идентификатора пространственной ссылки.
|String STAsText()| Возвращает WKT-представление Открытого геопространственного консорциума (OGC) для экземпляра Geometry. Этот текст не будет содержать значений Z (высота) и M (мера), сопровождающих экземпляр.
|byte[] STAsBinary()| Возвращает WKB-представление Открытого геопространственного консорциума (OGC) для экземпляра Geometry. Это значение не будет содержать значений Z и M, сопровождающих экземпляр.
|byte[] serialize()| Возвращает байты, представляющие внутренний формат типа Geometry в SQL Server.
|Логическое hasM ()| Возвращает, если объект содержит значение M (мера).
|Логическое hasZ ()| Возвращает, если объект содержит значение Z (повышение).
|Double Жеткс ()| Возвращает значение координаты X.
|Double Жети ()| Возвращает значение координаты Y.
|Double Жетм ()| Возвращает значение M (мера) объекта.
|Double Гетц ()| Возвращает значение Z (повышение) объекта.
|int getSrid()| Возвращает значение идентификатора пространственной ссылки (SRID).
|Логическая функция isNull ()| Возвращает, если объект Geometry имеет значение null.
|int STNumPoints ()| Возвращает количество точек в объекте Geometry.
|String STGeometryType()| Возвращает имя типа OGC, представленное экземпляром геометрического объекта.
|String asTextZM()| Возвращает хорошо известное текстовое (WKT) представление объекта Geometry.
|String toString ()| Возвращает строковое представление объекта Geometry.

### <a name="geography"></a>Geography

|Метод|Описание|
|:------|:----------|
|Geography STGeomFromText (строка WKT, int SRID)| Конструктор экземпляра Geography из WKT-представления Открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), входящими в экземпляр.
|Географическая STGeomFromWKB (Byte [] WKB)| Конструктор экземпляра Geography из WKB-представления Открытого геопространственного консорциума (OGC).
|Десериализация географии (Byte [] WKB)| Конструктор для экземпляра geography из внутреннего формата SQL Server для пространственных данных.
|Анализ географии (String WKT)| Конструктор экземпляра Geography из WKT-представления Открытого геопространственного консорциума (OGC). Идентификатор пространственной ссылки по умолчанию равен 0.
|Географическая точка (Double Долгота, двойная Широта, int SRID)| Конструктор экземпляра Geography, представляющий экземпляр Point по значениям широты и долготы и идентификатору пространственной привязки.
|String STAsText()| Возвращает WKT-представление Открытого геопространственного консорциума (OGC) для экземпляра Geography. Этот текст не будет содержать значений Z (высота) и M (мера), сопровождающих экземпляр.
|byte[] STAsBinary())| Возвращает WKB-представление Открытого геопространственного консорциума (OGC) для экземпляра Geography. Это значение не будет содержать значений Z и M, сопровождающих экземпляр.
|byte[] serialize()| Возвращает байты, представляющие внутренний формат типа Geography в SQL Server.
|Логическое hasM ()| Возвращает, если объект содержит значение M (мера).
|Логическое hasZ ()| Возвращает, если объект содержит значение Z (повышение).
|Двойное Широта ()| Возвращает значение широты.
|Двойная Долгота ()| Возвращает значение долготы.
|Double Жетм ()| Возвращает значение M (мера) объекта.
|Double Гетц ()| Возвращает значение Z (повышение) объекта.
|int getSrid()| Возвращает значение идентификатора пространственной ссылки (SRID).
|Логическая функция isNull ()| Возвращает, если объект geography имеет значение null.
|int STNumPoints ()| Возвращает количество точек в объекте geography.
|String STGeographyType()| Возвращает имя типа OGC, представленное экземпляром географического объекта.
|String asTextZM()| Возвращает хорошо известное текстовое (WKT) представление объекта geography.
|String toString ()| Возвращает строковое представление объекта Geography.

## <a name="limitations-of-spatial-datatypes"></a>Ограничения пространственных типов данных

1. Пространственные типы **CircularString**, **CompoundCurve**, **CurvePolygon**и **FullGlobe** поддерживаются только начиная с SQL Server 2012 и более поздних версий.

2. Always Encrypted нельзя использовать с пространственными типами.

3. Операции хранимых процедур, TVP и BulkCopy в настоящее время не поддерживаются для пространственных типов.

## <a name="see-also"></a>См. также раздел

[Пример пространственных типов данных (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
