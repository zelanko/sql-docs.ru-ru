---
title: Создание и экспорт моделей машинного обучения Spark с помощью Млеап
titleSuffix: SQL Server big data clusters
description: Используйте PySpark для обучения и создания моделей машинного обучения с помощью Spark на SQL Server кластерах больших данных (Предварительная версия). Экспортируйте с помощью Млеап, а затем оцените модель с помощью Java в SQL Server.
author: lgongmsft
ms.author: lgong
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aa4c31eca725e8e662937259f078cf00a3441915
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "67727375"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-sql-server-big-data-clusters"></a>Создание, экспорт и оценка моделей машинного обучения Spark на SQL Server кластерах больших данных

В следующем примере показано, как создать модель с помощью [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html), экспортировать модель в [млеап](http://mleap-docs.combust.ml/)и оценить модель в SQL Server с [расширением языка Java](../language-extensions/language-extensions-overview.md). Это делается в контексте кластера больших данных SQL Server 2019.

На следующей схеме показана работа, выполненная в этом примере:

![Экспорт результатов обучения с помощью Spark](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>предварительные требования

Все файлы для этого примера находятся в [https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml)папке.

Чтобы запустить пример, необходимо также выполнить следующие предварительные требования.

- [SQL Server кластер больших данных](deploy-get-started.md)

- [Инструменты для обработки больших данных](deploy-big-data-tools.md)
   - **kubectl**
   - **листывания**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Обучение модели с помощью Spark ML

В этом примере для построения модели конвейера Spark машинного обучения используется перепись данных (**адултценсусинкоме. csv**).

1. Используйте файл [mleap_sql_test/Setup. sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/setup.sh) , чтобы скачать набор данных из Интернета и разместить его в HDFS в SQL Server кластере больших данных. Это обеспечивает доступ к нему с помощью Spark.

1. Затем скачайте пример записной книжки [train_score_export_ml_models_with_spark. ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb). В командной строке PowerShell или bash выполните следующую команду, чтобы скачать записную книжку:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Эта записная книжка содержит ячейки с необходимыми командами для этого раздела примера.

1. Откройте записную книжку в Azure Data Studio и выполните каждый блок кода. Дополнительные сведения о работе с записными книжками см. [в статье использование записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

Данные сначала считываются в Spark и разбиваются на обучающие и проверочные наборы данных. Затем код обучает модель конвейера с обучающими данными. Наконец, она экспортирует модель в пакет Млеап.

> [!TIP]
> Вы также можете проверить или выполнить код Python, связанный с этими шагами, за пределами записной книжки в файле [mleap_sql_test/mleap_pyspark. корректировки](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_pyspark.py) .

## <a name="model-scoring-with-sql-server"></a>Оценка модели с помощью SQL Server

Теперь, когда модель конвейера Spark машинного обучения находится в стандартном формате [пакета сериализации млеап](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html) , можно оценить модель в Java без наличия Spark. 

В этом примере используется [расширение языка Java](../language-extensions/language-extensions-overview.md) в SQL Server. Чтобы оценить модель в SQL Server, сначала необходимо создать приложение Java, которое может загрузить модель в Java и оценить ее. Пример кода для этого приложения Java можно найти в [папке MSSQL-млеап-App](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mssql-mleap-app).

После создания примера можно использовать Transact-SQL для вызова приложения Java и оценки модели с таблицей базы данных. Это можно увидеть в исходном файле три [mleap_sql_test/mleap_sql_tests. корректировки](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_sql_tests.py) .

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в статье [развертывание SQL Server кластеров больших данных в Kubernetes](deployment-guidance.md) .
