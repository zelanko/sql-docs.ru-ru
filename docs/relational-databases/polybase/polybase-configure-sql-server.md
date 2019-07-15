---
title: Настройка PolyBase для доступа к внешним данным в SQL Server | Документация Майкрософт
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
ms.reviewer: mikeray
manager: craigg
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: c42ff3c215d3f252a61371ea560c2ecac7c3cf62
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67730339"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Настройка PolyBase для доступа к внешним данным в SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Эта статья описывает, как с помощью PolyBase в экземпляре SQL Server запросить внешние данные другого экземпляра SQL Server.

## <a name="prerequisites"></a>предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md). Необходимые условия описываются в статье, посвященной установке.

[Главный ключ](../../t-sql/statements/create-master-key-transact-sql.md) необходимо создать перед созданием учетных данных для базы данных. 

## <a name="configure-a-sql-server-external-data-source"></a>Настройка внешнего источника данных SQL Server

Чтобы запросить данные из источника данных SQL Server, необходимо создать внешние таблицы, чтобы ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц. 
 
Чтобы обеспечить оптимальную производительность запросов, создайте статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, фильтров и статистических выражений.

В рамках этого раздела используются следующие команды Transact-SQL:

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1.  Создайте учетные данные в области базы данных для доступа к источнику MongoDB.

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source.  
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials   
    WITH IDENTITY = 'username', Secret = 'password';
    ```

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

    ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
    WITH ( LOCATION = 'sqlserver://SqlServer',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = SQLServerCredentials);
    ```

1. **Необязательно**. Создайте статистику внешней таблицы.

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    We recommend creating statistics on external table columns, especially the ones used for joins, filters and aggregates, for optimal query performance.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN;
    ```

>[!IMPORTANT] 
>После создания внешнего источника данных можно использовать команду [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md), чтобы создать таблицу с поддержкой запросов по этому источнику.

## <a name="sql-server-connector-compatible-types"></a>Совместимые типы соединителей SQL Server

Вы можете установить подключение к другим источникам данных, поддерживающим подключение SQL Server. Соединитель SQL Server PolyBase позволяет создать внешнюю таблицу Хранилища данных SQL Azure и Базы данных SQL Azure. Для этого выполните те же действия, что указаны ранее. Учетные данные в области базы, а также адрес сервера, порт и строка расположения должны соответствовать аналогичным параметрам в совместимом источнике данных, к которому нужно подключиться.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
