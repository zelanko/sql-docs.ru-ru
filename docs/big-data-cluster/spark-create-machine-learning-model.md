---
title: Создание и экспорт машинного обучения моделей с MLeap Spark
titleSuffix: SQL Server big data clusters
description: Используйте PySpark для обучения и создания моделей машинного обучения с помощью Spark в кластерах больших данных SQL Server (Предварительная версия). Экспорт с MLeap, а затем в SQL Server для создания модели с помощью Java.
author: lgongmsft
ms.author: lgong
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aa4c31eca725e8e662937259f078cf00a3441915
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727375"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-sql-server-big-data-clusters"></a>Создание, экспорт и оценка моделей машинного обучения Spark в кластерах больших данных в SQL Server

Ниже приведен пример, как создать модель с [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html), экспортировать модель для [MLeap](http://mleap-docs.combust.ml/)и оценка модели в SQL Server с его [расширение языка Java](../language-extensions/language-extensions-overview.md). Это делается в контексте кластера SQL Server 2019 больших данных.

На следующей схеме показана работа, выполняемая в этом примере:

![Экспорт оценки обучение с помощью spark](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>предварительные требования

Все файлы для этого образца приведены в [ https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml ](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml).

Чтобы запустить пример, необходимо также иметь следующие предварительные требования:

- Объект [кластера больших данных в SQL Server](deploy-get-started.md)

- [Средства работы с большими данными](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Обучение модели с помощью машинного Обучения Spark

Для этого примера данных переписи населения (**AdultCensusIncome.csv**) используется для создания модели машинного Обучения Spark конвейера.

1. Используйте [mleap_sql_test/setup.sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/setup.sh) файл, чтобы скачать набор данных из Интернета и поместите ее в HDFS в кластере SQL Server больших данных. Это позволяет получать доступ к ней с помощью Spark.

1. Загрузите образец notebook [train_score_export_ml_models_with_spark.ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb). Из командной строки PowerShell или bash выполните следующую команду, чтобы загрузить записную книжку:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Эта записная книжка содержит ячейки с необходимые команды для этого раздела примера.

1. Откройте записную книжку в Azure Data Studio и выполните каждый блок кода. Дополнительные сведения о работе с записными книжками, см. в разделе [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).

Сначала данные считываются в Spark и разбить на обучающий и проверочный наборы данных. Затем код обучает модель конвейера с обучающими данными. Наконец он экспортирует комплект MLeap модели.

> [!TIP]
> Можно также просмотреть и выполнять код Python, связанных с этими шагами за пределами записную книжку в [mleap_sql_test/mleap_pyspark.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_pyspark.py) файла.

## <a name="model-scoring-with-sql-server"></a>Модель оценки при помощи SQL Server

Теперь, когда модель конвейера машинного Обучения Spark находится в распространенных сериализации [MLeap пакета](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html) формате, вы можете оценить модели на языке Java в отсутствие Spark. 

В этом примере используется [расширение языка Java](../language-extensions/language-extensions-overview.md) в SQL Server. С целью оценки модели в SQL Server, необходимо сначала создать приложение Java, которое можно загрузить модель в Java и оценить ее. Можно найти в примере кода для этого приложения Java в [папка mssql-mleap-app](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mssql-mleap-app).

После построения образца можно использовать Transact-SQL для вызова приложения Java и оценка модели с таблицей базы данных. Это можно увидеть в тебя [mleap_sql_test/mleap_sql_tests.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_sql_tests.py) исходный файл.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [кластеров развертывание больших данных в SQL Server в Kubernetes](deployment-guidance.md)
