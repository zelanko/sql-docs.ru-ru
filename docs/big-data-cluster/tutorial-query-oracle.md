---
title: Запрос внешних данных в Oracle
titleSuffix: SQL Server big data clusters
description: В этом учебнике описывается, как выполняется запрос данных Oracle из кластера больших данных SQL Server 2019. Для этого создается внешняя таблица на основе данных в Oracle, после чего выполняется запрос.
author: MikeRayMSFT
ms.author: dacoelho
ms.reviewer: mikeray
ms.date: 10/01/2020
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 48d7fb0f41446fa54f1376a9a84f7dbff7017960
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196089"
---
# <a name="tutorial-query-oracle-from-sql-server-big-data-cluster"></a>Руководство по созданию запроса Oracle из Кластера больших данных SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этом руководстве описывается, каким образом выполняется запрос данных Oracle из кластера больших данных SQL Server 2019. Для работы с этим руководством требуется доступ к серверу Oracle. Требуется учетная запись пользователя Oracle с правами на чтение для внешнего объекта. Поддерживается проверка подлинности пользователя через прокси-сервер Oracle. Если у вас нет доступа к серверу, из этого руководства вы можете узнать о принципах виртуализации данных для внешних источников в кластере больших данных SQL Server.

В этом руководстве описано следующее:

> [!div class="checklist"]
> * Создание внешней таблицы для данных во внешней базе данных Oracle.
> * Объединение этих данных с важными данными в главном экземпляре.

> [!TIP]
> При необходимости вы можете скачать и выполнить скрипт, содержащий команды из этого руководства. См. инструкции в разделе [Примеры виртуализации данных](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) на сайте GitHub.

## <a name="prerequisites"></a><a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка примера данных в кластер больших данных](tutorial-load-sample-data.md)

## <a name="create-an-oracle-table"></a>Создание таблицы Oracle

Далее описывается создание примера таблицы с именем `INVENTORY` в Oracle.

1. Подключитесь к базе данных и экземпляру Oracle, которые вы хотите использовать для этого руководства.

1. Чтобы создать эту таблицу `INVENTORY`, используйте следующую инструкцию:

   ```sql
    CREATE TABLE "INVENTORY"
    (
        "INV_DATE" NUMBER(10,0) NOT NULL,
        "INV_ITEM" NUMBER(10,0) NOT NULL,
        "INV_WAREHOUSE" NUMBER(10,0) NOT NULL,
        "INV_QUANTITY_ON_HAND" NUMBER(10,0)
    );

    CREATE INDEX INV_ITEM ON HR.INVENTORY(INV_ITEM);
    ```

