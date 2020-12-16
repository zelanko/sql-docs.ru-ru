---
title: 'Доступ к внешним данным: универсальные типы ODBC — PolyBase'
description: PolyBase в SQL Server позволяет подключаться к совместимым источникам данных через соединитель ODBC. Установите драйвер ODBC и создайте внешние таблицы.
ms.date: 07/16/2020
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15'
ms.openlocfilehash: ac4fa22e2d0aea57f25aaa9ef2d8c570f8bb130b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475935"
---
# <a name="configure-polybase-to-access-external-data-with-odbc-generic-types"></a>Настройка доступа к внешним данным в PolyBase с помощью универсальных типов ODBC

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

PolyBase в SQL Server 2019 позволяет подключаться к источникам данных, совместимым с ODBC, с помощью соединителя ODBC.

В этой статье содержатся сведения о том, как создать конфигурацию подключения с помощью источника данных ODBC. В качестве примера в руководстве используется один конкретный драйвер ODBC. Для получения конкретных примеров обратитесь к поставщику ODBC. Чтобы определить подходящие параметры строки подключения, обратитесь к документации по драйверу ODBC для источника данных. Примеры, приведенные в этой статье, могут не применяться к конкретному драйверу ODBC.

## <a name="prerequisites"></a>Предварительные требования

>[!NOTE]
>Для использования этой функции требуется SQL Server в Windows.

* PolyВase нужно установить и включить для [установки PolyВase](polybase-installation.md) для экземпляра SQL Server.

* [Главный ключ](../../t-sql/statements/create-master-key-transact-sql.md) необходимо создать перед созданием учетных данных для базы данных.

## <a name="install-the-odbc-driver"></a>Установка драйвера ODBC

Скачайте и установите драйвер ODBC источника данных, к которому нужно подключиться, на каждом узле PolyBase. После установки драйвера вы можете просмотреть и протестировать его в разделе **Администратор источников данных ODBC**.

![Масштабируемые группы PolyBase](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

В приведенном выше примере имя драйвера обведено красным кружком. Используйте это имя при создании внешнего источника данных.

> [!IMPORTANT]
> Чтобы повысить производительность запросов, включите пулы соединений. Это можно сделать в разделе **Администратор источников данных ODBC**.

## <a name="create-dependent-objects-in-sql-server"></a>Создание зависимых объектов в SQL Server

Чтобы использовать источник данных ODBC, сначала необходимо создать несколько объектов для завершения настройки.

В рамках этого раздела используются следующие команды Transact-SQL:

* [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
* [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 

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
    WITH ( LOCATION = 'odbc://<ODBC server address>[:<port>]',
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
    WITH ( LOCATION = 'odbc://SERVERNAME:4444',
    CONNECTION_OPTIONS = 'Driver={CData ODBC Driver For SAP 2015};
    ServerNode = sap_server_node:5555',
    PUSHDOWN = ON,
    CREDENTIAL = credential_name );
    ```
    
## <a name="create-an-external-table"></a>Создание внешней таблицы

После того как вы создали зависимые объекты, можно создать внешние таблицы с помощью T-SQL. 

В рамках этого раздела используются следующие команды Transact-SQL:
* [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md)
* [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. Создайте одну или несколько внешних таблиц.

   Создайте внешнюю таблицу. Вам нужно обратиться ко внешнему источнику данных, созданному выше с помощью аргумента `DATA_SOURCE`, и указать исходную таблицу в качестве `LOCATION`. Ссылаться на все столбцы не нужно, однако стоит убедиться, что типы сопоставлены должным образом.  

   ```sql
     CREATE EXTERNAL TABLE <your_table_name>
     (
     <col1_name>     DECIMAL(38) NOT NULL,
     <col2_name>     DECIMAL(38) NOT NULL,
     <col3_name>     CHAR COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
     LOCATION='<sap_table_name>',
     DATA_SOURCE= <external_data_source_name>
     )
     ;
   ```

   > [!NOTE]
   > Обратите внимание, что с помощью внешнего источника данных можно повторно использовать зависимые объекты для всех внешних таблиц.

1. **Необязательно**. Создайте статистику внешней таблицы.

    Чтобы обеспечить оптимальную производительность запросов, мы советуем создать статистику столбцов внешней таблицы, особенно тех, которые используются для объединения, применения фильтров и статистических выражений.

    ```sql
    CREATE STATISTICS statistics_name ON contact (FirstName) WITH FULLSCAN; 
    ```
    
## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о PolyBase см. в статье [Руководство по PolyBase](polybase-guide.md).
