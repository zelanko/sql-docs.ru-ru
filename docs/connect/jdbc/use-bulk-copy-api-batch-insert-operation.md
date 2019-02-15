---
title: Используя интерфейс API массового копирования для операции пакетной вставки для драйвера MSSQL JDBC | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: c3d3c7cc4d8dd7beeb620a211b2f41a1d1105a04
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737105"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Использование API массового копирования для операции пакетной вставки

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

7.0 драйвера Microsoft JDBC для SQL Server поддерживает использование интерфейс API массового копирования для операций вставки для хранилища данных Azure. Эта функция позволяет пользователям включить драйвер для выполнения операции массового копирования под при выполнении пакетной операции вставки. Операция вставки целей драйвера для повышения производительности во время вставки и те же данные, как драйвер будет иметь с использованием регулярных пакетной службы. Драйвер выполняет синтаксический анализ SQL-запрос пользователя, используя интерфейс API массового копирования вместо обычного пакетной операции вставки. Ниже приведены различные способы, чтобы включить интерфейс API массового копирования для пакетной вставки компонент, а также список со всеми существующими ограничениями. Эта страница также содержит небольшой пример кода, демонстрирующий использование и повысить производительность также.

Эта функция применима только для PreparedStatement и CallableStatement в `executeBatch()`  &  `executeLargeBatch()` API-интерфейсы.

## <a name="pre-requisites"></a>Предварительные требования

Существует два предварительных требования, чтобы включить интерфейс API массового копирования для вставки пакета.

* Сервер должен быть хранилище данных.
* Запрос должен быть запроса insert (запрос может содержать комментарии, но запроса должно начинаться с ключевым словом INSERT для этой функции вступают в силу).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>Включение интерфейс API массового копирования для вставки пакета

Чтобы включить интерфейс API массового копирования для вставки пакета тремя способами.

### <a name="1-enabling-with-connection-property"></a>1. Включение с помощью свойства соединения

Добавление **useBulkCopyForBatchInsert = true;** соединение строка включает эту функцию.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Включение с помощью метода setUseBulkCopyForBatchInsert() из объекта SQLServerConnection

Вызов **SQLServerConnection.setUseBulkCopyForBatchInsert(true)** включает эту функцию.

**SQLServerConnection.getUseBulkCopyForBatchInsert()** Извлекает текущее значение для **useBulkCopyForBatchInsert** свойство соединения.

Значение для **useBulkCopyForBatchInsert** остается неизменным для каждого PreparedStatement во время инициализации. Все последующие вызовы **SQLServerConnection.setUseBulkCopyForBatchInsert()** не повлияет на уже созданную PreparedStatement по отношению к его значение.

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Включение с помощью метода setUseBulkCopyForBatchInsert() из объекта SQLServerDataSource

Аналогично выше, но с использованием SQLServerDataSource для создания объекта SQLServerConnection. Оба метода дают одинаковый результат.

## <a name="known-limitations"></a>Известные ограничения

Сейчас эти ограничения, связанные с этой функции.

* Запросы, которые содержат непараметризованные значения INSERT (например, `INSERT INTO TABLE VALUES (?, 2`)), не поддерживаются. Подстановочные знаки (?) — только поддерживаемые параметры для этой функции.
* Запросы, содержащие выражения INSERT-SELECT INSERT (например, `INSERT INTO TABLE SELECT * FROM TABLE2`), не поддерживаются.
* Вставить запросы, которые содержат несколько выражений значений (например, `INSERT INTO TABLE VALUES (1, 2) (3, 4)`), не поддерживаются.
* Запросы INSERT, следуют предложение OPTION, объединенных с помощью нескольких таблиц или следуют другой запрос, не поддерживаются.
* Из-за ограничения интерфейс API массового копирования `MONEY`, `SMALLMONEY`, `DATE`, `DATETIME`, `DATETIMEOFFSET`, `SMALLDATETIME`, `TIME`, `GEOMETRY`, и `GEOGRAPHY` типы данных, в настоящее время не поддерживаются для данного функция.

Если запрос завершится с ошибкой из-за без ошибок, связанных с «SQL server», драйвер, регистрируются сообщение об ошибке и резервных точек в исходном логику для вставки пакета.

## <a name="example"></a>Пример

Ниже приведен пример кода, который показан случай использования пакетной вставки операции для хранилища данных Azure тысячи строк, для обоих сценариев (регулярных vs в интерфейс API массового копирования).

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