1. Импортируйте содержимое файла **inventory.csv** в эту таблицу. Этот файл был создан с помощью примеров скриптов создания в разделе [Предварительные требования](#prereqs).

## <a name="create-an-external-data-source"></a>Создание внешнего источника данных

Для начала необходимо создать внешний источник данных, который может обращаться к вашему серверу Oracle.

1. В Azure Data Studio установите подключение к главному экземпляру SQL Server в кластере больших данных. Дополнительные сведения см. в разделе [Подключение к главному экземпляру SQL Server](connect-to-big-data-cluster.md#master).

1. Дважды щелкните подключение в окне **Серверы** , чтобы открыть панель мониторинга сервера для главного экземпляра SQL Server. Выберите **Создать запрос** .

   ![Запрос главного экземпляра SQL Server](./media/tutorial-query-oracle/sql-server-master-instance-query.png)

1. Выполните следующую команду Transact-SQL, чтобы изменить контекст на базу данных **Sales** в главном экземпляре.

   ```sql
   USE Sales
   GO
   ```

1. Создайте учетные данные в области базы данных для подключения к серверу Oracle. Предоставьте соответствующие учетные данные серверу Oracle в следующей инструкции.

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleCredential]
   WITH IDENTITY = '<oracle_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_user_password,nvarchar(100),manager>';
   ```

1. Создайте внешний источник данных, который указывает на сервер Oracle.

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',CREDENTIAL = [OracleCredential]);
   ```

### <a name="optional-oracle-proxy-authentication"></a>Необязательно. Проверка подлинности прокси-сервера Oracle

Oracle поддерживает проверку подлинности прокси-сервера для обеспечения точной детализации управления доступом. Пользователь прокси-сервера подключается к базе данных Oracle, используя ее учетные данные, и олицетворяет другого пользователя в базе данных. 

Пользователя прокси-сервера можно настроить таким образом, чтобы он имел ограниченный доступ по сравнению с олицетворением пользователя. Например, пользователю прокси-сервера можно разрешить подключаться с помощью определенной роли базы данных олицетворенного пользователя. Удостоверение пользователя, подключающегося к базе данных Oracle через прокси-сервер, сохраняется в соединении, даже если с помощью проверки подлинности прокси-сервера подключаются несколько пользователей. Это позволяет Oracle принудительно применять управление доступом и выполнять аудит действий, выполняемых от имени фактического пользователя.

Если в сценарии требуется использование пользователя прокси-сервера Oracle, __вместо шагов 4 и 5 сделайте следующие__ .

4. Создайте учетные данные в области базы данных для подключения к серверу Oracle. Предоставьте соответствующие учетные данные пользователя прокси-сервера Oracle для сервера Oracle в следующей инструкции.

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleProxyCredential]
   WITH IDENTITY = '<oracle_proxy_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_proxy_user_password,nvarchar(100),manager>';
   ```

5. Создайте внешний источник данных, который указывает на сервер Oracle.

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',
   CONNECTION_OPTIONS = 'ImpersonateUser=% CURRENT_USER',
   CREDENTIAL = [OracleProxyCredential]);
   ```

## <a name="create-an-external-table"></a>Создание внешней таблицы

Далее создайте внешнюю таблицу с именем **iventory_ora** на основе таблицы `INVENTORY` на сервере Oracle.

```sql
CREATE EXTERNAL TABLE [inventory_ora]
    ([inv_date] DECIMAL(10,0) NOT NULL, [inv_item] DECIMAL(10,0) NOT NULL,
    [inv_warehouse] DECIMAL(10,0) NOT NULL, [inv_quantity_on_hand] DECIMAL(10,0))
WITH (DATA_SOURCE=[OracleSalesSrvr],
        LOCATION='<oracle_service_name,nvarchar(30),xe>.<oracle_schema,nvarchar(128),HR>.<oracle_table,nvarchar(128),INVENTORY>');
```

> [!NOTE]
> При выполнении запросов к Oracle в именах таблиц и столбцов будет использоваться идентификатор SQL ANSI в кавычках. В связи с этим в таких именах учитывается регистр букв. В определении внешней таблицы важно указывать имена, которые в точности соответствуют именам таблиц и столбцов в метаданных Oracle.

## <a name="query-the-data"></a>Запрос данных

Выполните следующий запрос, чтобы объединить данные во внешней таблице `iventory_ora` с таблицами в локальной базе данных `Sales`.

```sql
SELECT TOP(100) w.w_warehouse_name, i.inv_item, SUM(i.inv_quantity_on_hand) as total_quantity
  FROM [inventory_ora] as i
  JOIN item as it
    ON it.i_item_sk = i.inv_item
  JOIN warehouse as w
    ON w.w_warehouse_sk = i.inv_warehouse
 WHERE it.i_category = 'Books' and i.inv_item BETWEEN 1 and 18000 --> get items within specific range
 GROUP BY w.w_warehouse_name, i.inv_item;
```

## <a name="clean-up"></a>Очистка

Выполните следующую команду, чтобы удалить объекты базы данных, созданные в рамках этого руководства.

```sql
DROP EXTERNAL TABLE [inventory_ora];
DROP EXTERNAL DATA SOURCE [OracleSalesSrvr] ;
DROP DATABASE SCOPED CREDENTIAL [OracleCredential];
```

## <a name="next-steps"></a>Дальнейшие действия

Сведения о приеме данных в пул данных:
> [!div class="nextstepaction"]
> [Загрузка данных в пул данных](tutorial-data-pool-ingest-sql.md)
