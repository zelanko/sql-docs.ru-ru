---
title: "Задача Hive для Azure HDInsight | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afphivetask.f1"
  - "sql14.dts.designer.afphivetask.f1"
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Задача Hive для Azure HDInsight
  **Задача Hive для Azure HDInsight** позволяет выполнить скрипт Hive в кластере Azure HDInsight.
     
Чтобы добавить **задачу Hive для Azure HDInsight**, перетащите ее в конструктор SSIS, дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить**, чтобы открыть диалоговое окно **Редактор задач Hive для Azure HDInsight**.  
  
 **Задача Hive для Azure HDInsight** входит в состав пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure для SQL Server 2016. Пакет дополнительных компонентов можно скачать [отсюда](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
 В следующем списке описаны поля этого диалогового окна.  
  
1.  В поле **AzureSubscriptionConnection** выберите существующий диспетчер соединений подписки Azure (или создайте новый), ссылающийся на подписку Azure, в которой размещается кластер HDInsight.  
  
2.  В поле **HDInsightClusterName** введите имя кластера HDInsight, в котором требуется запустить сценарий Hive.  
  
3.  В поле **LocalLogFolder** щелкните **...** (многоточие) и выберите папку для скачивания журналов обработки Hive из кластера HDInsight.  
  
4.  Существует два способа задать скрипт Hive.  
  
    1.  **Встроенный скрипт**: щелкните **...** (многоточие) рядом с полем **Скрипт** и введите встроенный скрипт в диалоговом окне **Ввод скрипта**.  
  
    2.  **Файл сценария**: передайте файла сценария в расположение большого двоичного объекта и укажите его значение **BlobName**. Если большой двоичный объект не находится в используемом по умолчанию хранилище или контейнере кластера HDInsight, нужно указать значения **ExternalStorageAccountName** и **ExternalBlobContainer** . Если используется внешний большой двоичный объект, убедитесь, что он настроен как общедоступный.  
  
     Если использованы оба способа, будет задействован файл скрипта, а встроенный скрипт будет проигнорирован.  
  
  