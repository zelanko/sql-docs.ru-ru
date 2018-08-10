---
title: С помощью пространственных типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11d8ae48709f99f466fb0b0c6e387ad38336da5f
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467692"
---
# <a name="using-spatial-datatypes"></a>Использование пространственных типов данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Пространственные типы данных (Geometry и Geography) поддерживаются начиная с предварительной версии драйвера JDBC 6.5.0. Пространственные типы данных в настоящее время не поддерживает хранимые процедуры, таблицы с табличным значением параметров (TVP), BulkCopy и постоянного шифрования. Эта страница показывает, что различные использования типов данных Geometry и Geography с драйвером JDBC. Общие сведения о пространственных типов данных, проверьте [Общие сведения о типах пространственных данных](https://docs.microsoft.com/en-us/sql/relational-databases/spatial/spatial-data-types-overview) страницы.

## <a name="creating-a-geometry--geography-object"></a>Создание геометрического объекта / географический объект

Существует два основных способа создания геометрический или географический объект - либо преобразовать из Well-Known Text (WKT) или из Well-Known Binary (WKB).

### <a name="creating-from-wkt"></a>Создание из WKT

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);
```

Это создаст объект LINESTRING Geometry с идентификатор Пространственные системы ссылки (SRID) 0 и географический объект с SRID 4326.

### <a name="creating-from-wkb"></a>Создание из WKB

```java
byte[] geomWKB = Hex.decodeHex("00000000010403000000000000000000F03F00000000000000000000000000000000000000000000F03F000000000000F0BF000000000000000001000000010000000001000000FFFFFFFF0000000002".toCharArray());
byte[] geogWKB = Hex.decodeHex("E61000000104030000000000000000000000000000000000F03F000000000000F03F00000000000000000000000000000000000000000000F0BF01000000010000000001000000FFFFFFFF0000000002".toCharArray());

