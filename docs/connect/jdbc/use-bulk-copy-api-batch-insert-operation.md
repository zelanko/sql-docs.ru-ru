---
title: Использование API массового копирования для операции пакетной вставки в MSSQL JDBC Driver | Документация Майкрософт
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
ms.openlocfilehash: 3050cdf87775a67618902dfbb88b656003020769
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027098"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>Использование API массового копирования для операции пакетной вставки

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft JDBC Driver версии 7.0 для SQL Server поддерживает использование API-интерфейса массового копирования для пакетных операций вставки в Хранилище данных Azure. Эта функция позволяет активировать в драйвере выполнение операции массового копирования при выполнении операций пакетной вставки. Драйвер позволяет повысить производительность вставки аналогичного объема данных по сравнению с обычной операцией пакетной вставки. Драйвер анализирует SQL-запрос пользователя, используя API-интерфейс массового копирования вместо обычной операции пакетной вставки. Ниже приведены различные способы включения API-интерфейса массового копирования, а также список ограничений. На этой странице также содержится небольшой пример кода, демонстрирующий использование и увеличение производительности.

Эта функция применима только к API-интерфейсам `executeBatch()` & `executeLargeBatch()` объектов PreparedStatement и CallableStatement.

## <a name="prerequisites"></a>Предварительные требования

Существует два предварительных требования для включения API-интерфейса для пакетной вставки.

* Сервер должен быть Хранилищем данных Azure.
* Требуется запрос INSERT (запрос может содержать комментарии, но должен начинаться с ключевого слова INSERT, чтобы эта функция действовала).

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>Включение API массового копирования для операции пакетной вставки

Существует три способа включения API-интерфейса массового копирования для пакетной вставки.

### <a name="1-enabling-with-connection-property"></a>1. Включение с помощью свойства подключения

Эту функцию можно включить, добавив параметр **useBulkCopyForBatchInsert=true;** в строку подключения.

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2. Включение с помощью метода setUseBulkCopyForBatchInsert() из объекта SQLServerConnection

Эту функцию можно включить с помощью вызова **SQLServerConnection.setUseBulkCopyForBatchInsert(true)** .

Вызов **SQLServerConnection.getUseBulkCopyForBatchInsert()** извлекает текущее значение свойства подключения **useBulkCopyForBatchInsert**.

Значение параметра **useBulkCopyForBatchInsert** остается постоянным для каждой инструкции PreparedStatement во время инициализации. Последующие вызовы **SQLServerConnection.setUseBulkCopyForBatchInsert()** не влияют на уже созданную инструкцию PreparedStatement в отношении ее значения.

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3. Включение с помощью метода setUseBulkCopyForBatchInsert() из объекта SQLServerDataSource

Выполняется аналогично приведенному выше, но объект SQLServerConnection создается с помощью класса SQLServerDataSource. Оба метода дают одинаковый результат.

## <a name="known-limitations"></a>Известные ограничения

В настоящее время к этой функции применяются следующие ограничения.

* Запросы вставки, содержащие непараметризованные значения (например, `INSERT INTO TABLE VALUES (?, 2`), не поддерживаются. Подстановочные знаки (?) — единственные поддерживаемые параметры для этой функции.
* Запросы вставки, содержащие выражения INSERT-SELECT (например, `INSERT INTO TABLE SELECT * FROM TABLE2`), не поддерживаются.
* Запросы вставки, содержащие несколько выражений VALUE (например, `INSERT INTO TABLE VALUES (1, 2) (3, 4)`), не поддерживаются.
* Запросы вставки, за которыми следует предложение OPTION, объединенное с несколькими таблицами, или за которыми следует другой запрос, не поддерживаются.
* Из-за ограничений, связанных с API для массового копирования, типы данных `MONEY`, `SMALLMONEY`, `DATE`, `DATETIME`, `DATETIMEOFFSET`, `SMALLDATETIME`, `TIME`, `GEOMETRY` и `GEOGRAPHY` в настоящее время не поддерживаются для этой функции.

Если запрос не выполняется из-за ошибок, не связанных с SQL Server, драйвер регистрирует сообщение об ошибке и возвращает исходную логику для пакетной вставки.

## <a name="example"></a>Пример

Ниже приведен пример кода, демонстрирующий вариант использования операции пакетной вставки в Хранилище данных Azure с тысячами строк для обоих сценариев (обычная вставка и API массового копирования).

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

## <a name="see-also"></a>См. также раздел

[Повышение производительности и надежности с помощью JDBC Driver](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
