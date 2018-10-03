---
title: Задача Pig для Azure HDInsight | Документы Майкрософт
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afppigtask.f1
- sql14.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cee619bb2c7e11a1bb6609fcc6a6c1f51ebf6da7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832912"
---
# <a name="azure-hdinsight-pig-task"></a>Задача Pig для Azure HDInsight
Используйте **задачу Pig для Azure HDInsight** для выполнения сценария Pig на кластере Azure HDInsight.
     
Чтобы добавить **задачу Pig для Azure HDInsight**, перетащите ее в конструктор SSIS, дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить** , чтобы открыть **Редактор задач Pig для Azure HDInsight** .  
  
**Задача Pig для Azure HDInsight** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 В следующем списке описаны поля этого диалогового окна.  
  
1.  В поле **HDInsightConnection** выберите существующий диспетчер подключений Azure HDInsight (или создайте новый), который ссылается на кластер Azure HDInsight, используемый для выполнения скрипта.
  
2.  В поле **AzureStorageConnection** выберите существующий диспетчер подключений службы хранилища Azure (или создайте новый), который ссылается на учетную запись хранения Azure, связанную с кластером. Это необходимо только в том случае, если требуется скачать выходные данные выполнения скрипта и журналы ошибок.
 
3.  В поле **BlobContainer** укажите имя контейнера хранилища, связанного с кластером. Это необходимо только в том случае, если требуется скачать выходные данные выполнения скрипта и журналы ошибок.
  
4.  В поле **LocalLogFolder** укажите папку, в которую будут скачиваться выходные данные выполнения скрипта и журналы ошибок. Это необходимо только в том случае, если требуется скачать выходные данные выполнения скрипта и журналы ошибок.   
  
5.  Существует два способа указать выполняемый скрипт Pig.
  
    1.  **Встроенный скрипт**. Укажите значение в поле **Скрипт**, введя скрипт, который необходимо выполнить, в диалоговом окне **Введите сценарий**.
  
    2.  **Файл скрипта**. Отправьте файл скрипта в хранилище BLOB-объектов Azure и укажите значение в поле **BlobName**. Если BLOB-объект не находится в используемом по умолчанию хранилище или контейнере, связанном с кластером HDInsight, нужно указать значения в полях **ExternalStorageAccountName** и **ExternalBlobContainer**. Если используется внешний BLOB-объект, убедитесь в том, что он настроен как общедоступный.  
  
     Если использованы оба способа, будет задействован файл скрипта, а встроенный скрипт будет проигнорирован.
