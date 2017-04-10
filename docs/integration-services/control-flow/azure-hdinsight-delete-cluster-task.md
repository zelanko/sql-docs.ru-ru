---
title: "Задача удаления кластера Azure HDInsight | Microsoft Docs"
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
  - "sql13.dts.designer.afpdelcltask.f1"
  - "sql14.dts.designer.afpdelcltask.f1"
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Задача удаления кластера Azure HDInsight
  **Задача удаления кластера Azure HDInsight** позволяет пакету служб SSIS удалить кластер Azure HDInsight в указанной подписке Azure.  
  
 **Задача удаления кластера Azure HDInsight** входит в состав пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure для SQL Server 2016. Пакет дополнительных компонентов можно скачать [отсюда](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
> [!NOTE]  
>  Удаление кластера HDInsight обычно занимает 10 минут.  
  
 Чтобы добавить **задачу удаления кластера Azure HDInsight**, перетащите ее в конструкторе служб SSIS и дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить**, чтобы вызвать диалоговое окно **Редактор задач удаления кластера Azure HDInsight**.  
  
 Следующая таблица содержит описание полей этого диалогового окна.  
  
|||  
|-|-|  
|**Поле**|**Description**|  
|AzureSubscriptionConnection|Создайте новый или выберите существующий диспетчер соединений подписки Azure, ссылающийся на подписку Azure, в которой размещается кластер HDInsight.|  
|ClusterName|Укажите имя кластера для удаления.|  
|FailIfNotExists|Укажите, следует ли завершать задачу сбоем, если кластер не существует.|  
  
  