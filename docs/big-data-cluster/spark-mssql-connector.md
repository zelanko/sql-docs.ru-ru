---
title: Подключение Spark к SQL Server
titleSuffix: SQL Server big data clusters
description: Сведения о том, как использовать соединитель MSSQL Spark в Spark для чтения и записи данных в SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 19edd6bf2e28a0dd0ec2007493dc02ff55108554
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531613"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>Чтение и запись в SQL Server из Spark с помощью соединителя MSSQL Spark

Ключевой шаблон использования больших данных — это обработка больших объемов данных в Spark, а также запись данных в SQL Server для доступа к бизнес-приложениям. Эти шаблоны используют преимущества соединителя, который использует основные оптимизации SQL и предоставляет эффективный механизм записи.

В этой статье приведен пример использования соединителя MSSQL Spark для чтения и записи в следующих расположениях внутри кластера больших данных.

1. Главный экземпляр SQL Server
1. Пул данных SQL Server

   ![Схема соединителя MSSQL Spark](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

Этот пример выполняет следующие задачи.

- Чтение файла из HDFS и выполнение базовой обработки.
- Запись кадра данных в главный экземпляр SQL Server в виде таблицы SQL и последующее считывание таблицы в кадр данных.
- Запись кадра данных в пул данных SQL Server в виде внешней таблицы SQL и последующее считывание внешней таблицы в кадр данных.

## <a name="mssql-spark-connector-interface"></a>Интерфейс соединителя MSSQL Spark

SQL Server 2019 предоставляет **соединитель MSSQL Spark** для кластеров больших данных, использующий API массовой записи SQL Server для записи из Spark в SQL. Соединитель MSSQL Spark основан на интерфейсах API источника данных Spark и предоставляет привычный интерфейс соединителя JDBC Spark. Сведения о параметрах интерфейса см. в [документации по Apache Spark](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Для ссылки на соединитель MSSQL используется имя **com.microsoft.sqlserver.jdbc.spark**.

В следующей таблице описаны параметры интерфейса, которые были изменены или являются новыми.

| Имя свойства | Необязательно | Описание |
|---|---|---|
| **isolationLevel** | Да | Описывает уровень изоляции подключения. По умолчанию для соединителя MSSQLSpark используется **READ_COMMITTED** |

Соединитель использует API-интерфейсы массовой записи SQL Server. Любые параметры массовой записи могут передаваться пользователем в качестве необязательного параметра и передаются соединителем в базовый API. Дополнительные сведения об операциях массовой записи см. в разделе [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="prerequisites"></a>предварительные требования

- [Кластер больших данных SQL Server](deploy-get-started.md).

- [Azure Data Studio](https://aka.ms/getazuredatastudio).

## <a name="create-the-target-database"></a>Создание целевой базы данных

1. Откройте Azure Data Studio и [установите подключение к главному экземпляру SQL Server в кластере больших данных](connect-to-big-data-cluster.md).

1. Создайте запрос и выполните приведенную ниже команду, чтобы создать пример базы данных с именем **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>Загрузка примера данных в HDFS

1. Скачайте [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) на локальный компьютер.

1. Запустите Azure Data Studio и [подключитесь к кластеру больших данных](connect-to-big-data-cluster.md).

1. Щелкните правой кнопкой мыши папку HDFS в кластере больших данных и выберите пункт **Создать каталог**. Назовите каталог **spark_data**.

1. Щелкните правой кнопкой мыши каталог **spark_data** и выберите **Отправить файлы**. Отправьте файл **AdultCensusIncome.csv**.

   ![CSV-файл AdultCensusIncome](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>Запуск примера записной книжки

Чтобы продемонстрировать использование соединителя MSSQL Spark с этими данными, можно скачать пример записной книжки, открыть его в Azure Data Studio и выполнить каждый блок кода. Дополнительные сведения о работе с записными книжками см. в статье [Использование записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

1. В командной строке PowerShell или bash выполните следующую команду, чтобы скачать пример записной книжки **mssql_spark_connector.ipynb**.

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector.ipynb"
   ```

1. В Azure Data Studio откройте пример файла записной книжки. Убедитесь, что он подключен к шлюзу HDFS/Spark для кластера больших данных.

1. Выполните каждую ячейку кода в примере, чтобы просмотреть использование соединителя MSSQL Spark.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md).