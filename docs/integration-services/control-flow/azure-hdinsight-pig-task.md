---
title: "Задача Pig для Azure HDInsight | Документы Microsoft"
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
- sql13.dts.designer.afppigtask.f1
- sql14.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9874b119b634966b146f8fa9d22c016bcd91617b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-pig-task"></a>Задача Pig для Azure HDInsight
Используйте **задачу Pig для Azure HDInsight** для выполнения сценария Pig на кластере Azure HDInsight.
     
Чтобы добавить **задачу Pig для Azure HDInsight**, перетащите ее в конструктор SSIS, дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить** , чтобы открыть **Редактор задач Pig для Azure HDInsight** .  
  
**Задачу Pig для Azure HDInsight** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 В следующем списке описаны поля этого диалогового окна.  
  
1.  Для **HDInsightConnection** поля, выберите существующий диспетчер подключений Azure HDInsight или создайте новую, относится к кластеру Azure HDInsight используется для выполнения сценария.
  
2.  Для **AzureStorageConnection** поля, выберите существующий диспетчер подключений хранилища Azure или создайте новую, ссылается на учетную запись хранилища Azure связанной с кластером. Это только требуется, чтобы загрузить журналы вывода и ошибки выполнения скрипта.
 
3.  Для **BlobContainer** укажите имя контейнера хранилища, связанной с кластером. Это только требуется, чтобы загрузить журналы вывода и ошибки выполнения скрипта.
  
4.  Для **LocalLogFolder** укажите папку, в которую будут загружены журналы вывода и ошибки выполнения скрипта. Это только требуется, чтобы загрузить журналы вывода и ошибки выполнения скрипта.   
  
5.  Существует два способа задать сценарий Pig для выполнения:
  
    1.  **Встроенный скрипт**: укажите **сценарий** поле введите встроенный скрипт для выполнения в **ввод скрипта** диалоговое окно.
  
    2.  **Файл сценария**: передайте файла сценария в хранилище больших двоичных объектов Azure и укажите **BlobName** поля. Если большой двоичный объект не находится в учетной записи хранения по умолчанию или контейнера, связанного с кластером HDInsight, **ExternalStorageAccountName** и **ExternalBlobContainer** поля должен быть указан. Внешний большой двоичный объект убедитесь в том, что он настроен как общедоступный.  
  
     Если указаны оба аргумента, будет использоваться файл скрипта и встроенный скрипт будет игнорироваться.

