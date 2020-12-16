---
title: 'Доступ к внешним данным: SQL Server — PolyBase'
description: Узнайте, как с помощью PolyBase в экземпляре SQL Server запросить внешние данные с другого экземпляра SQL Server. Создание внешних таблиц для ссылки на внешние данные.
ms.date: 10/06/2020
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15'
ms.openlocfilehash: b03aa87cd92bd1aadbbb96a4019c76f3062dfb99
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469135"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Настройка PolyBase для доступа к внешним данным в SQL Server

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Эта статья описывает, как с помощью PolyBase в экземпляре SQL Server запросить внешние данные другого экземпляра SQL Server.

## <a name="prerequisites"></a>Предварительные требования

Если вы не установили PolyBase, см. раздел [Установка PolyBase](polybase-installation.md). Необходимые условия описываются в статье, посвященной установке. По завершении установки необходимо также [включить PolyBase](polybase-installation.md#enable).

Внешний источник данных SQL Server использует проверку подлинности SQL.

[Главный ключ](../../t-sql/statements/create-master-key-transact-sql.md) необходимо создать перед созданием учетных данных для базы данных. 

## <a name="configure-a-sql-server-external-data-source"></a>Настройка внешнего источника данных SQL Server

Чтобы запросить данные из источника данных SQL Server, необходимо создать внешние таблицы, чтобы ссылаться на внешние данные. Этот раздел содержит пример кода для создания таких внешних таблиц.
 
Чтобы обеспечить оптимальную производительность запросов, создайте статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, фильтров и статистических выражений.

В рамках этого раздела используются следующие команды Transact-SQL:

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Создайте учетные данные в области базы данных для доступа к источнику SQL Server. В следующем примере создаются учетные данные для внешнего источника данных с `IDENTITY = 'username'` и `SECRET = 'password'`.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials
    WITH IDENTITY = 'username', SECRET = 'password';
    ```
   >[!IMPORTANT]
   >Соединитель ODBC SQL для PolyBase поддерживает только обычную проверку подлинности, но не проверку подлинности Kerberos.

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md). В следующем примере происходит следующее:

   - Создает внешний источник данных `SQLServerInstance`.
   - Определяет внешний источник данных (`LOCATION = '<vendor>://<server>[:<port>]'`). В примере он указывает на экземпляр SQL Server по умолчанию.
   - Определяет, следует ли передавать вычисления на источник (`PUSHDOWN`). `PUSHDOWN` по умолчанию равен `ON`.

   Наконец, в примере используются учетные данные, созданные ранее.

    ```sql
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
        WITH ( LOCATION = 'sqlserver://SqlServer',
        PUSHDOWN = ON,
        CREDENTIAL = SQLServerCredentials);
    ```

1. (Необязательно) Создайте статистику для внешней таблицы.

  Чтобы обеспечить оптимальную производительность запросов, создайте статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, фильтров и статистических выражений.

  ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY)
    WITH FULLSCAN;
  ```

>[!IMPORTANT]
>После создания внешнего источника данных можно использовать команду [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md), чтобы создать таблицу с поддержкой запросов по этому источнику.

## <a name="sql-server-connector-compatible-types"></a>Совместимые типы соединителей SQL Server

Вы можете установить подключение к другим источникам данных, поддерживающим подключение SQL Server. Соединитель SQL Server PolyBase позволяет создать внешнюю таблицу Azure Synapse Analytics и Базы данных SQL Azure. Для этого выполните те же действия, что указаны ранее. Учетные данные в области базы, а также адрес сервера, порт и строка расположения должны соответствовать аналогичным параметрам в совместимом источнике данных, к которому нужно подключиться.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
