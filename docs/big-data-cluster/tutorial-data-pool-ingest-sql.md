---
title: Прием данных в пул данных SQL Server
titleSuffix: SQL Server 2019 big data clusters
description: Этом руководстве показано, как прием данных в пуле данных кластера SQL Server 2019 больших данных (Предварительная версия) с sp_data_pool_table_insert_data хранимой процедуры.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 086db0838eb02b0e83ffbb2f00b92d39e1e4d202
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017672"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>Учебник. Прием данных в пул данных SQL Server с помощью Transact-SQL

Этот учебник демонстрирует использование Transact-SQL для загрузки данных в [пула данных](concept-data-pool.md) кластера SQL Server 2019 больших данных (Предварительная версия). С кластерами больших данных в SQL Server данные из различных источников можно принимаются и распределения между экземплярами пула данных.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
> * Создайте внешнюю таблицу в пуле данных.
> * Вставьте образец веб-маршрута перемещения данных в таблице пула данных.
> * Объединить данные в таблице пула данных с локальными таблицами.

> [!TIP]
> При желании можно загрузить и запустить сценарий для команды в этом руководстве. Инструкции см. в разделе [данных пулов примеры](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) на сайте GitHub.

## <a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка образца данных в кластере больших данных](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Создайте внешнюю таблицу в пул данных

Следующие шаги создания внешней таблицы в пуле данных с именем **web_clickstream_clicks_data_pool**. Эта таблица можно затем использовать как расположение для приема данных к кластеру больших данных.

1. В Azure Data Studio подключитесь к основной экземпляр SQL Server кластера больших данных. Дополнительные сведения см. в разделе [подключение к экземпляру SQL Server master](connect-to-big-data-cluster.md#master).

1. Дважды щелкните подключение в **серверы** окно для отображения панели мониторинга сервера для главного экземпляра SQL Server. Выберите **новый запрос**.

   ![Запрос главного экземпляра SQL Server](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Выполните следующую команду Transact-SQL, чтобы изменить контекст, чтобы **Sales** базы данных master экземпляра.

   ```sql
   USE Sales
   GO
   ```

1. Создайте внешнюю таблицу с именем **web_clickstream_clicks_data_pool** пула данных. `SqlDataPool` Источником данных является типом источника данных, можно использовать из главного экземпляра служб кластера больших данных.

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
  
1. В CTP-версии 2.3 Создание данных пула является асинхронным, но нет способа определить, когда сеть будет еще. Подождите 2 минуты, чтобы убедиться в том, что при создании пула данных, прежде чем продолжить.

## <a name="load-data"></a>Загрузка данных

Следующие действия приема пример веб-маршрута перемещения данных в пул данных с помощью внешней таблицы, созданной на предыдущих шагах.

1. Определите переменные для запроса, который вы хотите использовать для вставки данных в пул данных. Затем с помощью **модели... sp_data_pool_table_insert_data** хранимую процедуру для вставки результатов из запроса в пуле данных ( **web_clickstream_clicks_data_pool** внешней таблицы).

   ```sql
   DECLARE @db_name SYSNAME = 'Sales'
   DECLARE @schema_name SYSNAME = 'dbo'
   DECLARE @table_name SYSNAME = 'web_clickstream_clicks_data_pool'
   DECLARE @query NVARCHAR(MAX) = '
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
   FROM sales.dbo.web_clickstreams
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
      AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;'

   EXEC model..sp_data_pool_table_insert_data @db_name, @schema_name, @table_name, @query
   ```

1. Проверьте данные, вставленные с два запроса SELECT.

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>Запрос данных

Присоединяйтесь к сохраненные результаты запроса в пуле данных с локальными данными в **Sales** таблицы.

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

## <a name="clean-up"></a>Очистить

Используйте следующую команду для удаления объектов базы данных, созданной в этом учебнике.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о том, как прием данных в пуле данных с помощью заданий Spark:
> [!div class="nextstepaction"]
> [Прием данных с помощью заданий Spark](tutorial-data-pool-ingest-spark.md)
