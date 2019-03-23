---
title: Пакет дополнительных компонентов Azure | Документация Майкрософт
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.SSIS.AZURE.F1
- SQL12.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 536dce64880c1e70b1b8a0c4b419811c1b32a975
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394531"
---
# <a name="azure-feature-pack"></a>Пакет дополнительных компонентов Azure
Пакет дополнительных компонентов Azure для служб SQL Server Integration Services (SSIS) — это дополнение, которое предоставляет перечисленные на этой странице компоненты для подключения служб SSIS к Azure, передачи данных между Azure и локальными источниками данных и обработки данных, хранящихся в Azure.

## <a name="components-in-the-feature-pack"></a>Компоненты в составе пакета дополнительных компонентов
  
-   Диспетчеры соединений  
  
    -   [Диспетчер подключений службы хранилища Azure](connection-manager/azure-storage-connection-manager.md)  
  
    -   [Диспетчер подключений подписки Azure](connection-manager/azure-subscription-connection-manager.md)  
    
    -   [Диспетчер подключений Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-connection-manager.md)
    
    -   [Диспетчер подключений Azure Resource Manager](../../2014/integration-services/azure-resource-manager-connection-manager.md)
    
    -   [Диспетчер подключений Azure HDInsight](../../2014/integration-services/azure-hdinsight-connection-manager.md)
  
-   Задания  
  
    -   [Задача передачи больших двоичных объектов Azure](control-flow/azure-blob-upload-task.md)  
  
    -   [Задача скачивания BLOB-объектов Azure](control-flow/azure-blob-download-task.md)  
  
    -   [Задача Hive для Azure HDInsight](control-flow/azure-hdinsight-hive-task.md)  
  
    -   [Задача Pig для Azure HDInsight](https://msdn.microsoft.com/library/mt146781(v=sql.120).aspx)
  
    -   [Задача создания кластера Azure HDInsight](control-flow/azure-hdinsight-create-cluster-task.md)  
  
    -   [Задача удаления кластера Azure HDInsight](control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Задача отправки в хранилище данных Azure SQL](../../2014/integration-services/azure-sql-dw-upload-task.md)    
    
    -   [Задача «Файловая система» для Azure Data Lake](control-flow/file-system-task.md)    
  
-   Компоненты потока данных  
  
    -   [Компонент Azure Blob Source](https://msdn.microsoft.com/library/mt146775(v=sql.120).aspx)  
  
    -   [Назначение больших двоичных объектов Azure](data-flow/azure-blob-destination.md)  
    
    -   [Источник Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-source.md)
    
    -   [Цель Azure Data Lake Store](../../2014/integration-services/azure-data-lake-store-destination.md)
  
-   Перечислитель больших двоичных объектов Azure и перечислитель файлов ADLS. См. раздел [Foreach Loop Container](control-flow/foreach-loop-container.md).  
  
 
## <a name="download-the-feature-pack"></a>Скачивание пакета дополнительных компонентов  
Скачайте пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure.  
  
-   [Microsoft SQL Server 2014 Integration Services пакет дополнительных компонентов для Azure](https://www.microsoft.com/download/details.aspx?id=47366)  

## <a name="prerequisites"></a>предварительные требования  
Перед установкой этого пакета необходимо установить следующие компоненты:  
  
-   Службы SQL Server Integration Services  
-   .NET Framework 4.5.  
  
## <a name="scenarios"></a>Сценарии  
  
### <a name="big-data-processing"></a>Обработка больших данных  
 Используйте соединитель Azure для выполнения следующих задач по обработке больших данных:  
  
1.  Передача входных данных в хранилище больших двоичных объектов Azure с помощью задачи передачи больших двоичных объектов Azure.  
  
2.  Создание кластера Azure HDInsight с помощью задачи создания кластера Azure HDInsight. Если вы хотите использовать собственный кластер, этот шаг является необязательным.  
  
3.  Запуск задания Pig или Hive в кластере Azure HDInsight с помощью задачи по запуску задания Pig в Azure HDInsight или задачи по запуску задания Hive в Azure HDInsight.  
  
4.  Удаление кластера Azure HDInsight после использования (если вы создавали кластер HDInsight по требованию на шаге 2) с помощью задачи удаления кластера Azure HDInsight.  
  
5.  Скачивание выходных данных из хранилища больших двоичных объектов Azure с помощью задачи скачивания больших двоичных объектов Azure HDInsight.  
  
 ![SSIS-AzureConnector-BigDataScenario](media/ssis-azureconnector-bigdatascenario.png "служб SSIS-AzureConnector-BigDataScenario")  
  
### <a name="cloud-data-archiving"></a>Архивация данных облака  
 Используйте назначение больших двоичных объектов Azure в пакете служб SSIS для записи выходных данных в хранилище больших двоичных объектов Azure или используйте источник больших двоичных объектов Azure для чтения данных из хранилища больших двоичных объектов Azure.  
  
 ![SSIS-AzureConnector-CloudArchive-1](media/ssis-azureconnector-cloudarchive-1.png "SSIS-AzureConnector-CloudArchive-1")  
  
 ![SSIS-AzureConnector-CloudArchive-2](media/ssis-azureconnector-cloudarchive-2.png "SSIS-AzureConnector-CloudArchive-2")  
  
 Используйте контейнер цикла Foreach с перечислителем больших двоичных объектов Azure для обработки данных в нескольких файлах больших двоичных объектов.  
  
 ![SSIS-AzureConnector-CloudArchive-3](media/ssis-azureconnector-cloudarchive-3.png "SSIS-AzureConnector-CloudArchive-3")  
  
  
