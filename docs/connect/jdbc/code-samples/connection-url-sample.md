---
title: Пример URL-адреса подключения | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3f65b4774564546907e14302552ad129160e55a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957258"
---
# <a name="connection-url-sample"></a>Образец URL-адреса соединения

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Этот пример приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показывает, как соединиться с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по URL-адресу соединения. Приложение также показывает, как извлечь данные из базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при помощи инструкции SQL.

Файл кода для этого образца имеет имя СonnectURL.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\connections
```

## <a name="requirements"></a>Требования

Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о настройке подкаталогов классов см. в разделе [Использование драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Для получения дополнительных сведений о том, какой JAR-файл выбрать, см. статью [Требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В следующем примере образец кода задает различные свойства соединения в URL-адресе соединения и затем вызывает метод getConnection класса DriverManager, чтобы вернуть объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).

Далее образец кода использует метод [createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) объекта SQLServerConnection, чтобы создать объект [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), после чего вызывается метод [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) для выполнения инструкции SQL.

Наконец, в образце используется объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), возвращенный из метода executeQuery, для прохода по результатам, возвращенным инструкцией SQL.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ConnectURL {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT TOP 10 * FROM Person.Contact";
            ResultSet rs = stmt.executeQuery(SQL);

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println(rs.getString("FirstName") + " " + rs.getString("LastName"));
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## <a name="see-also"></a>См. также:

[Подключение к данным и их извлечение](../../../connect/jdbc/code-samples/connecting-and-retrieving-data.md)
