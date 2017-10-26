---
title: "Задача Hive для Azure HDInsight | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afphivetask.f1
- sql14.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f9e67e91b5cd38482ab1151d5942c9c55c04136c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-hive-task"></a>Задача Hive для Azure HDInsight
**Задача Hive для Azure HDInsight** позволяет выполнить скрипт Hive в кластере Azure HDInsight.
     
Чтобы добавить **задачу Hive для Azure HDInsight**, перетащите ее в конструктор SSIS, дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить** , чтобы открыть диалоговое окно **Редактор задач Hive для Azure HDInsight** .  
  
**Задача Hive для Azure HDInsight** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 В следующем списке описаны поля этого диалогового окна.  
  
1.  Для **HDInsightConnection** поля, выберите существующий диспетчер подключений Azure HDInsight или создайте новую, относится к кластеру Azure HDInsight используется для выполнения сценария.
  
2.  Для **AzureStorageConnection** поля, выберите существующий диспетчер подключений хранилища Azure или создайте новую, ссылается на учетную запись хранилища Azure связанной с кластером. Это только требуется, чтобы загрузить журналы вывода и ошибки выполнения скрипта.
 
3.  Для **BlobContainer** укажите имя контейнера хранилища, связанной с кластером. Это только требуется, чтобы загрузить журналы вывода и ошибки выполнения скрипта.
  
4.  Для **LocalLogFolder** укажите папку, в которую будут загружены журналы вывода и ошибки выполнения скрипта. Это только требуется, чтобы загрузить журналы вывода и ошибки выполнения скрипта.   
  
5.  Существует два способа задать скрипт Hive для выполнения:
  
    1.  **Встроенный скрипт**: укажите **сценарий** поле введите встроенный скрипт для выполнения в **ввод скрипта** диалоговое окно.
  
    2.  **Файл сценария**: передайте файла сценария в хранилище больших двоичных объектов Azure и укажите **BlobName** поля. Если большой двоичный объект не находится в учетной записи хранения по умолчанию или контейнера, связанного с кластером HDInsight, **ExternalStorageAccountName** и **ExternalBlobContainer** поля должен быть указан. Внешний большой двоичный объект убедитесь в том, что он настроен как общедоступный.  
  
     Если указаны оба аргумента, будет использоваться файл скрипта и встроенный скрипт будет игнорироваться.

