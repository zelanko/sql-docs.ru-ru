---
title: Подключение Spark к SQL Server
titleSuffix: SQL Server big data clusters
description: Узнайте, как использовать соединитель Spark MSSQL в Spark для чтения и записи к SQL Server.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d4fde2e13efdebd0cdaad4a4f1c7e528c46ea136
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412881"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>Как считывать и записывать в SQL Server из Spark с помощью соединителя Spark MSSQL

Шаблон использования ключа больших данных — обработка большого объема данных в Spark, следуют запись данных в SQL Server для доступа к бизнес-приложениям. Эти шаблоны использования преимущества соединитель, который использует основные методы оптимизации SQL и обеспечивает механизм эффективно записи.

В этой статье приведен пример того, как использовать соединитель MSSQL Spark для чтения и записи в следующие расположения в пределах кластера больших данных.

1. Основной экземпляр SQL Server
1. Пул данных SQL Server

   ![Схема соединителя MSSQL Spark](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

Образец выполняет следующие задачи:

- Чтение файла из HDFS и выполнить некоторые основные обработку.
- Записи таблицы данных master экземпляра SQL Server как таблицу SQL, и затем обратиться к таблице для блока данных.
- Записи таблицы данных в пул данных SQL Server при внешней таблицы SQL и затем чтения внешней таблицы к таблице данных.

## <a name="mssql-spark-connector-interface"></a>Интерфейс соединителя Spark MSSQL

Предварительная версия SQL Server 2019 предоставляет **соединитель MSSQL Spark** для больших объемов данных кластеров, с помощью SQL Server массовых записи API-интерфейсы для Spark записи SQL. Соединитель Spark MSSQL основана на источнике данных Spark API-интерфейсы и предлагает привычный интерфейс соединитель Spark JDBC. Параметры интерфейса см. в статье [документации Apache Spark](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Соединитель MSSQL Spark ссылается имя **com.microsoft.sqlserver.jdbc.spark**.

В следующей таблице описаны параметры интерфейса, которые были изменены или не знакомы:

| Имя свойства | Необязательно | Описание |
|---|---|---|
| **IsolationLevel** | Да | Эта статья содержит уровень изоляции соединения. Значение по умолчанию для соединителя MSSQLSpark — **READ_COMMITTED** |

Соединитель использует SQL Server массового написании интерфейсов API. Каждая операция записи массового параметры могут передаваться в качестве необязательных параметров пользователя и передаются в виде — является соединителем для базового интерфейса API. Дополнительные сведения о массовой операции записи, см. в разделе [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="prerequisites"></a>предварительные требования

- Объект [кластера больших данных в SQL Server](deploy-get-started.md).

- [Azure Data Studio](https://aka.ms/azdata-insiders).

## <a name="create-the-target-database"></a>Создайте целевую базу данных

1. Откройте Azure Data Studio, и [подключитесь к экземпляру SQL Server главного кластера больших данных](connect-to-big-data-cluster.md).

1. Создайте новый запрос и выполните следующую команду для создания образца базы данных с именем **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>Загрузка образца данных в HDFS

1. Скачайте [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) на локальный компьютер.

1. Запуск студии данных Azure, и [подключения к кластеру больших данных](connect-to-big-data-cluster.md).

1. Щелкните правой кнопкой мыши на папку HDFS в кластере больших данных и выберите **новый каталог**. Имя каталога **spark_data**.

1. Щелкните правой кнопкой мыши **spark_data** каталог и выберите **передача файлов**. Отправка **AdultCensusIncome.csv** файла.

   ![AdultCensusIncome CSV-файла](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>Запустите пример записную книжку

Для демонстрации использования соединителя Spark MSSQL с этими данными, можно загрузить образец notebook, откройте его в Azure Data Studio и выполните каждый блок кода. Дополнительные сведения о работе с записными книжками, см. в разделе [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

1. Из командной строки PowerShell или bash, выполните следующую команду, чтобы скачать **mssql_spark_connector.ipynb** записной книжки для примера:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/spark_to_sql/mssql_spark_connector.ipynb"
   ```

1. В Azure Data Studio откройте файл примера записной книжки. Убедитесь, что она подключена к шлюзу HDFS или Spark для кластера больших данных.

1. Выполнения каждой ячейки кода в примере, чтобы просматривать сведения об использовании соединителя MSSQL Spark.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [кластеров развертывание больших данных в SQL Server в Kubernetes](deployment-guidance.md)