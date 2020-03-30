---
title: Пример изменения данных результирующего набора | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b5ae54dc-2a79-4664-bb21-cacdb7d745e1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 52ef5b12771cb7ef65f34dd7d890f19a8541d3ee
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028334"
---
# <a name="modifying-result-set-data-sample"></a>Изменение примера данных результирующего набора

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

В этом примере приложения, где используется [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показано получение обновляемого набора данных из базы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Затем с помощью методов объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) вставляется, изменяется, и в конечном итоге удаляется строка данных из набора данных.

Файл кода для этого примера с именем UpdateResultSet.java находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\resultsets
```

## <a name="requirements"></a>Требования

Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о том, как настроить параметр classpath, см. в статье [Использование JDBC Driver](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о выборе JAR-файла см. в описании [требований к системе для JDBC Driver](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В приведенном ниже примере образец кода будет использоваться для соединения с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Затем выполняется инструкция SQL с объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), и возвращенные ею данные помещаются в обновляемый объект SQLServerResultSet.

Далее образец кода с помощью метода [moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md) перемещает курсор результирующего набора в строку ввода, с помощью серии методов [updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) вводит данные в новую строку, а затем вызывает метод [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) для повторного сохранения новой строки данных в базе данных.

После введения новой строки данных образец кода с помощью инструкции SQL извлекает предварительно введенную строку, а затем использует комбинацию методов updateString и [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) для обновления строки данных и ее повторного сохранения в базе данных.

Наконец образец кода извлекает предварительно обновленную строку данных, затем удаляет ее из базы данных с помощью метода [deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md).

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class UpdateResultSet {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);) {

            // Create and execute an SQL statement, retrieving an updateable result set.
            String SQL = "SELECT * FROM HumanResources.Department;";
            ResultSet rs = stmt.executeQuery(SQL);

            // Insert a row of data.
            rs.moveToInsertRow();
            rs.updateString("Name", "Accounting");
            rs.updateString("GroupName", "Executive General and Administration");
            rs.updateString("ModifiedDate", "08/01/2006");
            rs.insertRow();

            // Retrieve the inserted row of data and display it.
            SQL = "SELECT * FROM HumanResources.Department WHERE Name = 'Accounting';";
            rs = stmt.executeQuery(SQL);
            displayRow("ADDED ROW", rs);

            // Update the row of data.
            rs.first();
            rs.updateString("GroupName", "Finance");
            rs.updateRow();

            // Retrieve the updated row of data and display it.
            rs = stmt.executeQuery(SQL);
            displayRow("UPDATED ROW", rs);

            // Delete the row of data.
            rs.first();
            rs.deleteRow();
            System.out.println("ROW DELETED");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        while (rs.next()) {
            System.out.println(rs.getString("Name") + " : " + rs.getString("GroupName"));
            System.out.println();
        }
    }
}

```

## <a name="see-also"></a>См. также раздел

[Работа с результирующими наборами](../../../connect/jdbc/code-samples/working-with-result-sets.md)
