---
title: Использование типа данных Sql_variant | Документация Майкрософт
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8df6fcee7b79f0c85f1182442195eb2cdf8d7ac9
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737352"
---
# <a name="using-sqlvariant-data-type"></a>Использование данных типа sql_variant

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Начиная с версии 6.3.0 драйвер JDBC поддерживает тип данных sql_variant. Sql_variant поддерживается также в том случае, если с помощью функции, такие как параметры с табличным значением и BulkCopy с некоторыми ограничениями упоминалось эту страницу позже. Не все типы данных могут храниться в тип данных sql_variant. Список поддерживаемых типов данных с sql_variant, см. в SQL Server [документация](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql).

##  <a name="populating-and-retrieving-a-table"></a>Заполнение и получение таблицы:
При условии, что одно содержит таблицу со столбцом типа sql_variant как:

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Пример сценария для вставки значений, с помощью инструкции:

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

Если известен базовый тип передаваемых данных, можно использовать соответствующие задания. Например `preparedStatement.setInt()` может использоваться при вставке целочисленное значение.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Для чтения значений из таблицы, можно использовать соответствующие методы Get. Например `getInt()` или `getString()` методы можно использовать, если известными значениями, приходящие с сервера:    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sqlvariant"></a>Использование хранимых процедур с sql_variant:   
Например, наличие хранимой процедуры:     

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

## <a name="limitations-of-sqlvariant"></a>Ограничения sql_variant:
- При использовании возвращающего табличное значение Параметра для заполнения таблицы с `datetime` / `smalldatetime` / `date` значение, хранящееся в sql_variant, вызвав `getDateTime()` / `getSmallDateTime()` / `getDate()` на Результирующий набор не работает и вызывает следующее исключение:
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Решение: используйте `getString()` или `getObject()` вместо этого. 
    
- Использование возвращающего табличное значение Параметра для заполнения таблицы и отправка значение null в sql_variant не поддерживается и создает исключение:
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>См. также:

[Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
