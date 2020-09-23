---
description: Использование пространственных типов данных
title: Использование пространственных типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0f4b01775e2c78c0cc8602539169a794eb476f92
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487965"
---
# <a name="using-spatial-datatypes"></a>Использование пространственных типов данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Пространственные типы данных (Geometry и Geography) поддерживаются, начиная с предварительного выпуска драйвера JDBC версии 6.5.0. Пространственные типы данных в настоящее время не поддерживаются с хранимыми процедурами, параметрами с табличным значением (TVP), функциями BulkCopy и Always Encrypted. На этой странице показаны различные варианты использования типов данных Geometry и Geography с помощью драйвера JDBC. Общие сведения о пространственных типах данных см. в [этой статье](https://docs.microsoft.com/sql/relational-databases/spatial/spatial-data-types-overview).

## <a name="creating-a-geometry--geography-object"></a>Создание объекта Geometry или Geography

Есть два основных способа создания объекта Geometry или Geography — преобразовать из формата Well-Known Text (WKT) или из внутреннего формата SQL Server (CLR).

### <a name="creating-from-wkt"></a>Создание из формата WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

В рамках этой операции будет создан объект Geometry LINESTRING с идентификатором системы пространственных ссылок (SRID) 0, а также объект Geography с SRID 4326.

### <a name="creating-from-clr"></a>Создание из формата CLR

```java
byte[] geomCLR = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogCLR = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomCLR);
Geography geogWKT = Geography.deserialize(geogCLR);
```

Будут созданы объекты Geometry и Geography, эквивалентные ранее созданным из WKT.

## <a name="working-with-a-geometry--geography-object"></a>Работа с объектами Geometry или Geography

