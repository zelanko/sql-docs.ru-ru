---
title: Прием данных с помощью заданий Spark
titleSuffix: SQL Server 2019 big data clusters
description: Этом руководстве показано, как прием данных в пул данных с помощью заданий Spark в Azure Data Studio кластера больших данных SQL Server 2019 (Предварительная версия).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: d1780ae630231cd96e9424f4f541d921b1496e7d
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432367"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Учебник. Прием данных в пул данных SQL Server с помощью заданий Spark

Этот учебник демонстрирует использование заданий Spark для загрузки данных в [пула данных](concept-data-pool.md) кластера SQL Server 2019 больших данных (Предварительная версия). 

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
> * Создайте внешнюю таблицу в пуле данных.
> * Создание задания Spark для загрузки данных из HDFS.
> * Запрос приведет к внешней таблице.

> [!TIP]
> При желании можно загрузить и запустить сценарий для команды в этом руководстве. Инструкции см. в разделе [данных пулов примеры](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) на сайте GitHub.

## <a id="prereqs"></a> Предварительные требования

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
- [Загрузка образца данных в кластере больших данных](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Создайте внешнюю таблицу в пул данных

Следующие шаги создания внешней таблицы в пуле данных с именем **web_clickstreams_spark_results**. Эта таблица можно затем использовать как расположение для приема данных к кластеру больших данных.

1. В Azure Data Studio подключитесь к основной экземпляр SQL Server кластера больших данных. Дополнительные сведения см. в разделе [подключение к экземпляру SQL Server master](connect-to-big-data-cluster.md#master).

1. Дважды щелкните подключение в **серверы** окно для отображения панели мониторинга сервера для главного экземпляра SQL Server. Выберите **новый запрос**.

   ![Запрос главного экземпляра SQL Server](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. Создайте внешнюю таблицу с именем **web_clickstreams_spark_results** пула данных. `SqlDataPool` Источником данных является типом источника данных, можно использовать из главного экземпляра служб кластера больших данных.

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
  
1. В CTP-версии 2.2 Создание данных пула является асинхронным, но нет способа определить, когда сеть будет еще. Подождите 2 минуты, чтобы убедиться в том, что при создании пула данных, прежде чем продолжить.

## <a name="start-a-spark-streaming-job"></a>Запустить задание потоковой передачи Spark

Следующим шагом является создание Spark streaming задание, которое загружает веб-маршрута перемещения данных из пула носителей (HDFS) в внешнюю таблицу, которую вы создали в пуле данных.

1. В Azure Data Studio, подключитесь к **HDFS/Spark шлюза** кластера больших данных. Дополнительные сведения см. в разделе [подключиться к шлюзу HDFS/Spark](connect-to-big-data-cluster.md#hdfs).

1. Дважды щелкните подключение шлюза HDFS или Spark в **серверы** окна. Затем выберите **новое задание Spark**.

   ![Создание задания Spark](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. В **новое задание** окно, введите имя в **имя задания** поля.

1. В **файл Jar/py** раскрывающегося списка, выберите **HDFS**. Затем введите следующий путь к файлу JAR-файл:

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. В **класс Main** введите `FileStreaming`.

1. В **аргументы** введите следующий текст, указав пароль для главного экземпляра SQL Server в `<your_password>` заполнителя. 

   ```text
   --server mssql-master-pool-0.service-master-pool --port 1433 --user sa --password <your_password> --database sales --table web_clickstreams_spark_results --source_dir hdfs:///clickstream_data --input_format csv --enable_checkpoint false --timeout 380000
   ```

   В следующей таблице описаны все аргументы:

   | Аргумент | Описание |
   |---|---|
   | имя сервера | Использование SQL Server для чтения схемы таблицы |
   | Номер порта | Порт SQL Server прослушивает (по умолчанию 1433) |
   | username | Имя пользователя для входа SQL Server |
   | password | Пароль для входа в SQL Server |
   | Имя базы данных | Целевая база данных |
   | Имя внешней таблицы | Таблица, используемая для результатов |
   | Исходный каталог для потоковой передачи | Это должен быть полным URI, например «hdfs: / / / clickstream_data» |
   | формат входных данных | Это может быть «csv», «parquet» или «json» |
   | Включить контрольную точку | true или false |
   | timeout | время выполнения задания в миллисекундах перед выходом из |

1. Нажмите клавишу **отправить** для отправки задания.

   ![Отправка заданий Spark](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

## <a name="query-the-data"></a>Запрос данных

Ниже показано, что задание потоковой передачи Spark загружены данные из HDFS в пул данных.

1. Перед выполнением запроса данные, полученные, просмотрите журнал выходных данных задачи, чтобы убедиться, что задание выполнено.

   ![Журнал заданий Spark](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. Вернитесь в окно запроса главного экземпляра SQL Server, открытой в начале работы с этим руководством.

1. Выполните следующий запрос, чтобы проверить данные, полученные.

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```

## <a name="clean-up"></a>Очистить

Используйте следующую команду для удаления объектов базы данных, созданной в этом учебнике.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о том, как запустить записную книжку образец студии данных Azure:
> [!div class="nextstepaction"]
> [Запуск записной книжки образца](tutorial-notebook-spark.md)
