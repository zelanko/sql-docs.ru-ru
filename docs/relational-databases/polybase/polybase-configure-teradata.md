---
title: Настройка PolyBase для доступа к внешним данным в Teradata | Документация Майкрософт
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
ms.openlocfilehash: 4038f6ee6be90e3c6cf11a3b7c70ec9576e6ee8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818862"
---
# <a name="configure-polybase-to-access-external-data-in-teradata"></a>Настройка PolyBase для доступа к внешним данным в Teradata

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается использование PolyBase в экземпляре SQL Server для запроса внешних данных в Teradata.

## <a name="prerequisites"></a>предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md). Необходимые условия описываются в статье, посвященной установке.

Для использования Polybase в Teradata требуется распространяемый компонент VC++. 
 
## <a name="configure-an-external-table"></a>Настройка внешней таблицы

Чтобы запросить данные из источника данных Teradata, необходимо создать внешние таблицы, позволяющие ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц. 
 
Рекомендуется создавать статистику для столбцов внешней таблицы, особенно для тех, которые используются для объединения, применения фильтров и статистических вычислений, чтобы обеспечить оптимальную производительность запросов.

В этом разделе будут созданы такие объекты:

- CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) 
- CREATE EXTERNAL DATA SOURCE (Transact-SQL) 
- CREATE EXTERNAL FILE FORMAT (Transact-SQL) 
- CREATE EXTERNAL TABLE (Transact-SQL) 
- CREATE STATISTICS (Transact-SQL)


1. Создайте главный ключ в базе данных. Это необходимо для шифрования секрета учетных данных.

     ```sql
     CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
     ```

1. Создайте учетные данные на уровне базы данных.
 
     ```sql
     /*  specify credentials to external data source
      *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL TeradataCredentials 
     WITH IDENTITY = 'username', Secret = 'password'
     ```

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). Укажите расположение внешнего источника данных и учетные данные для Teradata.

     ```sql
      /*  LOCATION: Server DNS name or IP address.
     *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
     *  CREDENTIAL: the database scoped credential, created above.
     */  
     CREATE EXTERNAL DATA SOURCE TeradataInstance
     WITH ( 
     LOCATION = '<vendor>://<server>[:<port>]',
     -- PUSHDOWN = ON | OFF,
       CREDENTIAL = TeradataCredentials
     );
     ```

1. Создайте схемы для внешних данных.

     ```sql
     CREATE SCHEMA teradata;
     GO
     ```

1.  Создайте внешние таблицы, которые представляют данные, хранящиеся во внешней системе Teradata: [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
 
     ```sql
     /*  LOCATION: Teradata table/view in '<database_name>.<object_name>' format
      *  DATA_SOURCE: the external data source, created above.
      */
     CREATE EXTERNAL TABLE teradata.lineitem(
      L_ORDERKEY INT NOT NULL,
      L_PARTKEY INT NOT NULL,
     L_SUPPKEY INT NOT NULL,
     L_LINENUMBER INT NOT NULL,
     L_QUANTITY DECIMAL(15,2) NOT NULL,
     L_EXTENDEDPRICE DECIMAL(15,2) NOT NULL,
     L_DISCOUNT DECIMAL(15,2) NOT NULL,
     L_TAX DECIMAL(15,2) NOT NULL,
     L_RETURNFLAG CHAR NOT NULL,
     L_LINESTATUS CHAR NOT NULL,
     L_SHIPDATE DATE NOT NULL,
     L_COMMITDATE DATE NOT NULL,
     L_RECEIPTDATE DATE NOT NULL,
     L_SHIPINSTRUCT CHAR(25) NOT NULL,
     L_SHIPMODE CHAR(10) NOT NULL,
     L_COMMENT VARCHAR(44) NOT NULL
     )
     WITH (
     LOCATION='tpch.lineitem',
     DATA_SOURCE=TeradataInstance
     );
     ```

1. Создайте статистику по внешней таблице для оптимизации производительности.

     ```sql
      CREATE STATISTICS LineitemOrderKeyStatistics ON teradata.lineitem(L_ORDERKEY) WITH FULLSCAN; 
      ```



## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
