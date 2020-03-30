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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 44d6fd9052b2f36381b95223222ec9008a8e4728
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71298402"
---
# <a name="azure-hdinsight-pig-task"></a>Задача Pig для Azure HDInsight

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
