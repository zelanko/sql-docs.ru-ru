---
title: Использование типа данных Sql_variant | Документация Майкрософт
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
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69025839"
---
# <a name="using-sql_variant-data-type"></a>Использование данных типа sql_variant

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Начиная с версии 6.3.0 Драйвер JDBC поддерживает тип данных sql_variant. Sql_variant также поддерживается при использовании таких функций, как возвращающие табличные значения параметры, и BulkCopy с некоторыми ограничениями, упомянутыми далее на этой странице. Не все типы данных могут храниться в типе данных sql_variant. Чтобы получить список поддерживаемых типов данных с типом sql_variant, проверьте [документацию](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql) по SQL Server.

##  <a name="populating-and-retrieving-a-table"></a>Заполнение и получение таблицы:
Предположим, что у одного столбца есть таблица со столбцом sql_variant:

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Пример скрипта для вставки значений с помощью инструкции:

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

Вставка значения с помощью подготовленной инструкции:

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

Если известен базовый тип передаваемых данных, можно использовать соответствующий метод задания. Например, `preparedStatement.setInt()` может использоваться при вставке целочисленного значения.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Для чтения значений из таблицы можно использовать соответствующие методы получения. Например, можно `getInt()` использовать `getString()` методы или, если значения, поступающие от сервера, известны:    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sql_variant"></a>Использование хранимых процедур с sql_variant:   
Наличие хранимой процедуры, например:     

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

## <a name="limitations-of-sql_variant"></a>Ограничения типа sql_variant:
- При использовании `datetime` TVP для заполнения таблицы / `getSmallDateTime()` / `getDateTime()` `smalldatetime` значением, хранящимся в sql_variant, вызов`getDate()` метода / / `date` ResultSet не работает и вызывает следующее исключение:
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Обходное решение `getString()` . `getObject()` используйте или. 
    
- Использование TVP для заполнения таблицы и отправки значения NULL в sql_variant не поддерживается и вызывает исключение:
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>См. также раздел

[Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
