---
title: Образец источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e199eff1bf1667ea66d5b4191d911534dfc4dd7c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66770054"
---
# <a name="data-source-sample"></a>Образец источника данных

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Этот пример приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показывает, как установить соединение с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] через объект источника данных. Приложение также демонстрирует извлечение данных из базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью хранимой процедуры.

Файл кода для этого примера с именем ConnectDataSource.java находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\connections
```

## <a name="requirements"></a>Требования

Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Для получения дополнительных сведений о том, какой JAR-файл выбрать, см. статью [Требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В следующем примере образец кода задает различные свойства соединения с помощью методов задания объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md), затем вызывает метод [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) объекта SQLServerDataSource, чтобы вернуть объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).

Далее образец кода создает объект [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) с помощью метода [prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) объекта SQLServerConnection, после чего вызывается метод [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) для выполнения хранимой процедуры.

Наконец, для прохода по результатам, возвращенным хранимой процедурой, используется объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), возвращенный из метода executeQuery.

```java
import java.sql.CallableStatement;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class ConnectDataSource {

    public static void main(String[] args) {

        // Create datasource.
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setUser("<user>");
        ds.setPassword("<password>");
        ds.setServerName("<server>");
        ds.setPortNumber(Integer.parseInt("<port>"));
        ds.setDatabaseName("AdventureWorks");

        try (Connection con = ds.getConnection();
                CallableStatement cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");) {
            // Execute a stored procedure that returns some data.
            cstmt.setInt(1, 50);
            ResultSet rs = cstmt.executeQuery();

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println("EMPLOYEE: " + rs.getString("LastName") + ", " + rs.getString("FirstName"));
                System.out.println("MANAGER: " + rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));
                System.out.println();
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
