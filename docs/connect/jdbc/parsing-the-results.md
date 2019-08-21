---
title: Анализ результатов | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: rene-ye
ms.author: v-reye
manager: kenvh
ms.openlocfilehash: 127c97ec155ef1e19df4103b12a6e10b8b67fe74
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027860"
---
# <a name="parsing-the-results"></a>Анализ результатов

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье описывается, как SQL Server планирует, чтобы пользователи полностью обрабатывали результаты, возвращаемые из любого запроса.

## <a name="update-counts-and-result-sets"></a>Количество обновлений и результирующие наборы

В этом разделе будут обсуждаться два наиболее распространенных результата, возвращаемых из SQL Server: число обновлений и набор результатов. В общем случае любой запрос, выполняемый пользователем, приведет к возвращению одного из этих результатов. при обработке результатов пользователи должны обрабатывать обе эти операции.

Следующий код является примером того, как пользователь может перебрать все результаты с сервера:
```java
try (Connection connection = DriverManager.getConnection(URL); Statement statement = connection.createStatement()) {
    boolean resultsAvailable = statement.execute(USER_SQL);
    int updateCount = -2;
    while (true) {
        updateCount = statement.getUpdateCount();
        if (!resultsAvailable && updateCount == -1)
            break;
        if (resultsAvailable) {
            // handle ResultSet
        } else {
            // handle Update Count
        }
        resultsAvailable = statement.getMoreResults();
    }
}
```

## <a name="exceptions"></a>Исключения
При выполнении инструкции, которая приводит к ошибке или информационному сообщению, SQL Server будет отвечать по-разному в зависимости от того, может ли он создать план выполнения. Сообщение об ошибке может быть создано сразу после выполнения инструкции или может требовать отдельный результирующий набор. В последнем случае приложения должны проанализировать результирующий набор, чтобы получить исключение.

Если SQL Server не удается создать план выполнения, исключение создается немедленно.

```java
String SQL = "SELECT * FROM nonexistentTable;";
try (Statement statement = connection.createStatement();) {
    statement.execute(SQL);
} catch (SQLException e) {
    e.printStackTrace();
}
```

Когда SQL Server возвращает сообщение об ошибке в результирующем наборе, необходимо обработать результирующий набор, чтобы получить исключение.

```java
String SQL = "SELECT 1/0;";
try (Statement statement = connection.createStatement();) {
    boolean hasResult = statement.execute(SQL);
    if (hasResult) {
        try (ResultSet rs = statement.getResultSet()) {
            // Exception is thrown on next().
            while (rs.next()) {}
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

Если при выполнении инструкции создается несколько результирующих наборов, то каждый результирующий набор должен обрабатываться до тех пор, пока не будет достигнуто исключение.

```java
String SQL = "SELECT 1; SELECT * FROM nonexistentTable;";
try (Statement statement = connection.createStatement();) {
    // Does not throw an exception on execute().
    boolean hasResult = statement.execute(SQL);
    while (hasResult) {
        try (ResultSet rs = statement.getResultSet()) {
            while (rs.next()) {
                System.out.println(rs.getString(1));
            }
        }
        // Moves the next result set that generates the exception.
        hasResult = statement.getMoreResults();
    }
} catch (SQLException e) {
    e.printStackTrace();
}
```

В случае `String SQL = "SELECT * FROM nonexistentTable; SELECT 1;";`исключение вызывается немедленно в `execute()` и `SELECT 1` не выполняется вообще.

Если ошибка из SQL Server имеет серьезность `0` `9`, то она рассматривается как информационное сообщение и возвращается как `SQLWarning`.

```java
String SQL = "RAISERROR ('WarningLevel5', 5, 2);";
try (Statement statement = connection.createStatement();) {
    boolean hasResult = statement.execute(SQL);
    SQLWarning warning = statement.getWarnings();
    System.out.println(warning);
}
```

## <a name="see-also"></a>См. также раздел

[Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)
