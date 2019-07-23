---
title: Использование API-интерфейса копирования для операции пакетной вставки для драйвера MSSQL JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 028caf1bf69c7e361ea7e4445c192c1fc1adf437
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004135"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Использование API массового копирования для операции пакетной вставки

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер Microsoft JDBC Driver 7,0 для SQL Server поддерживает использование API-интерфейса копирования для пакетных операций вставки в хранилище данных Azure. Эта функция позволяет пользователям включить драйвер для выполнения операции копирования после выполнения операций пакетной вставки. Драйвер предназначен для повышения производительности при вставке тех же данных, что и драйвер, с обычной операцией пакетной вставки. Драйвер анализирует SQL-запрос пользователя, используя API-интерфейс полного копирования вместо обычной операции пакетной вставки. Ниже приведены различные способы включения API-интерфейса для пакетной вставки, а также список ограничений. На этой странице также содержится небольшой пример кода, демонстрирующий использование и увеличение производительности.

Эта функция применима только к `executeBatch()` `executeLargeBatch()` API-интерфейсам PreparedStatement и CallableStatement  &  .

## <a name="pre-requisites"></a>Предварительные требования

Существует два предварительных требования для включения API-интерфейса для пакетной вставки.

* Сервер должен быть хранилищем данных Azure.
* Запрос должен быть запросом INSERT (запрос может содержать комментарии, но запрос должен начинаться с ключевого слова INSERT, чтобы эта функция действовала).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>Включение API-интерфейса небольшого копирования для пакетной вставки

Существует три способа включения API-интерфейса копирования для пакетной вставки.

### <a name="1-enabling-with-connection-property"></a>1. Включение со свойством соединения

Добавление **усебулккопифорбатчинсерт = true;** в строку подключения включает эту функцию.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Включение с помощью метода Сетусебулккопифорбатчинсерт () из объекта SQLServerConnection

Вызов **SQLServerConnection. сетусебулккопифорбатчинсерт (true)** включает эту функцию.

**SQLServerConnection. жетусебулккопифорбатчинсерт ()** извлекает текущее значение для свойства соединения **усебулккопифорбатчинсерт** .

Значение для **усебулккопифорбатчинсерт** остается постоянным для каждого PreparedStatement во время его инициализации. Последующие вызовы **SQLServerConnection. сетусебулккопифорбатчинсерт ()** не влияют на уже созданный PreparedStatement в отношении его значения.

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Включение с помощью метода Сетусебулккопифорбатчинсерт () из объекта SQLServerDataSource

Аналогично приведенному выше, но с помощью SQLServerDataSource для создания объекта SQLServerConnection. Оба метода дают одинаковый результат.

## <a name="known-limitations"></a>Известные ограничения

В настоящее время существуют ограничения, применимые к этой функции.

* Запросы INSERT, содержащие непараметризованные значения (например, `INSERT INTO TABLE VALUES (?, 2`)), не поддерживаются. Подстановочные знаки (?) — единственные поддерживаемые параметры для этой функции.
* Запросы INSERT, содержащие выражения INSERT-SELECT (например, `INSERT INTO TABLE SELECT * FROM TABLE2`), не поддерживаются.
* Запросы INSERT, содержащие несколько выражений значений (например, `INSERT INTO TABLE VALUES (1, 2) (3, 4)`), не поддерживаются.
* Запросы INSERT, за которыми следует предложение OPTION, Соединенное с несколькими таблицами или за которыми следует другой запрос, не поддерживаются.
* Из-за ограничений, связанных с массовым `MONEY`копированием `DATE`, `DATETIME` `SMALLDATETIME` `DATETIMEOFFSET` `SMALLMONEY` `TIME`,,,,,, `GEOGRAPHY` , и типами данных в настоящее время не поддерживаются для этого `GEOMETRY` функциями.

Если запрос завершается неудачей из-за ошибок, связанных с ошибками SQL Server, драйвер регистрирует сообщение об ошибке и откат к исходной логике для пакетной вставки.

## <a name="example"></a>Пример

Ниже приведен пример кода, демонстрирующий вариант использования для операции пакетной вставки в хранилище данных Azure в тысячах строк, как для сценариев (регулярных, так и для групповых API).

```java
    public static void main(String[] args) throws Exception
    {
        String tableName = "batchTest";
        String tableNameBulkCopyAPI = "batchTestBulk";

        String azureDWconnectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl); // connects to an Azure Data Warehouse.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableName + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableName + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableName + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableName + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using regular batch insert operation.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl + ";useBulkCopyForBatchInsert=true"); // connects to an Azure Data Warehouse, with useBulkCopyForBatchInsert connection property set to true.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableNameBulkCopyAPI + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableNameBulkCopyAPI + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableNameBulkCopyAPI + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableNameBulkCopyAPI + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using Bulk Copy API.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }
    }
```

Результат:

```bash
Starting batch operation using regular batch insert operation.
Finished. Time taken : 104132 milliseconds.
Starting batch operation using Bulk Copy API.
Finished. Time taken : 1058 milliseconds.
```

## <a name="see-also"></a>См. также:

[Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
