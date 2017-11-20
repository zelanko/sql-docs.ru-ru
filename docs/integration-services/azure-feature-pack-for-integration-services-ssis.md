---
title: "Пакет дополнительных компонентов Azure для служб Integration Services (SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.SSIS.AZURE.F1
- SQL14.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 4941d8eb846e9d47b008447fe0e346d43de5d87f
ms.openlocfilehash: d4204ba56e515025bed3ae3bf8e7a77d6da471be
ms.contentlocale: ru-ru
ms.lasthandoff: 08/30/2017

---
# <a name="azure-feature-pack-for-integration-services-ssis"></a>Пакет дополнительных компонентов Azure для служб Integration Services (SSIS)
Пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure — это расширение, предоставляет компоненты, перечисленные на этой странице для служб SSIS для подключения к службам Azure, передачи данных между Azure и локальными источниками данных и обработки данных, хранящихся в Azure.

[![Загрузите пакет компонентов служб SSIS для Azure](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/download/details.aspx?id=54798) **загрузки**

- Для SQL Server 2017 г - [Microsoft SQL Server 2017 г Integration Services пакета дополнительных компонентов для Azure](https://www.microsoft.com/download/details.aspx?id=54798)
- Для SQL Server 2016 — [Microsoft SQL Server 2016 Integration Services пакета дополнительных компонентов для Azure](https://www.microsoft.com/download/details.aspx?id=49492)
- Для SQL Server 2014 — [Microsoft SQL Server 2014 Integration Services пакета дополнительных компонентов для Azure](https://www.microsoft.com/en-us/download/details.aspx?id=47366)
- Для SQL Server 2012 — [Microsoft SQL Server 2012 Integration Services пакета дополнительных компонентов для Azure](https://www.microsoft.com/en-us/download/details.aspx?id=47367)

## <a name="components-in-the-feature-pack"></a>Компоненты в пакете дополнительных компонентов
-   Диспетчеры соединений

    -   [Диспетчер подключений службы хранилища Azure](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Диспетчер подключений подписки Azure](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
    -   [Диспетчер подключений Azure Data Lake Store](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)
    
    -   [Диспетчер соединений диспетчер ресурсов Azure](../integration-services/connection-manager/azure-resource-manager-connection-manager.md)
    
    -   [Диспетчер подключений Azure HDInsight](../integration-services/connection-manager/azure-hdinsight-connection-manager.md)

-   Задания

    -   [Задача передачи больших двоичных объектов Azure](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Задача скачивания BLOB-объектов Azure](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Задача Hive для Azure HDInsight](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Задача Pig для Azure HDInsight](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Задача создания кластера Azure HDInsight](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Задача удаления кластера Azure HDInsight](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Задача отправки в хранилище данных Azure SQL](../integration-services/control-flow/azure-sql-dw-upload-task.md)

    -   [Задача файловой системы для хранилища Озера данных Azure](../integration-services/control-flow/azure-data-lake-store-file-system-task.md)

-   Компоненты потока данных

    -   [Компонент Azure Blob Source](../integration-services/data-flow/azure-blob-source.md)

    -   [Назначение больших двоичных объектов Azure](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Источник Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Цель Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-destination.md)

-   BLOB-объектов Azure & ADLS файл перечислителя. В разделе [контейнер цикла Foreach](http://msdn.microsoft.com/library/95a19dde-61ca-4d9b-aa3d-131fa4264296)

## <a name="download-the-feature-pack"></a>Скачивание пакета дополнительных компонентов
 Загрузите SQL Server Integration Services (SSIS) пакете дополнительных компонентов для Azure.
 
- [Службы SSIS пакет дополнительных компонентов для Azure](http://go.microsoft.com/fwlink/?LinkID=626967) для SQL Server 2016
- [Службы SSIS пакет дополнительных компонентов для Azure](https://www.microsoft.com/en-us/download/details.aspx?id=54798) для[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Перед установкой этого пакета необходимо установить следующие компоненты:

-   службы SQL Server Integration Services
-   .NET Framework 4.5.

## <a name="scenario-processing-big-data"></a>Сценарий: обработка больших данных
 Используйте соединитель Azure для выполнения следующих задач по обработке больших данных:

1.  Передача входных данных в хранилище больших двоичных объектов Azure с помощью задачи передачи больших двоичных объектов Azure.

2.  Создание кластера Azure HDInsight с помощью задачи создания кластера Azure HDInsight. Если вы хотите использовать собственный кластер, этот шаг является необязательным.

3.  Запуск задания Pig или Hive в кластере Azure HDInsight с помощью задачи по запуску задания Pig в Azure HDInsight или задачи по запуску задания Hive в Azure HDInsight.

4.  Удаление кластера Azure HDInsight после использования (если вы создавали кластер HDInsight по требованию на шаге 2) с помощью задачи удаления кластера Azure HDInsight.

5.  Скачивание выходных данных из хранилища больших двоичных объектов Azure с помощью задачи скачивания больших двоичных объектов Azure HDInsight.

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>Сценарий: управление данными в облаке
 Используйте назначение больших двоичных объектов Azure в пакете SSIS для записи выходных данных в хранилище BLOB-объектов Azure или источник больших двоичных объектов Azure для чтения данных из хранилища BLOB-объектов Azure.

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 Используйте контейнер цикла Foreach с перечислителем BLOB-объектов Azure для обработки данных в нескольких файлах больших двоичных объектов.

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  

