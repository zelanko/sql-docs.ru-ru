---
title: Использование соединителя Apache Spark для SQL Server и SQL Azure
titleSuffix: SQL Server big data clusters
description: Сведения о том, как использовать соединитель Apache Spark для SQL Server и SQL Azure для чтения и записи данных в SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning-bdc
ms.openlocfilehash: 454d5fadaa88d645e9d1c2feec2c9d87c2af29c9
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645505"
---
# <a name="use-the-apache-spark-connector-for-sql-server-and-azure-sql"></a>Использование соединителя Apache Spark для SQL Server и SQL Azure

[Соединитель Apache Spark для SQL Server и Azure SQL](https://github.com/microsoft/sql-spark-connector) — это высокопроизводительный соединитель, который позволяет использовать данные о транзакциях в аналитике больших данных и сохранять результаты для ad-hoc-запросов или отчетов. Соединитель позволяет использовать любую базу данных SQL, локальную или облачную, в качестве источника входных данных или приемника выходных данных для заданий Spark. Соединитель использует API-интерфейсы массовой записи SQL Server. Любые параметры массовой записи могут передаваться пользователем в качестве необязательного параметра и передаются соединителем в базовый API. Дополнительные сведения об операциях массовой записи см. в разделе [Использование массового копирования с помощью JDBC Driver]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

Этот соединитель включается по умолчанию в состав кластеры SQL Server больших данных.

Дополнительные сведения о соединителе см. в [репозитории с открытым исходным кодом](https://github.com/microsoft/sql-spark-connector). Примеры см. в [образцах](https://github.com/microsoft/sql-spark-connector/tree/master/samples).

## <a name="write-to-a-new-sql-table"></a>Запись в новую таблицу SQL

>[!CAUTION]
> В режиме `overwrite` соединитель сначала удаляет таблицу, если она уже существует в базе данных по умолчанию. Используйте этот параметр с осторожностью, чтобы избежать непредвиденных потерь данных.
> 
> При использовании режима `overwrite`, если не используется параметр `truncate` при повторном создании таблицы, индексы будут потеряны. Например, таблица columnstore преобразуется в кучу. Если вы хотите сохранить существующее индексирование, задайте для параметра `truncate` значение `true`. Например `.option("truncate",true)`

```python
server_name = "jdbc:sqlserver://{SERVER_ADDR}"
database_name = "database_name"
url = server_name + ";" + "databaseName=" + database_name + ";"

table_name = "table_name"
username = "username"
password = "password123!#" # Please specify password here

try:
  df.write \
    .format("com.microsoft.sqlserver.jdbc.spark") \
    .mode("overwrite") \
    .option("url", url) \
    .option("dbtable", table_name) \
    .option("user", username) \
    .option("password", password) \
    .save()
except ValueError as error :
    print("Connector write failed", error)
```

## <a name="append-to-sql-table"></a>Добавление в таблицу SQL
```python
try:
  df.write \
    .format("com.microsoft.sqlserver.jdbc.spark") \
    .mode("append") \
    .option("url", url) \
    .option("dbtable", table_name) \
    .option("user", username) \
    .option("password", password) \
    .save()
except ValueError as error :
    print("Connector write failed", error)
```

## <a name="specify-the-isolation-level"></a>Указание уровня изоляции

По умолчанию этот соединитель использует уровень изоляции READ_COMMITTED при выполнении массовой вставки в базу данных. Если вы хотите переопределить его на другой уровень изоляции, используйте параметр `mssqlIsolationLevel`, как показано ниже.
```python
    .option("mssqlIsolationLevel", "READ_UNCOMMITTED") \
```

## <a name="read-from-sql-table"></a>Чтение из таблицы SQL

```python
jdbcDF = spark.read \
        .format("com.microsoft.sqlserver.jdbc.spark") \
        .option("url", url) \
        .option("dbtable", table_name) \
        .option("user", username) \
        .option("password", password).load()
```

## <a name="non-active-directory-mode"></a>Режим без Active Directory

В режиме без Active Directory каждый пользователь имеет имя пользователя и пароль, которые необходимо предоставить в качестве параметров во время создания экземпляра соединителя для выполнения операций чтения и записи.

Ниже приведен пример создания экземпляра соединителя для режима без Active Directory. Перед выполнением скрипта замените `?` значением для своей учетной записи.

```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark" 

url = "jdbc:sqlserver://master-p-svc;databaseName=?;"
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("user", ?) \ 
   .option("password",?) 
writer.save() 
```

## <a name="active-directory-mode"></a>Режим Active Directory

В режиме безопасности с Active Directory после того, как пользователь создал файл keytab, он должен указать `principal` и `keytab` в качестве параметров во время создания экземпляра соединителя.

В этом режиме драйвер загружает файл keytab в соответствующие контейнеры исполнителя. Затем исполнители используют имя участника и keytab для создания маркера, который используется для создания соединителя JDBC для чтения и записи.

Ниже приведен пример создания экземпляра соединителя для режима с Active Directory. Перед выполнением скрипта замените `?` значением для своей учетной записи.

```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark"

url = "jdbc:sqlserver://master-p-svc;databaseName=?;integratedSecurity=true;authenticationScheme=JavaKerberos;" 
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("principal", ?) \ 
   .option("keytab", ?)   

writer.save() 
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md).

У вас есть отзывы или рекомендации по функциям для кластеров больших данных SQL Server? [Напишите нам в разделе "Отзывы от кластерах больших данных SQL Server"](https://aka.ms/sql-server-bdc-feedback).
