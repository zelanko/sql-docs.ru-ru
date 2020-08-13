---
title: Подключение Spark к SQL Server
titleSuffix: SQL Server big data clusters
description: Сведения о том, как использовать соединитель Apache Spark для SQL Server и SQL Azure для чтения и записи данных в SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning-bdc
ms.openlocfilehash: 3cb36c4bdddfaa97b9b6c08015308799d54cb0dc
ms.sourcegitcommit: 56f6892b3795da308d226d4b3c5c859ead2e830a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86438076"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-apache-spark-connector-for-sql-server-and-azure-sql"></a>Чтение и запись данных в SQL Server из Spark с помощью соединителя Apache Spark для SQL Server и SQL Azure

Ключевой шаблон использования больших данных — это обработка больших объемов данных в Spark, а также запись данных в SQL Server для доступа к бизнес-приложениям. Эти шаблоны используют преимущества соединителя, который использует основные оптимизации SQL и предоставляет эффективный механизм записи.

В этой статье представлен обзор интерфейса соединителя Apache Spark для SQL Server и SQL Azure и создание его экземпляров для использования в режиме с AD и без AD. Также здесь приведен пример использования соединителя Apache Spark для SQL Server и SQL Azure для чтения и записи данных в следующих расположениях внутри кластера больших данных.
1. Главный экземпляр SQL Server
1. Пул данных SQL Server

   ![Схема соединителя Apache Spark для SQL Server и SQL Azure](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

## <a name="apache-spark-connector-for-sql-server-and-azure-sql-interface"></a>Интерфейс соединителя Apache Spark для SQL Server и SQL Azure

SQL Server 2019 предоставляет [**соединитель Apache Spark для SQL Server и SQL Azure**](https://github.com/microsoft/sql-spark-connector) для кластеров больших данных, использующий API массовой записи SQL Server для записи из Spark в SQL. Соединитель Apache Spark для SQL Server и SQL Azure основан на API источника данных Spark и предоставляет привычный интерфейс соединителя JDBC Spark. Сведения о параметрах интерфейса см. в [документации по Apache Spark](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Для ссылки на соединитель Apache Spark для SQL Server и SQL Azure используется имя **com.microsoft.sqlserver.jdbc.spark**. Соединитель Apache Spark для SQL Server и SQL Azure поддерживает два режима безопасности для подключения к SQL Server — без Active Directory (AD) и с Active Directory.
### <a name="non-ad-mode"></a>Режим без AD:
В режиме без AD каждый пользователь имеет имя пользователя и пароль, которые необходимо предоставить в качестве параметров во время создания экземпляра соединителя для выполнения операций чтения и записи.
Ниже приведен пример создания экземпляра соединителя для режима без AD:
```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark" 

url = "jdbc:sqlserver://master-p-svc;databaseName=?;"
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("user", ?) \ 
   .option("password",?) 
writer.save() 
```
### <a name="ad-mode"></a>Режим с AD:
В режиме безопасности с AD после того, как пользователь создал файл keytab, он должен указать `principal` и `keytab` в качестве параметров во время создания экземпляра соединителя.

В этом режиме драйвер загружает файл keytab в соответствующие контейнеры исполнителя. Затем исполнители используют имя участника и keytab для создания маркера, который используется для создания соединителя JDBC для чтения и записи.

Ниже приведен пример создания экземпляра соединителя для режима с AD:
```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark"

url = "jdbc:sqlserver://master-p-svc;databaseName=?;integratedSecurity=true;authenticationScheme=JavaKerberos;" 
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("principal", ?) \ 
   .option("keytab", ?)   

writer.save() 
```

В следующей таблице описаны параметры интерфейса, которые были изменены или являются новыми.

| Имя свойства | Необязательно | Описание |
|---|---|---|
| **isolationLevel** | Да | Описывает уровень изоляции подключения. По умолчанию для соединителя используется **READ_COMMITTED**. |

Соединитель использует API-интерфейсы массовой записи SQL Server. Любые параметры массовой записи могут передаваться пользователем в качестве необязательного параметра и передаются соединителем в базовый API. Дополнительные сведения об операциях массовой записи см. в разделе [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="apache-spark-connector-for-sql-server-and-azure-sql-sample"></a>Пример соединителя Apache Spark для SQL Server и SQL Azure
Этот пример выполняет следующие задачи.

- Чтение файла из HDFS и выполнение базовой обработки.
- Запись кадра данных в главный экземпляр SQL Server в виде таблицы SQL и последующее считывание таблицы в кадр данных.
- Запись кадра данных в пул данных SQL Server в виде внешней таблицы SQL и последующее считывание внешней таблицы в кадр данных.
### <a name="prerequisites"></a>Предварительные требования

- [Кластер больших данных SQL Server](deploy-get-started.md).

- [Azure Data Studio](https://aka.ms/getazuredatastudio).

### <a name="create-the-target-database"></a>Создание целевой базы данных

1. Откройте Azure Data Studio и [установите подключение к главному экземпляру SQL Server в кластере больших данных](connect-to-big-data-cluster.md).

1. Создайте запрос и выполните приведенную ниже команду, чтобы создать пример базы данных с именем **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

### <a name="load-sample-data-into-hdfs"></a>Загрузка примера данных в HDFS

1. Скачайте [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) на локальный компьютер.

1. Запустите Azure Data Studio и [подключитесь к кластеру больших данных](connect-to-big-data-cluster.md).

1. Щелкните правой кнопкой мыши папку HDFS в кластере больших данных и выберите пункт **Создать каталог**. Назовите каталог **spark_data**.

1. Щелкните правой кнопкой мыши каталог **spark_data** и выберите **Отправить файлы**. Отправьте файл **AdultCensusIncome.csv**.

   ![CSV-файл AdultCensusIncome](./media/spark-mssql-connector/spark_data.png)

### <a name="run-the-sample-notebook"></a>Запуск примера записной книжки

Чтобы продемонстрировать использование соединителя Apache Spark для SQL Server и SQL Azure с этими данными в режиме без AD, можно скачать пример записной книжки, открыть его в Azure Data Studio и выполнить каждый блок кода. Дополнительные сведения о работе с записными книжками см. в статье [Использование записных книжек в SQL Server](../azure-data-studio/notebooks-guidance.md).

1. В командной строке PowerShell или оболочке Bash выполните следующую команду, чтобы скачать пример записной книжки **mssql_spark_connector_non_ad_pyspark.ipynb**:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector_non_ad_pyspark.ipynb"
   ```

1. В Azure Data Studio откройте пример файла записной книжки. Убедитесь, что он подключен к шлюзу HDFS/Spark для кластера больших данных.

1. Выполните каждую ячейку кода в примере, чтобы просмотреть использование соединителя Apache Spark для SQL Server и SQL Azure.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md).

У вас есть отзывы или рекомендации по функциям для кластеров больших данных SQL Server? [Напишите нам в разделе "Отзывы от кластерах больших данных SQL Server"](https://aka.ms/sql-server-bdc-feedback).
