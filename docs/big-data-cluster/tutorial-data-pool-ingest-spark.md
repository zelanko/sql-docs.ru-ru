---
title: Прием данных с помощью заданий Spark
titleSuffix: SQL Server big data clusters
description: В этом руководстве описано, каким образом выполняется прием данных в пул данных кластера больших данных SQL Server 2019 (предварительная версия) с помощью заданий Spark в Azure Data Studio.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 06/26/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6d0ea6d4fb7a3aea9788c089ad68cb3bf523837f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67957818"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Руководство. Прием данных в пул данных SQL Server с помощью заданий Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом руководстве описано, каким образом выполняется загрузка данных в [пул данных](concept-data-pool.md) с помощью заданий Spark в кластере больших данных SQL Server 2019 (предварительная версия). 

В этом руководстве описано следующее.

> [!div class="checklist"]
> * Создание внешней таблицы в пуле данных.
> * Создание задания Spark для загрузки данных из HDFS.
> * Запрос результатов во внешней таблице.

> [!TIP]
> При необходимости вы можете скачать и выполнить скрипт, содержащий команды из этого руководства. См. инструкции в разделе [Примеры пулов данных](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) на сайте GitHub.

## <a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка примера данных в кластер больших данных](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Создание внешней таблицы в пуле данных

Выполните следующие действия, чтобы создать внешнюю таблицу с именем **web_clickstreams_spark_results** в пуле данных. В дальнейшем эта таблица может использоваться для приема данных в кластер больших данных.

1. В Azure Data Studio установите подключение к главному экземпляру SQL Server в кластере больших данных. Дополнительные сведения см. в разделе [Подключение к главному экземпляру SQL Server](connect-to-big-data-cluster.md#master).

1. Дважды щелкните подключение в окне **Серверы**, чтобы открыть панель мониторинга сервера для главного экземпляра SQL Server. Выберите **Создать запрос**.

   ![Запрос главного экземпляра SQL Server](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. Создайте внешний источник данных для пула данных, если это не было сделано ранее.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://controller-svc/default');
   ```

1. Создайте внешнюю таблицу с именем **web_clickstreams_spark_results** в пуле данных.

   ```sql
   USE Sales
   GO
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstreams_spark_results')
      CREATE EXTERNAL TABLE [web_clickstreams_spark_results]
      ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. В CTP 3.1 создание пула данных выполняется асинхронно, однако на данный момент не реализованы способы определить момент завершения этого процесса. Прежде чем продолжать, подождите примерно две минуты, чтобы удостовериться в создании пула данных.

## <a name="start-a-spark-streaming-job"></a>Запуск задания потоковой передачи Spark

Следующим шагом является создание задания потоковой передачи Spark, которое загружает сведения о посещениях из пула носителей (HDFS) во внешнюю таблицу, созданную в пуле данных.

1. В Azure Data Studio установите подключение к главному экземпляру в кластере больших данных. Дополнительные сведения см. в разделе [Подключение к кластеру больших данных](connect-to-big-data-cluster.md).

1. Дважды щелкните подключение шлюза HDFS/Spark в окне **Серверы**. Затем выберите **New Spark Job** (Создать задание Spark).

   ![Создание задания Spark](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. В окне **Создание задания** введите имя в поле **Имя задания**.

1. В раскрывающемся списке **Файл JAR/PY** выберите **HDFS**. Введите следующий путь к JAR-файлу.

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. В поле **Класс Main** введите `FileStreaming`.

1. В поле **Аргументы** введите приведенный ниже текст, указав пароль для главного экземпляра SQL Server в заполнителе `<your_password>`. 

   ```text
   --server mssql-master-pool-0.service-master-pool --port 1433 --user sa --password <your_password> --database sales --table web_clickstreams_spark_results --source_dir hdfs:///clickstream_data --input_format csv --enable_checkpoint false --timeout 380000
   ```

   В следующей таблице описаны все аргументы.

   | Аргумент | Описание |
   |---|---|
   | имя сервера | Сервер SQL Server, используемый для чтения схемы таблицы |
   | номер порта | Порт, прослушиваемый SQL Server (по умолчанию 1433) |
   | username | Имя пользователя для входа SQL Server |
   | password | Пароль для входа SQL Server |
   | Имя базы данных | Целевая база данных |
   | external table name | Таблица, используемая для результатов |
   | Исходный каталог для потоковой передачи | Это должен быть полный универсальный код ресурса (URI), например hdfs:///clickstream_data |
   | input format | Это может быть csv, parquet или json |
   | enable checkpoint | true или false |
   | timeout | Время выполнения задания в миллисекундах перед выходом |

1. Нажмите кнопку **Отправить**, чтобы отправить задание.

   ![Отправка задания Spark](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

## <a name="query-the-data"></a>Запрос данных

Следующие шаги показывают, что задание потоковой передачи Spark загрузило данные из HDFS в пул данных.

1. Перед запросом принятых данных просмотрите выходные данные журнала задач, чтобы убедиться, что задание завершено.

   ![Журнал заданий Spark](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. Вернитесь в окно запроса главного экземпляра SQL Server, которое было открыто в начале работы с этим руководством.

1. Выполните приведенный ниже запрос, чтобы изучить принятые данные.

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```

## <a name="clean-up"></a>Очистка

Выполните следующую команду, чтобы удалить объекты базы данных, созданные в рамках этого руководства.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Следующие шаги

См. сведения о запуске примера записной книжки в Azure Data Studio:
> [!div class="nextstepaction"]
> [Запуск примера записной книжки](tutorial-notebook-spark.md).
