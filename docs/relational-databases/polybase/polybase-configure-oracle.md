---
title: Настройка PolyBase для доступа к внешним данным в Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 04/10/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 4a7484acf7a63b5c2a6804e1f3f7914cabaf8524
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59476649"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Настройка PolyBase для доступа к внешним данным в Oracle

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается использование PolyBase в экземпляре SQL Server для запроса внешних данных в Oracle.

## <a name="prerequisites"></a>предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md).

## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные из источника данных Oracle, необходимо создать внешние таблицы, позволяющие ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц. 
 
В рамках этого раздела используются следующие команды Transact-SQL:

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Создайте в базе данных главный ключ, если его нет. Это необходимо для шифрования секрета учетных данных.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
   ```

   > [!NOTE]
   > `PASSWORD` — это пароль, который использовался при шифровании главного ключа базы данных. Пароль должен соответствовать требованиям политики паролей Windows на компьютере, где размещается экземпляр SQL Server.

1. Создайте учетные данные на уровне базы данных.

   ```sql
   /*  
   * Specify credentials to external data source
   * IDENTITY: user name for external source.  
   * SECRET: password for external source.
   */
   CREATE DATABASE SCOPED CREDENTIAL credential_name
   WITH IDENTITY = 'username', Secret = 'password';
   ```

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Укажите расположение внешнего источника данных и учетные данные для источника данных Oracle.

   ```sql
   /* 
   * LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
   * PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
   * CONNECTION_OPTIONS: Specify driver location
   * CREDENTIAL: the database scoped credential, created above.
   */  
   CREATE EXTERNAL DATA SOURCE external_data_source_name
   WITH ( 
     LOCATION = 'oracle://<server address>[:<port>]',
     -- PUSHDOWN = ON | OFF,
     CREDENTIAL = credential_name)
   ```

1. Создайте внешние таблицы, которые представляют данные, хранящиеся во внешней системе Oracle, с помощью инструкции [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).

   ```sql
   /*
   * LOCATION: Oracle table/view in '<database_name>.<schema_name>.<object_name>' format
   * DATA_SOURCE: the external data source, created above.
   */
   CREATE EXTERNAL TABLE customers(
   [O_ORDERKEY] DECIMAL(38) NOT NULL,
   [O_CUSTKEY] DECIMAL(38) NOT NULL,
   [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
   [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
   [O_ORDERDATE] DATETIME2(0) NOT NULL,
   [O_ORDERPRIORITY] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
   [O_CLERK] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
   [O_SHIPPRIORITY] DECIMAL(38) NOT NULL,
   [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
   )
   WITH (
    LOCATION='customer',
    DATA_SOURCE=  external_data_source_name
   );
   ```

1. **Необязательно**. Создайте статистику для внешней таблицы с помощью приведенной ниже команды.

   ```sql
   CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
   ```

   > [!TIP]
   > Рекомендуем создать статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, фильтров и статистических выражений. Это позволит оптимизировать производительность запросов.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
