---
title: Прием данных с помощью заданий Spark
titleSuffix: SQL Server Big Data Clusters
description: В этом руководстве описано, как принимать данные в пул данных кластера больших данных SQL Server с помощью заданий Spark в Azure Data Studio.
author: rajmera3
ms.author: raajmera
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0eb0069b2f98a42b1069dcef283372c9711aae29
ms.sourcegitcommit: 1126792200d3b26ad4c29be1f561cf36f2e82e13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2020
ms.locfileid: "90076644"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Руководство по Прием данных в пул данных SQL Server с помощью заданий Spark

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этом учебнике описывается, как использовать задания Spark для загрузки данных в [пул данных](concept-data-pool.md)[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. 

В этом руководстве описано следующее:

> [!div class="checklist"]
> * Создание внешней таблицы в пуле данных.
> * Создание задания Spark для загрузки данных из HDFS.
> * Запрос результатов во внешней таблице.

> [!TIP]
> При необходимости вы можете скачать и выполнить скрипт, содержащий команды из этого руководства. См. инструкции в разделе [Примеры пулов данных](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) на сайте GitHub.

## <a name="prerequisites"></a><a id="prereqs"></a> Предварительные требования

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

1. Создайте разрешения для соединителя MSSQL-Spark.
   ```sql
   USE Sales
   CREATE LOGIN sample_user  WITH PASSWORD ='password123!#' 
   CREATE USER sample_user FROM LOGIN sample_user

   -- To create external tables in data pools
   GRANT ALTER ANY EXTERNAL DATA SOURCE TO sample_user;

   -- To create external tables
   GRANT CREATE TABLE TO sample_user;
   GRANT ALTER ANY SCHEMA TO sample_user;

   -- To view database state for Sales
   GRANT VIEW DATABASE STATE ON DATABASE::Sales TO sample_user;

   ALTER ROLE [db_datareader] ADD MEMBER sample_user
   ALTER ROLE [db_datawriter] ADD MEMBER sample_user
   ```

1. Создайте внешний источник данных для пула данных, если это не было сделано ранее.

   ```sql
   USE Sales
   GO
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
   
1. Создайте имя входа для пулов данных и предоставьте пользователю разрешения.
   ```sql 
   EXECUTE( ' Use Sales; CREATE LOGIN sample_user  WITH PASSWORD = ''password123!#'' ;') AT  DATA_SOURCE SqlDataPool;

   EXECUTE('Use Sales; CREATE USER sample_user; ALTER ROLE [db_datareader] ADD MEMBER sample_user;  ALTER ROLE [db_datawriter] ADD MEMBER sample_user;') AT DATA_SOURCE SqlDataPool;
   ```
   
Создание внешней таблицы пула данных является блокирующей операцией. Управление возвращается лишь после создания указанной таблицы на всех узлах пула данных серверной части. Если во время операции создания произойдет ошибка, сообщение о ней возвращается вызывающей стороне.

## <a name="start-a-spark-streaming-job"></a>Запуск задания потоковой передачи Spark

Следующим шагом является создание задания потоковой передачи Spark, которое загружает сведения о посещениях из пула носителей (HDFS) во внешнюю таблицу, созданную в пуле данных. Эти данные были добавлены в /clickstream_data в разделе [Загрузка примера данных в кластер больших данных](tutorial-load-sample-data.md).

1. В Azure Data Studio установите подключение к главному экземпляру в кластере больших данных. Дополнительные сведения см. в разделе [Подключение к кластеру больших данных](connect-to-big-data-cluster.md).

2. Создайте новую записную книжку и выберите Spark | Scala в качестве ядра.

3. Запуск задания приема Spark

   1. Настройка параметров соединителя Spark-SQL

    > [!NOTE]
    > Если кластер больших данных развертывается с интеграцией с Active Directory, замените значение **hostname** ниже, чтобы оно включало полное доменное имя, добавленное к имени службы. Пример: *hostname=master-p-svc.\<domainName>* .

      ```
      import org.apache.spark.sql.types._
      import org.apache.spark.sql.{SparkSession, SaveMode, Row, DataFrame}

      // Change per your installation
      val user= "username"
      val password= "****"
      val database =  "MyTestDatabase"
      val sourceDir = "/clickstream_data"
      val datapool_table = "web_clickstreams_spark_results"
      val datasource_name = "SqlDataPool"
      val schema = StructType(Seq(
      StructField("wcs_click_date_sk",LongType,true), StructField("wcs_click_time_sk",LongType,true), 
      StructField("wcs_sales_sk",LongType,true), StructField("wcs_item_sk",LongType,true),
      StructField("wcs_web_page_sk",LongType,true), StructField("wcs_user_sk",LongType,true)
      ))

      val hostname = "master-p-svc"
      val port = 1433
      val url = s"jdbc:sqlserver://${hostname}:${port};database=${database};user=${user};password=${password};"
      ```
   2. Определение и запуск задания Spark
      * Каждое задание состоит из двух частей: readStream и writeStream. Ниже мы создадим кадр данных, используя определенную выше схему, а затем запишем его во внешнюю таблицу в пуле данных.
      ```
      import org.apache.spark.sql.{SparkSession, SaveMode, Row, DataFrame}
      
      val df = spark.readStream.format("csv").schema(schema).option("header", true).load(sourceDir)
      val query = df.writeStream.outputMode("append").foreachBatch{ (batchDF: DataFrame, batchId: Long) => 
                batchDF.write
                 .format("com.microsoft.sqlserver.jdbc.spark")
                 .mode("append")
                  .option("url", url)
                  .option("dbtable", datapool_table)
                  .option("user", user)
                  .option("password", password)
                  .option("dataPoolDataSource",datasource_name).save()
               }.start()

      query.awaitTermination(40000)
      query.stop()
      ```
## <a name="query-the-data"></a>Запрос данных

Следующие шаги показывают, что задание потоковой передачи Spark загрузило данные из HDFS в пул данных.

1. Перед запросом полученных данных просмотрите состояние выполнения Spark, включая идентификатор приложения Yarn, пользовательский интерфейс Spark и журналы драйверов. Эти сведения будут отображаться в записной книжке при первом запуске приложения Spark.

   ![Сведения о выполнении Spark](./media/tutorial-data-pool-ingest-spark/Spark-Joblog-sparkui-yarn.png)

1. Вернитесь в окно запроса главного экземпляра SQL Server, которое было открыто в начале работы с этим руководством.

1. Выполните приведенный ниже запрос, чтобы изучить принятые данные.

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```
1. Данные также можно запрашивать в Spark. Например, приведенный ниже код выводит число записей в таблице.
   ```
   def df_read(dbtable: String,
                url: String,
                dataPoolDataSource: String=""): DataFrame = {
        spark.read
             .format("com.microsoft.sqlserver.jdbc.spark")
             .option("url", url)
             .option("dbtable", dbtable)
             .option("user", user)
             .option("password", password)
             .option("dataPoolDataSource", dataPoolDataSource)
             .load()
             }

   val new_df = df_read(datapool_table, url, dataPoolDataSource=datasource_name)
   println("Number of rows is " +  new_df.count)
   ```
## <a name="clean-up"></a>Очистка

Выполните следующую команду, чтобы удалить объекты базы данных, созданные в рамках этого руководства.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Дальнейшие действия

См. сведения о запуске примера записной книжки в Azure Data Studio:
> [!div class="nextstepaction"]
> [Запуск примера записной книжки](notebooks-tutorial-spark.md).
