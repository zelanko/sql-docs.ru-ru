---
title: Настройка PolyBase для доступа к внешним данным в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d2b4bb2249f0c4a6ec57c037db54c490f3066e2b
ms.sourcegitcommit: 41979c9d511b3eeb45134d30ccb0dbc6bba70f1a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50757949"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Настройка PolyBase для доступа к внешним данным в SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья описывает, как с помощью PolyBase в экземпляре SQL Server запросить внешние данные другого экземпляра SQL Server.

## <a name="prerequisites"></a>предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md). Необходимые условия описываются в статье, посвященной установке.

## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные из источника данных SQL Server, необходимо создать внешние таблицы, чтобы ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц. 
 
Чтобы обеспечить оптимальную производительность запросов, создайте статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, фильтров и статистических выражений.

В этом разделе будут созданы следующие объекты:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Создайте главный ключ в базе данных. Он необходим для шифрования секрета учетных данных.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
     ```

1. Создайте учетные данные на уровне базы данных.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials   
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Укажите расположение внешнего источника данных и учетные данные для SQL Server.

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
    WITH ( 
    LOCATION = sqlserver://SqlServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = SQLServerCredentials
    );

     ```

1. Создайте схемы для внешних данных.

     ```sql
     CREATE SCHEMA sqlserver;
     GO
     ```

1.  Создайте внешние таблицы для представления данных, хранимых во внешнем экземпляре SQL Server, с помощью инструкции [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: sql server table/view in 'database_name.schema_name.object_name' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE sqlserver.customer(
     C_CUSTKEY INT NOT NULL,
     C_NAME VARCHAR(25) NOT NULL,
     C_ADDRESS VARCHAR(40) NOT NULL,
     C_NATIONKEY INT NOT NULL,
     C_PHONE CHAR(15) NOT NULL,
     C_ACCTBAL DECIMAL(15,2) NOT NULL,
     C_MKTSEGMENT CHAR(10) NOT NULL,
     C_COMMENT VARCHAR(117) NOT NULL
      )
      WITH (
      LOCATION='tpch_10.dbo.customer',
      DATA_SOURCE=SqlServerInstance
     );
      ```

1. Создайте статистику внешней таблицы.

     ```sql
      CREATE STATISTICS CustomerCustKeyStatistics ON sqlserver.customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="sql-server-connector-compatible-types"></a>Совместимые типы соединителей SQL Server

Вы можете установить подключение к другим источникам данных, поддерживающим подключение SQL Server. Соединитель SQL Server PolyBase позволяет создать внешнюю таблицу Хранилища данных SQL Azure и Базы данных SQL Azure. Для этого выполните те же действия, что указаны ранее. Учетные данные в области базы, а также адрес сервера, порт и строка расположения должны соответствовать аналогичным параметрам в совместимом источнике данных, к которому нужно подключиться.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
