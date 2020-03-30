---
title: Использование данных типа sql_variant | Документация Майкрософт
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
ms.openlocfilehash: cdede5d41d5ad7fc22cfed3f1efa9f95612032ca
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69025839"
---
# <a name="using-sql_variant-data-type"></a>Использование данных типа sql_variant

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Начиная с версии 6.3.0, драйвер JDBC поддерживает тип данных sql_variant. Sql_variant также поддерживается при использовании таких функций, как возвращающие табличные значения параметры и BulkCopy с некоторыми ограничениями, упомянутыми ниже на этой странице. В типе данных sql_variant можно хранить не все типы данных. Чтобы получить список поддерживаемых sql_variant типов данных, см. [документацию](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql) SQL Server.

##  <a name="populating-and-retrieving-a-table"></a>Заполнение и получение таблицы.
Предположим, что у одного столбца есть таблица со столбцом sql_variant:

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Пример скрипта для вставки значений с помощью оператора:

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

Вставка значения с помощью подготовленного оператора:

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

Если известен базовый тип передаваемых данных, можно использовать соответствующий метод задания. Например, при вставке значения с целым числом можно использовать `preparedStatement.setInt()`.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Для чтения значений из таблицы можно использовать соответствующие методы получения. Например, если поступающие от сервера значения известны, можно использовать метод `getInt()` или `getString()`:    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sql_variant"></a>Использование хранимых процедур с sql_variant.   
При наличии хранимой процедуры, например:     

```java
String sql = "CREATE PROCEDURE " + inputProc + " @p0 sql_variant OUTPUT AS SELECT TOP 1 @p0=col1 FROM sampleTable ";
``` 
    
Выходные параметры должны быть зарегистрированы:

```java
try (CallableStatement callableStatement = con.prepareCall(" {call " + inputProc + " (?) }")) {
    callableStatement.registerOutParameter(1, microsoft.sql.Types.SQL_VARIANT);      
    callableStatement.execute();
}
```

## <a name="limitations-of-sql_variant"></a>Ограничения sql_variant.
- При использовании TVP для заполнения таблицы `datetime`/`smalldatetime`/`date` значения, хранящегося в sql_variant, вызов `getDateTime()`/`getSmallDateTime()`/`getDate()` в ResultSet не будет работать и вызовет следующее исключение:
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Обходное решение: вместо этого используйте `getString()` или `getObject()`. 
    
- Использование TVP для заполнения таблицы и отправка нулевого значения в sql_variant не поддерживается и вызывает исключение:
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>См. также раздел

[Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