Geometry geomWKT = Geometry.deserialize(geomWKB);
Geography geogWKT = Geography.deserialize(geogWKB);
```

Это создаст объект Geometry и Geography, эквивалентный ранее созданы в формате WKT.

## <a name="working-with-a-geometry--geography-object"></a>Работа с геометрический или географический объект

Предполагая, что пользователь имеет таблицу на сервере SQL Server как ниже:

```sql
CREATE TABLE sampleTable (c1 geometry)  
```

Пример сценария для вставки значения геометрического объекта будет следующим:

```java
String geoWKT = "LINESTRING(1 0, 0 1, -1 0)";
Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) connection.prepareStatement("insert into sampleTable values (?)");
pstmt.setGeometry(1, geomWKT);  
pstmt.execute();
``` 

То же можно сделать для какой Geography, с помощью столбца типа Geography и **setGeography()** метод.

Для чтения геометрического или географического столбца:

```java
try(SQLServerResultSet rs = (SQLServerResultSet)stmt.executeQuery("select * from geomTable")) {
    while(rs.next()){
        rs.getGeometry(1);
    }
}
```

То же можно сделать для какой Geography, с помощью столбца типа Geography и **getGeography()** метод.

## <a name="newly-introduced-apis"></a>Новых API-интерфейсов

Это новый открытый API, были введены в результате этого добавления в классах **SQLServerPreparedStatement**, **SQLServerResultSet**, **Geometry**и  **География**.

### <a name="sqlserverpreparedstatement"></a>SQLServerPreparedStatement

|Метод|Описание|
|:------|:----------|
|void setGeometry (int n, Geometry x)| Задает указанному параметру microsoft.sql.Geometry заданного объекта класса.
|void setGeography (int n, География x)| Задает указанному параметру microsoft.sql.Geography заданного объекта класса.

### <a name="sqlserverresultset"></a>SQLServerResultSet

|Метод|Описание|
|:------|:----------|
|Geometry getGeometry (int colunIndex)| Возвращает значение заданного столбца в текущей строке этого объекта ResultSet в виде com.microsoft.sqlserver.jdbc.Geometry объекта на языке программирования Java.
|Geometry getGeometry (columnName строка)| Возвращает значение заданного столбца в текущей строке этого объекта ResultSet в виде com.microsoft.sqlserver.jdbc.Geometry объекта на языке программирования Java.
|География getGeography (int colunIndex)| Возвращает значение заданного столбца в текущей строке этого объекта ResultSet в виде com.microsoft.sqlserver.jdbc.Geography объекта на языке программирования Java.
|География getGeography (columnName строка)| Возвращает значение заданного столбца в текущей строке этого объекта ResultSet в виде com.microsoft.sqlserver.jdbc.Geography объекта на языке программирования Java.

### <a name="geometry"></a>Geometry

|Метод|Описание|
|:------|:----------|
|STGeomFromText геометрии (строка wkt, int SRID)| Конструктор экземпляра Geometry из WKT-представления Открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), входящими в экземпляр.
|STGeomFromWKB геометрии (wkb byte [])| Конструктор экземпляра Geometry из WKB-представления Открытого геопространственного консорциума (OGC).
|Геометрические объекты десериализации (wkb byte [])| Конструктор для экземпляра геометрического объекта из внутреннего формата SQL Server для пространственных данных.
|Синтаксический анализ геометрии (строка в формате wkt)| Конструктор экземпляра Geometry из WKT-представления Открытого геопространственного консорциума (OGC). Идентификатор пространственной ссылки по умолчанию 0.
|Геометрический тип point (double x, y, double, int SRID)| Конструктор, представляющий экземпляр Point, по значениям X и Y и идентификатор пространственной ссылки экземпляра геометрического объекта.
|Строка STAsText()| Возвращает WKT-представление Открытого геопространственного консорциума (OGC) для экземпляра Geometry. Этот текст не будет содержать значений Z (высота) и M (мера), сопровождающих экземпляр.
|Byte [] STAsBinary()| Возвращает WKB-представление Открытого геопространственного консорциума (OGC) для экземпляра Geometry. Это значение не будет содержать значений Z и M, сопровождающих экземпляр.
|serialize() Byte]| Возвращает байты, представляющие внутренний формат типа Geometry в SQL Server.
|Логическое hasM()| Возвращает, если объект содержит значение M (Мера).
|Логическое hasZ()| Возвращает, если объект содержит значение Z (высота).
|Двойные getX()| Возвращает значение координаты X.
|Двойные getY()| Возвращает значение координаты Y.
|Двойные getM()| Возвращает значение M (Мера) объекта.
|Двойные getZ()| Возвращает значение Z (высота) объекта.
|int getSrid()| Возвращает значение идентификатора пространственной ссылки (SRID).
|Логическое isNull()| Возвращает, если объект Geometry имеет значение null.
|int STNumPoints()| Возвращает количество точек в геометрический объект.
|Строка STGeometryType()| Возвращает имя типа OGC, представленное экземпляром геометрического объекта.
|Строка, asTextZM()| Возвращает представление объекта Geometry в формате Well-Known Text (WKT).
|Строка toString()| Возвращает строковое представление объекта Geometry.

### <a name="geography"></a>Geography

|Метод|Описание|
|:------|:----------|
|STGeomFromText Geography (строка wkt, int SRID)| Конструктор экземпляра Geography из WKT-представления Открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), входящими в экземпляр.
|STGeomFromWKB Geography (wkb byte [])| Конструктор экземпляра Geography из WKB-представления Открытого геопространственного консорциума (OGC).
|География десериализации (wkb byte [])| Конструктор для экземпляра географического объекта внутренний формат SQL Server для пространственных данных.
|Синтаксический анализ Geography (строка в формате wkt)| Конструктор экземпляра Geography из WKT-представления Открытого геопространственного консорциума (OGC). Идентификатор пространственной ссылки по умолчанию 0.
|Географическую точку (двойная lat, double lon, int SRID)| Конструктор экземпляра Geography, представляющий экземпляр Point по значениям широты и долготы и идентификатору пространственной привязки.
|Строка STAsText()| Возвращает WKT-представление Открытого геопространственного консорциума (OGC) для экземпляра Geography. Этот текст не будет содержать значений Z (высота) и M (мера), сопровождающих экземпляр.
|Byte [] STAsBinary())| Возвращает WKB-представление Открытого геопространственного консорциума (OGC) для экземпляра Geography. Это значение не будет содержать значений Z и M, сопровождающих экземпляр.
|serialize() Byte]| Возвращает байты, представляющие внутренний формат типа Geography в SQL Server.
|Логическое hasM()| Возвращает, если объект содержит значение M (Мера).
|Логическое hasZ()| Возвращает, если объект содержит значение Z (высота).
|Двойные getLatitude()| Возвращает значение широты.
|Двойные getLongitude()| Возвращает значение долготы.
|Двойные getM()| Возвращает значение M (Мера) объекта.
|Двойные getZ()| Возвращает значение Z (высота) объекта.
|int getSrid()| Возвращает значение идентификатора пространственной ссылки (SRID).
|Логическое isNull()| Возвращает, если географический объект имеет значение null.
|int STNumPoints()| Возвращает количество точек в географический объект.
|Строка STGeographyType()| Возвращает имя типа OGC, представленное экземпляром географического объекта.
|Строка, asTextZM()| Возвращает представление объекта географического объекта в формате Well-Known Text (WKT).
|Строка toString()| Возвращает строковое представление объекта Geography.

## <a name="limitations-of-spatial-datatypes"></a>Ограничения пространственных типов данных

1. Пространственные типы sub данных **CircularString**, **CompoundCurve**, **CurvePolygon**, и **FullGlobe** поддерживаются начиная SQL Server 2012 и более поздних версий.

2. Always Encrypted не может использоваться с пространственных типов данных.

3. Хранимые процедуры, возвращающего табличное значение Параметра и BulkCopy операции в настоящее время не поддерживаются для пространственных типов данных.

## <a name="see-also"></a>См. также:

[Пример пространственных типов данных (JDBC)](../../connect/jdbc/spatial-data-types-sample.md)
