---
title: Прием данных в пул данных SQL Server
titleSuffix: SQL Server big data clusters
description: В этом руководстве описывается, как выполняется прием данных в пул данных в кластере больших данных SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ed3719a2fa24c7f7306b91cf8d422808d5fcea27
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772893"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>Руководство по Прием данных в пул данных SQL Server с помощью Transact-SQL

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этом учебнике описывается, как использовать Transact-SQL для загрузки данных в [пул данных](concept-data-pool.md)[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. С [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] данные из самых разных источников могут приниматься и распределяться между экземплярами пула данных.

В этом руководстве описано следующее:

> [!div class="checklist"]
> * Создание внешней таблицы в пуле данных.
> * Вставка примера с данными о посещениях веб-страниц в таблицу пула данных.
> * Объединение данных в таблице пула данных с локальными таблицами.

> [!TIP]
> При необходимости вы можете скачать и выполнить скрипт, содержащий команды из этого руководства. См. инструкции в разделе [Примеры пулов данных](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) на сайте GitHub.

## <a name="prerequisites"></a><a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка примера данных в кластер больших данных](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Создание внешней таблицы в пуле данных

Выполните следующие действия, чтобы создать внешнюю таблицу с именем **web_clickstream_clicks_data_pool** в пуле данных. В дальнейшем эта таблица может использоваться для приема данных в кластер больших данных.

1. В Azure Data Studio установите подключение к главному экземпляру SQL Server в кластере больших данных. Дополнительные сведения см. в разделе [Подключение к главному экземпляру SQL Server](connect-to-big-data-cluster.md#master).

1. Дважды щелкните подключение в окне **Серверы**, чтобы открыть панель мониторинга сервера для главного экземпляра SQL Server. Выберите **Создать запрос**.

   ![Запрос главного экземпляра SQL Server](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Выполните следующую команду Transact-SQL, чтобы изменить контекст на базу данных **Sales** в главном экземпляре.

   ```sql
   USE Sales
   GO
   ```

1. Создайте внешний источник данных для пула данных, если это не было сделано ранее.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://controller-svc/default');
   ```

1. Создайте внешнюю таблицу с именем **web_clickstream_clicks_data_pool** в пуле данных.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstream_clicks_data_pool')
      CREATE EXTERNAL TABLE [web_clickstream_clicks_data_pool]
      ("wcs_user_sk" BIGINT , "i_category_id" BIGINT , "clicks" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```

Создание внешней таблицы пула данных является блокирующей операцией. Управление возвращается лишь после создания указанной таблицы на всех узлах пула данных серверной части. Если во время операции создания произойдет ошибка, сообщение о ней возвращается вызывающей стороне.

## <a name="load-data"></a>Загрузка данных

Выполните следующие действия, чтобы принять данные о посещениях веб-страниц в пул данных с использованием внешней таблицы, созданной на предыдущих шагах.

1. Используйте инструкцию `INSERT INTO` для вставки результатов запроса в пул данных (внешняя таблица **web_clickstream_clicks_data_pool**).

   ```sql
   INSERT INTO web_clickstream_clicks_data_pool
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
     FROM sales.dbo.web_clickstreams_hdfs
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
                           AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;
   ```

1. Проверьте вставленные данные с помощью двух запросов SELECT.

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>Запрос данных

Объедините сохраненные результаты запроса в пуле данных с локальными данными в таблице **Sales**.

```sql
SELECT TOP (100)
   w.wcs_user_sk,
   SUM( CASE WHEN i.i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
   SUM( CASE WHEN w.i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
   SUM( CASE WHEN w.i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
   SUM( CASE WHEN w.i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
   SUM( CASE WHEN w.i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
   SUM( CASE WHEN w.i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
   SUM( CASE WHEN w.i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
   SUM( CASE WHEN w.i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
   SUM( CASE WHEN w.i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
   SUM( CASE WHEN w.i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
FROM [dbo].[web_clickstream_clicks_data_pool] as w
INNER JOIN (SELECT DISTINCT i_category_id, i_category FROM item) as i
   ON i.i_category_id = w.i_category_id
GROUP BY w.wcs_user_sk;
```

## <a name="clean-up"></a>Очистка

Выполните следующую команду, чтобы удалить объекты базы данных, созданные в рамках этого руководства.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>Дальнейшие действия

Сведения о приеме данных в пул данных с помощью заданий Spark:
> [!div class="nextstepaction"]
> [Прием данных с помощью заданий Spark](tutorial-data-pool-ingest-spark.md)
