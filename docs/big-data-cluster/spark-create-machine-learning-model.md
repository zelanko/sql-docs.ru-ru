---
title: Создание и экспорт моделей машинного обучения Spark с помощью Млеап
titleSuffix: SQL Server big data clusters
description: Используйте PySpark для обучения и создания моделей машинного обучения с помощью [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Spark на (Предварительная версия). Экспортируйте с помощью Млеап, а затем оцените модель с помощью Java в SQL Server.
author: RogPodge
ms.author: roliu
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bba570a4ac68cf5a4d1405d4152669ed9ed211a0
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653410"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Создание, экспорт и оценка моделей машинного обучения Spark на[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

В следующем примере показано, как создать модель с помощью [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html), экспортировать модель в [млеап](http://mleap-docs.combust.ml/)и оценить модель в SQL Server с [расширением языка Java](../language-extensions/language-extensions-overview.md). Это делается в контексте кластера больших данных SQL Server 2019.

На следующей схеме показана работа, выполненная в этом примере:

![Экспорт результатов обучения с помощью Spark](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>Предварительные требования

Все файлы для этого примера находятся в [https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml)папке.

Чтобы запустить пример, необходимо также выполнить следующие предварительные требования.

- [SQL Server кластер больших данных](deploy-get-started.md)

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Обучение модели с помощью Spark ML

В этом примере для построения модели конвейера Spark машинного обучения используется перепись данных (**адултценсусинкоме. csv**).

1. Используйте файл [mleap_sql_test/Setup. sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/setup.sh) , чтобы скачать набор данных из Интернета и разместить его в HDFS в SQL Server кластере больших данных. Это обеспечивает доступ к нему с помощью Spark.

1. Затем скачайте пример записной книжки [train_score_export_ml_models_with_spark. ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb). В командной строке PowerShell или bash выполните следующую команду, чтобы скачать записную книжку:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Эта записная книжка содержит ячейки с необходимыми командами для этого раздела примера.

1. Откройте записную книжку в Azure Data Studio и выполните каждый блок кода. Дополнительные сведения о работе с записными книжками см. в статье [Использование записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

Данные сначала считываются в Spark и разбиваются на обучающие и проверочные наборы данных. Затем код обучает модель конвейера с обучающими данными. Наконец, она экспортирует модель в пакет Млеап.

> [!TIP]
> Вы также можете проверить или выполнить код Python, связанный с этими шагами, за пределами записной книжки в файле [mleap_sql_test/mleap_pyspark. корректировки](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_pyspark.py) .

## <a name="model-scoring-with-sql-server"></a>Оценка модели с помощью SQL Server

Теперь, когда модель конвейера Spark машинного обучения находится в стандартном формате [пакета сериализации млеап](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html) , можно оценить модель в Java без наличия Spark. 

В этом примере используется [расширение языка Java](../language-extensions/language-extensions-overview.md) в SQL Server. Чтобы оценить модель в SQL Server, сначала необходимо создать приложение Java, которое может загрузить модель в Java и оценить ее. Пример кода для этого приложения Java можно найти в [папке MSSQL-млеап-App](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mssql-mleap-app).

После создания примера можно использовать Transact-SQL для вызова приложения Java и оценки модели с таблицей базы данных. Это можно увидеть в исходном файле три [mleap_sql_test/mleap_sql_tests. корректировки](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_sql_tests.py) .

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в статье [развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md) .
