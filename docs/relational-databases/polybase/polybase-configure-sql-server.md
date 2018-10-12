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
ms.openlocfilehash: 4729d78f0cfecf80f65dbff0f7bc2d6abe2ebbfa
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874262"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Настройка PolyBase для доступа к внешним данным в SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описано, как с помощью PolyBase в экземпляре SQL Server запросить внешние данные с другого экземпляра SQL Server.

## <a name="prerequisites"></a>предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md). Необходимые условия описываются в статье, посвященной установке.

## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные из источника данных SQL Server, необходимо создать внешние таблицы, чтобы ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц. 
 
Чтобы обеспечить оптимальную производительность запросов, мы советуем создать статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, применения фильтров и статистических выражений.

В этом разделе будут созданы такие объекты:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)

1. Создайте главный ключ в базе данных. Это необходимо для шифрования секрета учетных данных.

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
     ```

1. Создайте учетные данные уровня базы данных.

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials   
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. Создайте внешний источник данных с помощью команды [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Укажите расположение внешнего источника данных и учетные данные для SQL Server.

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
    WITH ( 
    LOCATION = sqlserver://SqlServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = TeradataCredentials
    );

     ```

1. Создайте схемы для внешних данных.

     ```sql
     CREATE SCHEMA sqlserver;
     GO
     ```

1.  Создайте внешние таблицы, которые представляют данные, хранящиеся во внешней системе SQL Server, с помощью инструкции [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
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

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
