---
title: 'Доступ к внешним данным: универсальные типы ODBC — PolyBase'
description: PolyBase в SQL Server позволяет подключаться к совместимым источникам данных через соединитель ODBC. Установите драйвер ODBC и создайте внешние таблицы.
ms.date: 02/19/2020
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: de3d0489acfca3363824b45ce87ba7ac4b63bf7a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80215842"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>Настройка PolyBase для доступа к внешним данным в SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

PolyBase в SQL Server 2019 позволяет подключаться к совместимым источникам данных ODBC через соединитель ODBC.

В этой статье приводятся некоторые примеры использования драйвера ODBC. Для получения конкретных примеров обратитесь к поставщику ODBC. Чтобы определить подходящие параметры строки подключения, обратитесь к документации по драйверу ODBC для источника данных. Примеры, приведенные в этой статье, могут не применяться к конкретному драйверу ODBC.

## <a name="prerequisites"></a>Предварительные требования

>[!NOTE]
>Для использования этой функции требуется SQL Server в Windows.

* [Установка PolyBase](polybase-installation.md).

* [Главный ключ](../../t-sql/statements/create-master-key-transact-sql.md) необходимо создать перед созданием учетных данных для базы данных.

## <a name="install-the-odbc-driver"></a>Установка драйвера ODBC

Сначала скачайте и установите на всех узлах PolyBase драйвер ODBC источника данных, к которому нужно подключиться. После установки драйвера вы можете просмотреть и протестировать его в разделе **Администратор источников данных ODBC**.

![Масштабируемые группы PolyBase](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

В приведенном выше примере имя драйвера обведено красным кружком. Используйте это имя при создании внешнего источника данных.

> [!IMPORTANT]
> Чтобы повысить производительность запросов, включите пулы соединений. Это можно сделать в разделе **Администратор источников данных ODBC**.

## <a name="create-an-external-table"></a>Создание внешней таблицы

Чтобы запросить данные из источника ODBC, нужно создать внешние таблицы, позволяющие ссылаться на внешние данные. Этот раздел содержит пример кода для создания внешних таблиц.

В рамках этого раздела используются следующие команды Transact-SQL:

* [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
* [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
* [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Создайте учетные данные в области базы данных для доступа к источнику ODBC.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL <credential_name> WITH IDENTITY = '<username>', Secret = '<password>';
    ```

    Например, в следующем примере создаются учетные данные с именем `credential_name`с удостоверением `username` и сложным паролем.

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'BycA4ZjrE#*2W%!';
    ```

1. Создайте внешний источник данных с помощью инструкции [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).

    ```sql
    CREATE EXTERNAL DATA SOURCE <external_data_source_name>
    WITH ( LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'Driver={<Name of Installed Driver>};
    ServerNode = <name of server  address>:<Port>',
    -- PUSHDOWN = [ON] | OFF,
    CREDENTIAL = <credential_name> );
    ```

    В следующем примере создается внешний источник данных:
    * С именем `external_data_source_name`
    * Размещенный ODBC `SERVERNAME` с номером порта `4444`
    * Подключение с помощью `CData ODBC Driver For SAP 2015` — это драйвер, созданный в разделе [Установка драйвера ODBC](#install-the-odbc-driver)
    * На `ServerNode` `sap_server_node` с номером порта `5555`
    * Настроен для обработки данных, отправляемых на сервер (`PUSHDOWN = ON`)
    * С использованием учетных данных `credential_name`

    ```sql
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = odbc://SERVERNAME:4444,
    CONNECTION_OPTIONS = 'Driver={CData ODBC Driver For SAP 2015};
    ServerNode = sap_server_node:5555',
    PUSHDOWN = ON,
    CREDENTIAL = credential_name );
    ```

1. **Необязательно**. Создайте статистику внешней таблицы.

    Чтобы обеспечить оптимальную производительность запросов, мы советуем создать статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, применения фильтров и статистических выражений.

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT]
>После создания внешнего источника данных можно использовать команду [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md), чтобы создать таблицу с поддержкой запросов к этому источнику.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
