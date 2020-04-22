---
title: Шаг 3. Подключение к SQL с помощью Java
description: Шаг 3 — это подтверждение концепции, которое показывает, как можно подключиться к SQL Server с помощью Java и JDBC. В этих простых примерах демонстрируется выделение и вставка данных.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1504a348-1774-47ab-8967-288ec3985ae4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 966c931f5012e5701a0f6db0bd64503be1189d50
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528898"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-java"></a>Шаг 3. Подтверждение концепции: подключение к SQL с помощью Java
  
Этот пример следует рассматривать только как подтверждение концепции. Пример кода упрощен для ясности и для него не гарантируется соблюдение рекомендаций корпорации Майкрософт.  
  
## <a name="step-1-connect"></a>Шаг 1. Подключение  
  
Используйте класс подключения для подключения к базе данных SQL.   
  
```java  
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class SQLDatabaseConnection {
    // Connect to your database.
    // Replace server name, username, and password with your credentials
    public static void main(String[] args) {
        String connectionUrl =
                "jdbc:sqlserver://yourserver.database.windows.net:1433;"
                        + "database=AdventureWorks;"
                        + "user=yourusername@yourserver;"
                        + "password=yourpassword;"
                        + "encrypt=true;"
                        + "trustServerCertificate=false;"
                        + "loginTimeout=30;";

        try (Connection connection = DriverManager.getConnection(connectionUrl);) {
            // Code here.
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```  
  
## <a name="step-2-execute-a-query"></a>Шаг 2. Выполнение запроса  
В этом примере следует подключиться к базе данных SQL Azure, выполнить инструкцию SELECT и вернуть выбранные строки.   
  
```java  
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class SQLDatabaseConnection {

    // Connect to your database.
    // Replace server name, username, and password with your credentials
    public static void main(String[] args) {
        String connectionUrl =
                "jdbc:sqlserver://yourserver.database.windows.net:1433;"
                + "database=AdventureWorks;"
                + "user=yourusername@yourserver;"
                + "password=yourpassword;"
                + "encrypt=true;"
                + "trustServerCertificate=false;"
                + "loginTimeout=30;";

        ResultSet resultSet = null;

        try (Connection connection = DriverManager.getConnection(connectionUrl);
                Statement statement = connection.createStatement();) {

            // Create and execute a SELECT SQL statement.
            String selectSql = "SELECT TOP 10 Title, FirstName, LastName from SalesLT.Customer";
            resultSet = statement.executeQuery(selectSql);

            // Print results from select statement
            while (resultSet.next()) {
                System.out.println(resultSet.getString(2) + " " + resultSet.getString(3));
            }
        }
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```  
  
## <a name="step-3-insert-a-row"></a>Шаг 3. Вставка строки  
В этом примере следует выполнить инструкцию INSERT, передать параметры и извлечь автоматически созданное значение первичного ключа.   
  
```java  
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.Statement;

public class SQLDatabaseConnection {

    // Connect to your database.
    // Replace server name, username, and password with your credentials
    public static void main(String[] args) {
        String connectionUrl =
                "jdbc:sqlserver://yourserver.database.windows.net:1433;"
                        + "database=AdventureWorks;"
                        + "user=yourusername@yourserver;"
                        + "password=yourpassword;"
                        + "encrypt=true;"
                        + "trustServerCertificate=false;"
                        + "loginTimeout=30;";

        String insertSql = "INSERT INTO SalesLT.Product (Name, ProductNumber, Color, StandardCost, ListPrice, SellStartDate) VALUES "
                + "('NewBike', 'BikeNew', 'Blue', 50, 120, '2016-01-01');";

        ResultSet resultSet = null;

        try (Connection connection = DriverManager.getConnection(connectionUrl);
                PreparedStatement prepsInsertProduct = connection.prepareStatement(insertSql, Statement.RETURN_GENERATED_KEYS);) {

            prepsInsertProduct.execute();
            // Retrieve the generated key from the insert.
            resultSet = prepsInsertProduct.getGeneratedKeys();

            // Print the ID of the inserted row.
            while (resultSet.next()) {
                System.out.println("Generated: " + resultSet.getString(1));
            }
        }
        // Handle any errors that may have occurred.
        catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```  
  
## <a name="additional-samples"></a>Дополнительные примеры  
[Примеры приложений JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)