Предполагая, что у пользователя есть таблица в SQL Server, как показано ниже:

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Пример скрипта для вставки значения Geometry:

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
```

То же самое можно сделать для эквивалентного элемента объекта Geography, используя столбец Geography и метод **setGeography()**.

Чтобы считать столбец Geometry или Geography, выполните следующие действия.

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

То же самое можно сделать для эквивалентного элемента объекта Geography, используя столбец Geography и метод **getGeography()**.

## <a name="newly-introduced-apis"></a>Новые API-интерфейсы

Это новые общедоступные API-интерфейсы, которые появились в этом дополнении в классах **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometry** и **Geography**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Метод|Описание|
|:------|:----------|
|void setGeometry(int n, Geometry x)| Задает указанный параметр для заданного объекта класса microsoft.sql.Geometry.
|void setGeography(int n, Geography x)| Задает указанный параметр для заданного объекта класса microsoft.sql.Geography.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Метод|Описание|
|:------|:----------|
|Geometry getGeometry(int colunIndex)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта com.microsoft.sqlserver.jdbc.Geometry на языке программирования Java.
|Geometry getGeometry(String columnName)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта com.microsoft.sqlserver.jdbc.Geometry на языке программирования Java.
|Geography getGeography(int colunIndex)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта com.microsoft.sqlserver.jdbc.Geography на языке программирования Java.
|Geography getGeography(String columnName)| Возвращает значение указанного столбца в текущей строке этого объекта ResultSet в виде объекта com.microsoft.sqlserver.jdbc.Geography на языке программирования Java.

### <a name="geometry"></a>Геометрия

|Метод|Описание|
|:------|:----------|
|Geometry STGeomFromText(String wkt, int SRID)| Конструктор экземпляра Geometry из WKT-представления Открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), входящими в экземпляр.
|Geometry STGeomFromWKB(byte[] wkb)| Конструктор экземпляра Geometry из WKB-представления Открытого геопространственного консорциума (OGC). Примечание. В настоящее время этот метод использует внутренний формат SQL Server (CLR) для создания экземпляра Geometry, что является известной проблемой в драйвере и сейчас его планируется изменить, чтобы вместо этого принимать данные WKB. Для существующих пользователей, которые уже используют этот метод, рекомендуем вместо этого перейти на deserialize(byte).
|Geometries deserialize(byte[] clr)| Конструктор для экземпляра Geometry из внутреннего формата SQL Server для пространственных данных.
|Geometry parse(String wkt)| Конструктор экземпляра Geometry из WKT-представления Открытого геопространственного консорциума (OGC). Идентификатор пространственной ссылки по умолчанию равен 0.
|Geometry point(double x, double y, int SRID)| Конструктор экземпляра Geometry, представляющий экземпляр Point по значениям X и Y и идентификатору пространственной привязки.
|String STAsText()| Возвращает WKT-представление Открытого геопространственного консорциума (OGC) для экземпляра Geometry. Этот текст не будет содержать значений Z (высота) и M (мера), сопровождающих экземпляр.
|byte[] STAsBinary()| Возвращает представление экземпляра Geometry во внутреннем формате SQL Server (CLR). Это значение не будет содержать значений Z и M, сопровождающих экземпляр.
|byte[] serialize()| Возвращает байты, представляющие внутренний формат типа Geometry в SQL Server.
|boolean hasM()| Возвращается, если объект содержит значение M (мера).
|boolean hasZ()| Возвращается, если объект содержит значение Z (высота).
|Double getX()| Возвращает значение координаты X.
|Double getY()| Возвращает значение координаты Y.
|Double getM()| Возвращает значение M (мера) для объекта.
|Double getZ()| Возвращает значение Z (высота) для объекта.
|int getSrid()| Возвращает значение идентификатора пространственной ссылки (SRID).
|boolean isNull()| Возвращается, если объект Geometry имеет значение NULL.
|int STNumPoints()| Возвращает количество точек в объекте Geometry.
|String STGeometryType()| Возвращает имя типа OGC, представленное экземпляром геометрического объекта.
|String asTextZM()| Возвращает представление объекта Geometry в формате Well-Known Text (WKT).
|String toString()| Возвращает строковое представление объекта Geometry.

### <a name="geography"></a>Geography

|Метод|Описание|
|:------|:----------|
|Geography STGeomFromText(String wkt, int SRID)| Конструктор экземпляра Geography из WKT-представления Открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), входящими в экземпляр.
|Geography STGeomFromWKB(byte[] wkb)| Конструктор экземпляра Geography из WKB-представления Открытого геопространственного консорциума (OGC). Примечание. В настоящее время этот метод использует внутренний формат SQL Server (CLR) для создания экземпляра Geometry, но в будущем он будет изменен для получения данных WKB, поскольку аналог этого метода в SQL Server (STGeomFromWKB) использует WKB. Для существующих пользователей, которые уже используют этот метод, рекомендуем вместо этого перейти на deserialize(byte).
|Geography deserialize(byte[] clr)| Конструктор для экземпляра Geography из внутреннего формата SQL Server для пространственных данных.
|Geography parse(String wkt)| Конструктор экземпляра Geography из WKT-представления Открытого геопространственного консорциума (OGC). Идентификатор пространственной ссылки по умолчанию равен 0.
|Geography point(double lon, double lat, int SRID)| Конструктор экземпляра Geography, представляющий экземпляр Point по значениям широты и долготы и идентификатору пространственной привязки.
|String STAsText()| Возвращает WKT-представление Открытого геопространственного консорциума (OGC) для экземпляра Geography. Этот текст не будет содержать значений Z (высота) и M (мера), сопровождающих экземпляр.
|byte[] STAsBinary())| Возвращает представление экземпляра Geography во внутреннем формате SQL Server (CLR). Это значение не будет содержать значений Z и M, сопровождающих экземпляр.
|byte[] serialize()| Возвращает байты, представляющие внутренний формат типа Geography в SQL Server.
|boolean hasM()| Возвращается, если объект содержит значение M (мера).
|boolean hasZ()| Возвращается, если объект содержит значение Z (высота).
|Double getLatitude()| Возвращает значение широты.
|Double getLongitude()| Возвращает значение долготы.
|Double getM()| Возвращает значение M (мера) для объекта.
|Double getZ()| Возвращает значение Z (высота) для объекта.
|int getSrid()| Возвращает значение идентификатора пространственной ссылки (SRID).
|boolean isNull()| Возвращается, если объект Geography имеет значение NULL.
|int STNumPoints()| Возвращает количество точек в объекте Geography.
|String STGeographyType()| Возвращает имя типа OGC, представленное экземпляром географического объекта.
|String asTextZM()| Возвращает представление объекта Geography в формате Well-Known Text (WKT).
|String toString()| Возвращает строковое представление объекта Geography.

## <a name="limitations-of-spatial-datatypes"></a>Ограничения пространственных типов данных

1. Подтипы пространственных типов данных **CircularString**, **CompoundCurve**, **CurvePolygon** и **FullGlobe** поддерживаются только начиная с SQL Server 2012 и более поздних версий.

2. Функцию Always Encrypted нельзя использовать с пространственными типами.

3. Операции хранимых процедур, TVP и BulkCopy в настоящее время не поддерживаются для пространственных типов.

## <a name="see-also"></a>См. также раздел

[Пример пространственных типов данных (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
