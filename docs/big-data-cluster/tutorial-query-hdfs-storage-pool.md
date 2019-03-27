---
title: Запрашивать данные из HDFS в пуле носителей
titleSuffix: SQL Server 2019 big data clusters
description: Этом руководстве показано, как запросить данные из HDFS в кластере SQL Server 2019 больших данных (Предварительная версия). Создайте внешнюю таблицу данных в пуле носителей и затем выполнить запрос.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: a8752f4879f4b03f89378e4f30c44c10dc272694
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494406"
---
# <a name="tutorial-query-hdfs-in-a-sql-server-big-data-cluster"></a>Учебник. Запрос HDFS в кластере SQL Server больших данных

Этом руководстве показано, как запросить данные из HDFS в кластере SQL Server 2019 больших данных (Предварительная версия).

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
> * Создайте внешнюю таблицу, указывающую на данные из HDFS в кластере больших данных.
> * Объединение этих данных с помощью данных высокой ценности, в основной экземпляр.

> [!TIP]
> При желании можно загрузить и запустить сценарий для команды в этом руководстве. Инструкции см. в разделе [образцы данных виртуализации](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) на сайте GitHub.

## <a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка образца данных в кластере больших данных](tutorial-load-sample-data.md)

## <a name="create-an-external-table-to-hdfs"></a>Создайте внешнюю таблицу в HDFS

Пул носителей содержит веб-маршрута перемещения данных в CSV-файле, хранящихся в HDFS. Выполните следующие действия для определения внешней таблицы, могут обращаться к данным в этом файле.

1. В Azure Data Studio подключитесь к основной экземпляр SQL Server кластера больших данных. Дополнительные сведения см. в разделе [подключение к экземпляру SQL Server master](connect-to-big-data-cluster.md#master).

1. Дважды щелкните подключение в **серверы** окно для отображения панели мониторинга сервера для главного экземпляра SQL Server. Выберите **новый запрос**.

   ![Запрос главного экземпляра SQL Server](./media/tutorial-query-hdfs-storage-pool/sql-server-master-instance-query.png)

1. Выполните следующую команду Transact-SQL, чтобы изменить контекст, чтобы **Sales** базы данных master экземпляра.

   ```sql
   USE Sales
   GO
   ```

1. Определите формат CSV-файла для чтения из HDFS. Нажмите клавишу F5 для запуска инструкции.

   ```sql
   CREATE EXTERNAL FILE FORMAT csv_file
   WITH (
       FORMAT_TYPE = DELIMITEDTEXT,
       FORMAT_OPTIONS(
           FIELD_TERMINATOR = ',',
           STRING_DELIMITER = '"',
           FIRST_ROW = 2,
           USE_TYPE_DEFAULT = TRUE)
   );
   ```

1. Создание внешнего источника данных в пул носителей, если он еще не существует.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
     CREATE EXTERNAL DATA SOURCE SqlStoragePool
     WITH (LOCATION = 'sqlhdfs://service-mssql-controller:8080');
   ```

1. Создание внешней таблицы, который может читать `/clickstream_data` из пула носителей. **SqlStoragePool** доступен из главного экземпляра служб кластерам больших данных.

   ```sql
   CREATE EXTERNAL TABLE [web_clickstreams_hdfs]
   ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
   WITH
   (
       DATA_SOURCE = SqlStoragePool,
       LOCATION = '/clickstream_data',
       FILE_FORMAT = csv_file
   );
   GO
   ```

## <a name="query-the-data"></a>Запрос данных

Выполните следующий запрос на объединение данных HDFS `web_clickstream_hdfs` внешнюю таблицу с реляционными данными в локальной `Sales` базы данных.

```sql
SELECT  
    wcs_user_sk,
    SUM( CASE WHEN i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
    SUM( CASE WHEN i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
    SUM( CASE WHEN i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
    SUM( CASE WHEN i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
    SUM( CASE WHEN i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
    SUM( CASE WHEN i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
    SUM( CASE WHEN i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
    SUM( CASE WHEN i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
    SUM( CASE WHEN i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
    SUM( CASE WHEN i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
  FROM [dbo].[web_clickstreams_hdfs]
  INNER JOIN item it ON (wcs_item_sk = i_item_sk
                        AND wcs_user_sk IS NOT NULL)
GROUP BY  wcs_user_sk;
GO
```

## <a name="clean-up"></a>Очистить

Используйте следующую команду для удаления внешней таблицы, используемые в этом руководстве.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_hdfs];
GO
```

## <a name="next-steps"></a>Следующие шаги

Перейдите к следующей статье, чтобы узнать, как запросить Oracle из кластера больших данных.
> [!div class="nextstepaction"]
> [Запрос внешних данных Oracle](tutorial-query-oracle.md)
