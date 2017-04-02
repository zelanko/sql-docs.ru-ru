---
title: "Задача Pig для Azure HDInsight | Microsoft Docs"
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
  - "sql13.dts.designer.afppigtask.f1"
  - "sql14.dts.designer.afppigtask.f1"
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Задача Pig для Azure HDInsight
  Используйте **задачу Pig для Azure HDInsight** для выполнения сценария Pig на кластере Azure HDInsight. 
    
Чтобы добавить **задачу Pig для Azure HDInsight**, перетащите ее в конструктор SSIS, дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить**, чтобы открыть **Редактор задач Pig для Azure HDInsight**.  
  
 **Задача Pig для Azure HDInsight** входит в состав пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure для SQL Server 2016. Пакет дополнительных компонентов можно скачать [отсюда](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
1.  В поле **AzureSubscriptionConnection** выберите существующий диспетчер соединений подписки Azure (или создайте новый), ссылающийся на подписку Azure, в которой размещается кластер HDInsight.  
  
2.  В поле **HDInsightClusterName** введите имя кластера HDInsight, на котором вы хотите запустить сценарий Pig.  
  
3.  В поле **LocalLogFolder** щелкните **...** (многоточие) и выберите папку для скачивания журналов обработки Pig с кластера HDInsight.  
  
4.  Существует два способа задать сценарий Pig.  
  
    1.  **Встроенный скрипт**: щелкните **...** (многоточие) рядом с полем **Скрипт** и введите встроенный скрипт в диалоговом окне **Ввод скрипта**.  
  
    2.  **Файл сценария**: передайте файла сценария в расположение большого двоичного объекта и укажите его значение **BlobName**. Если большой двоичный объект не находится в используемом по умолчанию хранилище или контейнере кластера HDInsight, нужно указать значения **ExternalStorageAccountName** и **ExternalBlobContainer** . Если используется внешний большой двоичный объект, убедитесь, что он настроен как общедоступный.  
  
     Если использованы оба способа, будет задействован файл скрипта, а встроенный скрипт будет проигнорирован.  
  
  