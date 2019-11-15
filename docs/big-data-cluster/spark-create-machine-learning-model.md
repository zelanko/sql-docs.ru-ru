---
title: Создание и экспорт моделей машинного обучения Spark с помощью MLeap
titleSuffix: SQL Server big data clusters
description: Используйте PySpark для обучения и создания моделей машинного обучения в Spark в Кластерах больших данных SQL Server. Выполните экспорт с помощью MLeap, а затем оцените модель с помощью Java в SQL Server.
author: RogPodge
ms.author: roliu
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bc9191ad90b05e9f48facab0cc4003bbf5adce11
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844228"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Создание, экспорт и оценка моделей машинного обучения Spark в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

Следующий пример демонстрирует, как строить модель с помощью [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html), экспортировать эту модель в [MLeap](http://mleap-docs.combust.ml/) и оценивать ее в SQL Server с помощью [расширения языка Java](../language-extensions/language-extensions-overview.md). Это делается в контексте кластера больших данных SQL Server 2019.

На следующей схеме показана работа, выполненная в этом примере.

![Экспорт оценки обучения с помощью Spark](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>предварительные требования

Все файлы для этого примера находятся в [https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml).

Для выполнения этого примера необходимы также следующие элементы.

- [Кластер больших данных SQL Server](deploy-get-started.md)

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Обучение модели с помощью Spark ML

Для этого примера используются данные переписи (**AdultCensusIncome.csv**), на основе которых строится модель конвейера Spark ML.

1. Используйте файл [mleap_sql_test/setup.sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/setup.sh) для загрузки набора данных из Интернета и размещения его в HDFS в вашем кластере больших данных SQL Server. Это обеспечивает доступ к нему из Spark.

1. Затем скачайте пример записной книжки [train_score_export_ml_models_with_spark.ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb). В командной строке PowerShell или bash выполните следующую команду, чтобы скачать записную книжку:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Эта записная книжка содержит ячейки с необходимыми командами для данного раздела примера.

1. Откройте записную книжку в Azure Data Studio и выполните каждый блок кода. Дополнительные сведения о работе с записными книжками см. в статье [Использование записных книжек в SQL Server](notebooks-guidance.md).

Данные сначала считываются в Spark и разбиваются на наборы данных для обучения и тестирования. Затем код обучает модель конвейера с использованием обучающих данных. Наконец, модель экспортируется в пакет MLeap.

> [!TIP]
> Вы также можете проверить или выполнить код Python, соответствующий этим действиям, вне записной книжки, в файле [mleap_sql_test/mleap_pyspark.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_pyspark.py).

## <a name="model-scoring-with-sql-server"></a>Оценка модели в SQL Server

Теперь, когда модель конвейера Spark ML находится в стандартном пакете сериализации [MLeap](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html), можно оценивать модель в Java без наличия Spark. 

В этом примере используется [расширение языка Java](../language-extensions/language-extensions-overview.md) в SQL Server. Для оценки модели в SQL Server сначала необходимо создать приложение Java, которое может загрузить модель в Java и оценить ее. Пример кода для этого приложения Java можно найти в [папке mssql-mleap-app](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mssql-mleap-app).

После сборки примера можно использовать Transact-SQL для вызова приложения Java и оценки модели с помощью таблицы базы данных. Это можно увидеть в исходном файле [mleap_sql_test/mleap_sql_tests.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_sql_tests.py).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в статье [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md).
